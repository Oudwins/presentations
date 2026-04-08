---
theme: seriph
title: The future of IDE's in the agent of agents
subtitle: My AI first coding workflow
author: Tristan May
info: |
  The tools, prompts and flows I use automate the simple parts of engineering work.
class: text-center
drawings:
  persist: false
transition: slide-left
comark: true
duration: 35min
highlighter: shiki
mdc: true
---

<div class="absolute inset-0 bg-gradient-to-br from-slate-950 via-slate-900 to-emerald-950" />
<div class="absolute top-16 left-12 w-72 h-72 rounded-full bg-emerald-500/15 blur-3xl" />
<div class="absolute bottom-10 right-16 w-96 h-96 rounded-full bg-cyan-500/10 blur-3xl" />

<div class="relative z-10 h-full flex flex-col justify-center px-14">
  <p class="uppercase tracking-[0.35em] text-emerald-300 text-sm mb-6">Slidev talk</p>
  <h1 class="!text-5xl !leading-tight !font-700 text-white max-w-4xl mx-auto">
    The future of IDE's in the agent of agents
  </h1>
  <p class="mt-6 text-xl text-slate-200 max-w-3xl mx-auto leading-relaxed">
    My AI first coding workflow: the tools, prompts and flows I use automate the simple parts of engineering work.
  </p>
  <div class="mt-10 flex justify-center gap-3 text-sm text-slate-300">
    <span class="rounded-full border border-white/15 px-4 py-1">Agent orchestration</span>
    <span class="rounded-full border border-white/15 px-4 py-1">Parallel threads of work</span>
    <span class="rounded-full border border-white/15 px-4 py-1">Context engineering</span>
  </div>
</div>

<!--
Set the framing immediately: this is a workflow talk, not a model benchmark talk.
-->

---
layout: center
class: text-left
---

<h1 class="!text-slate-100">Quick room check</h1>

<div class="mt-8 space-y-5 text-2xl leading-tight text-slate-900">
  <div class="rounded-2xl bg-slate-100 px-6 py-4 text-slate-900">
    How many people have multiple versions of the repo they are working in?
  </div>
  <div class="rounded-2xl bg-slate-100 px-6 py-4 text-slate-900">
    How many people use worktrees specifically?
  </div>
  <div class="rounded-2xl bg-slate-100 px-6 py-4 text-slate-900">
    How many do you have?
  </div>
</div>

---
layout: statement
---

<h1 class="!text-slate-100">Obligatory mention</h1>

This is my experience and my opinions.

I am probably wrong about a bunch of stuff.

My setup and opinions are evolving, so this might be slightly different next week.

---
layout: two-cols
layoutClass: gap-14
---

<h1 class="!text-slate-100">Who am I?</h1>

- Wrote my first line of code at 10 or 11 trying to build a Unity game
- Founder of many failed or sunset startups and side projects
- Before Eleven, I worked as an SDE on software for operating spacecraft
- I do a lot of open source work; biggest claim to fame is `Zog`, a validation library for Go

::right::

- I work mostly on the marketing website
- I run my own home server
- I play Dungeons and Dragons and airsoft
- I hate breaking flow, so I hate notifications

<div class="mt-8 rounded-2xl border border-slate-200 bg-slate-50 px-5 py-4 text-sm text-slate-700">
That last point matters more than it sounds. A lot of this talk is really about protecting flow.
</div>

---
layout: center
class: text-center
---

<h1 class="!text-slate-100">I was a coding agent skeptic until Dec 2025</h1>

<div class="mt-8 text-2xl text-slate-300 max-w-3xl mx-auto leading-relaxed">
Not because the demos were bad.
<br><br>
Because the workflow cost felt higher than the leverage.
</div>

---
layout: two-cols-header
---

<h1 class="!text-slate-100">What this talk is about</h1>

::left::

## Core idea

I think about engineering work as a <span v-mark.underline.orange>thread of work</span>.

- agents let us scale from one thread to multiple
- the challenge is not raw generation speed
- the challenge is coordination, oversight and context

::right::

## What you should leave with

- a better mental model for multi-threaded engineering
- patterns for scaling parallelism without tanking quality
- a practical view on where local, remote and cloud agents fit

---
layout: center
zoom: 0.82
---

<h1 class="!text-slate-100">One thread of work</h1>

```mermaid {scale: 0.88}
flowchart LR
  R[Research] --> P[Plan]
  P --> I[Implementation]
  I --> V[Review]
  V --> PR[PR]
  PR --> S[Ship]
  I -. iterate .-> P
  V -. fix .-> I
  PR -. feedback .-> I
```

<div class="mt-6 text-slate-300 text-lg max-w-5xl mx-auto">
The important change is not that the steps disappeared. It is that more of them can now run in parallel.
</div>

---
layout: center
class: text-center
---

<h1 class="!text-slate-100">The goal</h1>

<div class="text-4xl leading-tight max-w-4xl mx-auto">
Increase your parallelism
<br>
without decreasing code quality
</div>

---
layout: two-cols
layoutClass: gap-10
---

<h1 class="!text-slate-100">A useful reference point</h1>

<Tweet id="2019903946056237516" scale="0.82" />

::right::

> "The amount of software I can create is now mostly limited by inference time and hard thinking."

<div class="mt-6 text-slate-300 leading-relaxed">
Peter Steinberger's workflow is a good example of where this is heading: multiple active threads, local control, lots of automation, and the human spending more time steering than typing.
</div>

<div class="mt-8 text-sm text-slate-400">
Refs: `x.com/steipete/status/2019903946056237516`, `steipete.me/posts/2025/shipping-at-inference-speed`
</div>

---
layout: two-cols-header
zoom: 0.84
---

<h1 class="!text-slate-100">Current solution shapes</h1>

::left::

## IDE first

- Cursor 2.0
- great single-thread ergonomics
- still tends to center one active workspace

## Cloud agents

- async by default
- look scalable on paper
- poor fit for day to day engineering loops

## Orchestration first

- `gastown`
- interesting direction
- not enough for real engineering control yet

::right::

## Agent first apps

- `vibe-kanban`
- Codex
- `t3.chat` / `t3.codes`
- Conductor
- Superset
- `claude-squad`
- maybe Cursor 3.0

## DIY stack

- tmux
- worktrees
- local CLIs
- scripts and glue

---
layout: center
---

<h1 class="!text-slate-100">Late last year I moved to 4 Cursor worktrees and instances</h1>

<div class="mt-10 grid grid-cols-2 gap-5 text-left text-lg text-slate-900">
  <div class="rounded-2xl border border-amber-200 bg-amber-50 p-5 text-slate-900">
    Hard to know what I was working on
  </div>
  <div class="rounded-2xl border border-amber-200 bg-amber-50 p-5 text-slate-900">
    Hard to know what needed my attention
  </div>
  <div class="rounded-2xl border border-amber-200 bg-amber-50 p-5 text-slate-900">
    High context switching cost
  </div>
  <div class="rounded-2xl border border-amber-200 bg-amber-50 p-5 text-slate-900">
    Easy to conflict with my own edits in the same repo
  </div>
</div>

<div class="mt-8 text-slate-300">
The problem was not lack of agent power. The problem was lack of thread management.
</div>

---
layout: center
class: text-left
---

<h1 class="!text-slate-100">Shared repos are hostile to parallel agent work</h1>

<div class="mt-8 rounded-3xl border-2 border-dashed border-slate-300 bg-slate-50 p-8">
  <div class="text-sm uppercase tracking-[0.2em] text-slate-500 mb-3">Screenshot placeholder</div>
  <div class="text-2xl leading-relaxed text-slate-700">
    Add the screenshot of the colleague who almost had a bunch of code deleted.
  </div>
  <div class="mt-4 text-slate-500">
    This slide works best as the concrete "never share mutable state with an unsupervised agent" moment.
  </div>
</div>

---
layout: center
---

<h1 class="!text-slate-100">Then I tried cloud agents more seriously</h1>

<div class="mt-8 text-2xl leading-relaxed max-w-4xl mx-auto text-slate-300">
They felt like the right abstraction for parallelism.
<br><br>
In practice, they were the wrong abstraction for engineering.
</div>

---
layout: center
class: text-left
---

<h1 class="!text-slate-100">Why cloud agents break down in practice</h1>

<v-clicks>

- low steerability once they are off doing their thing
- weak feedback loops for browser, tests and partial review
- too much latency for tight iteration
- the work comes back as a PR-shaped blob instead of a living thread
- less obvious recovery path when the agent goes weird

</v-clicks>

<div class="mt-8 rounded-3xl border-2 border-dashed border-slate-300 bg-slate-50 p-8">
  <div class="text-sm uppercase tracking-[0.2em] text-slate-500 mb-3">Screenshot placeholder</div>
  <div class="text-xl leading-relaxed text-slate-700">
    Add the image of trying to get a cloud agent to change one line of code.
  </div>
</div>

---
layout: two-cols
layoutClass: gap-14
---

<h1 class="!text-slate-100">When I decided to go all in</h1>

## Switch to `nvim`

- many IDEs open at the same time
- keyboard-first switching
- low friction between threads

## Add `tmux`

- cheap session management
- terminal native multiplexing
- fast jumps between active threads

::right::

## Add `cc`

- local agent in the same environment as the code
- direct access to tests, browser and repo state
- way more steerable than remote async flows

<div class="mt-8 rounded-2xl bg-slate-100 px-5 py-4 text-slate-800">
Show `tmux-sessionizer` here.
</div>

---
layout: two-cols-header
---

<h1 class="!text-slate-100">Then I needed an engine for threads of work</h1>

::left::

## Droner

- throw as many threads of work at it as I want at the start of the day
- jump between them at my own pace
- slowly handle each one until it merges
- local first today, backend-oriented API for later

## Why it exists

- worktrees alone are not orchestration
- sessions alone are not orchestration
- PRs alone are not orchestration

::right::

## Things it handles

- background worktree creation
- worktree reuse
- hydration
- GitHub integration
- branch name generation
- moving to the next relevant session with `alt+]`
- oversight via slash commands

---
layout: center
---

<h1 class="!text-slate-100">Thread orchestration is mostly a human factors problem</h1>

<div class="mt-10 grid grid-cols-3 gap-4 text-left">
  <div class="rounded-2xl bg-slate-100 p-5 text-slate-900">
    <div class="text-sm uppercase tracking-[0.18em] text-slate-500">Discover</div>
    <div class="mt-2 text-xl text-slate-900">What needs my attention next?</div>
  </div>
  <div class="rounded-2xl bg-slate-100 p-5 text-slate-900">
    <div class="text-sm uppercase tracking-[0.18em] text-slate-500">Switch</div>
    <div class="mt-2 text-xl text-slate-900">How fast can I move into the thread?</div>
  </div>
  <div class="rounded-2xl bg-slate-100 p-5 text-slate-900">
    <div class="text-sm uppercase tracking-[0.18em] text-slate-500">Recover</div>
    <div class="mt-2 text-xl text-slate-900">How easily can I fix or redirect it?</div>
  </div>
</div>

---
layout: two-cols
layoutClass: gap-14
---

<h1 class="!text-slate-100">What parallelism actually requires</h1>

## What the agent needs

- enough autonomy to make progress
- a way to check its own work
- browser, tests, build and repo access
- isolated code environment

::right::

## What the human needs

- preview and test surfaces
- minimal context-switch strain
- a way to undo large bad turns
- a way to jump into the thread and help
- a backlog beyond just one ticket
- control over oversight level per thread

---
layout: center
zoom: 0.9
---

<h1 class="!text-slate-100">Oversight should be adjustable</h1>

<div class="mt-8 grid grid-cols-2 gap-4 text-left">
  <div class="rounded-2xl border border-slate-700 bg-slate-900/70 p-5 text-slate-100">
    <div class="text-xs uppercase tracking-[0.2em] text-emerald-300">Low oversight</div>
    <div class="mt-2 text-2xl">Just get me a PR</div>
  </div>
  <div class="rounded-2xl border border-slate-700 bg-slate-900/70 p-5 text-slate-100">
    <div class="text-xs uppercase tracking-[0.2em] text-emerald-300">Medium</div>
    <div class="mt-2 text-2xl">Review implementation</div>
  </div>
  <div class="rounded-2xl border border-slate-700 bg-slate-900/70 p-5 text-slate-100">
    <div class="text-xs uppercase tracking-[0.2em] text-emerald-300">Higher</div>
    <div class="mt-2 text-2xl">Review plan first</div>
  </div>
  <div class="rounded-2xl border border-emerald-500/40 bg-emerald-950/40 p-5 text-slate-100">
    <div class="text-xs uppercase tracking-[0.2em] text-emerald-300">Highest</div>
    <div class="mt-2 text-2xl leading-tight">Keep asking me before risky moves</div>
  </div>
</div>

<div class="mt-6 text-slate-300 text-lg max-w-4xl mx-auto">
Different threads deserve different supervision. A typo fix and a risky refactor should not have the same control surface.
</div>

---
layout: two-cols-header
---

<h1 class="!text-slate-100">Why I think cloud agents are the wrong default abstraction</h1>

::left::

## Good at

- queueing work
- fire-and-forget demos
- long running isolated tasks

::right::

## Bad at

- continuous steering
- rich local verification
- preserving flow
- feeling like part of your IDE instead of a separate product

---
layout: center
---

<h1 class="!text-slate-100">Looking forward</h1>

<div class="text-3xl leading-tight max-w-4xl mx-auto">
The future is a meta-IDE:
<br>
many sub-IDEs, local and remote, each running their own agent,
<br>
with the line between local and remote disappearing.
</div>

<div class="mt-8 text-slate-300 max-w-3xl mx-auto">
Not one chat box. Not one tab. A fabric of active engineering threads.
</div>

---
layout: section
---

<h1 class="!text-slate-100">If there is time</h1>

Context engineering and agent flows

---
layout: two-cols
layoutClass: gap-14
---

<h1 class="!text-slate-100">Context engineering matters</h1>

## Better results come from better context

- isolate work so context stays legible
- keep docs and subsystem notes current
- make verification cheap
- make rollback and redirection cheap

::right::

## Agent flow matters too

- research
- plan
- implement
- verify
- review
- merge

Same stages as before. Better tools for moving between them.

---
layout: center
class: text-center
---

<h1 class="!text-slate-100">Takeaways</h1>

<div class="mt-8 grid grid-cols-2 gap-4 text-left">
  <div class="rounded-2xl bg-emerald-50 border border-emerald-200 p-5 text-slate-900">Parallelism without orchestration mostly creates confusion.</div>
  <div class="rounded-2xl bg-emerald-50 border border-emerald-200 p-5 text-slate-900">Local agents win when you care about steering, feedback loops and flow.</div>
  <div class="rounded-2xl bg-emerald-50 border border-emerald-200 p-5 text-slate-900">The real product is not the model. It is the thread management layer around the model.</div>
  <div class="rounded-2xl bg-emerald-50 border border-emerald-200 p-5 text-slate-900">The future IDE probably looks like orchestration plus context engineering.</div>
</div>

---
layout: center
class: text-center
---

<h1 class="!text-slate-100">Questions?</h1>

<div class="mt-8 text-xl text-slate-300">
I would genuinely love to hear what you think I am wrong about.
</div>
