---
title: Zog
subtitle: Zod-Like schema validation library for Go
theme: default
highlighter: shiki
transition: slide-left
author: Tristan May
info: ## Slidev Starter Template Presentation slides for developers. Learn more at [Sli.dev](https://sli.dev)
---

# Zog
An origin story

<!--
Intro: quick personal story + what Zog is.
-->

---

## The original annoyance

In JS/TS I really don't like using `process.env` directly

- **missing vars fail late, increases service unreliability**
- stringly-typed
- parsing/coercion is manual
- validation ends up duplicated

---

## The known good solution (TS)

I usually reach for `t3-env` which doesn't allow you to startup your app if schema validation on its environment variables fails.

```ts
import { createEnv } from "@t3-oss/env-nextjs";
import { z } from "zod";
 
export const env = createEnv({
  server: {
    DATABASE_URL: z.url(),
    OPEN_AI_API_KEY: z.string().min(1),
  },
  client: {
    NEXT_PUBLIC_PUBLISHABLE_KEY: z.string().min(1),
  },
  runtimeEnv: {
    DATABASE_URL: process.env.DATABASE_URL,
    OPEN_AI_API_KEY: process.env.OPEN_AI_API_KEY,
    NEXT_PUBLIC_PUBLISHABLE_KEY: process.env.NEXT_PUBLIC_PUBLISHABLE_KEY,
  },
});

```


---

## Same problem in Go

In Go, I also don't like `os.Getenv`

- always a `string`
- no coercion (`"3000"` -> `int`)
- missing/empty values are easy to miss
- validation is often ad-hoc per service
- Default values spread across `os.Getenv` calls

---

## Struct validation in go

Alright so we just need a validator & that should be it! Quick and small library specifically for envs....


```go
// The standard package everyone uses is `go-playground/validator`
type User struct {
	FirstName      string     `validate:"required"`
	LastName       string     `validate:"required"`
	Age            uint8      `validate:"gte=0,lte=130"`
	Gender         string     `validate:"oneof=male female prefer_not_to"`
}
```

Actually, I'm too clumsy to use magic strings. Lets build a simple schema validator

---

## So I built Zog

Zog is a schema builder for runtime parsing and validation in Go

- Zod-like chaining API
- built-in coercion
- rich, structured errors (issues)
- fast, zero dependencies
- helper packages: `zenv`, `zhttp`, `zjson`, `i18n`

```go
type User struct {
	Name string
	Age  int
}

var userSchema = z.Struct(z.Shape{
	// its very important that schema keys like "name" match the struct field name NOT the input data
	"name": z.String().Min(3, z.Message("Override default message")).Max(10),
	"age":  z.Int().GT(18),
})
```

---

## What "schema" means in Zog

You describe the destination Go shape, then:

- `Parse(input, &dest)` parses + coerces + validates
- `Validate(&value)` validates an already-typed Go value

Same schema, two workflows.

---

## Example: typesafe envs with `zenv`

```go
import (
  z "github.com/Oudwins/zog"
  "github.com/Oudwins/zog/zenv"
)

var envSchema = z.Struct(z.Shape{
  "PORT": z.Int().GT(1000).LT(65535).Default(3000),
  "DB_URL"z.String().URL().Required(),
})

var Env = struct {
  PORT int
  DB_URL string
}{}

func Init() {
  errs := envSchema.Parse(zenv.New(), &Env)
  if errs != nil {
    // fail fast at startup
    panic(errs)
  }
}
```


---

## Errors are first-class

Zog returns a `ZogIssueList` (not "just one error")

```go
type ZogIssue struct {
	// Code is the unique identifier for the issue. 
  // Generally also the ID for the Test that caused the issue. See below for a full list
	Code zconst.ZogIssueCode
	// Path is the path to the field that caused the issue
	Path []string
	// Value is the data value that caused the issue.
	// If using Schema.Parse(data, dest) then this will be the value of data.
	Value any
	// Dtype is the destination type. i.e The zconst.ZogType of the value that was validated.
	// If using Schema.Parse(data, dest) then this will be the type of dest.
	Dtype string
	// Params is the params map for the issue. Taken from the Test that caused the issue.
	// This may be nil if Test has no params.
	Params map[string]any
	// Message is the human readable, user-friendly message for the issue.
	// This is safe to expose to the user.
	Message string
	// Err is the wrapped error or nil if none
	Err error
}

```

---


## i18n as first class citizen

```go
i18n.SetLanguagesErrsMap(map[string]i18n.LangMap{
	"es": es.Map,
	"en": en.Map,
	"ja": ja.Map,
},
	"es",                        // default language
	i18n.WithLangKey("langKey"), // (optional) default lang key is "lang" and is stored in i18n.LangKey
)


// Now when we parse
schema.Parse(data, &dest, z.WithCtxValue("langKey", "es")) // get spanish errors
schema.Parse(data, &dest, z.WithCtxValue("langKey", "en")) // get english errors
schema.Parse(data, &dest, z.WithCtxValue("langKey", "ja")) // get japanese errors
```

---
layout: center
class: text-center
---

## Is it fast?


---

## Lets make a bench!

So I created `Oudwins/govalidbench`. And we were fast. But we could be faster. Working to make Zog become almost as fast as the validator package:

1. Reduce internal allocations
2. Pool allocated internal resources
3. Give an option for the user to do the same with user facing resources `z.Issues.Free()`


---

## Recursive schema


```go
var nodeSchema = z.EXPERIMENTAL_RECURSIVE(func(self z.RecursiveSchema[*z.PointerSchema]) *z.PointerSchema {
    return z.Ptr(z.Struct(z.Shape{
        "value": z.Int().Required(),
        "self": self(func(original *z.PointerSchema) *z.PointerSchema {
            // Modify the original schema
            return original
        }),
    }))
})
```


---

## Into the future

- Codegen
- ZSS & OpenAPI Schema

