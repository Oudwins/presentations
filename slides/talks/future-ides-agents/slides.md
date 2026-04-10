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
Hey from comment
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
    How many agents do you run in parallel on average?
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
layout: default
layoutClass: gap-14
---

<h1 class="!text-slate-100">Who am I?</h1>

- Wrote my first line of code at 10 or 11 trying to build a Unity game
- Founder of many failed or sunset startups and side projects
- Before Eleven, I worked as an SDE on software for operating spacecraft
- I do a lot of open source work; biggest claim to fame is `Zog`, a validation library for Go
- I work mostly on the marketing website



---
layout: image-right
image: /assets/loot.jpeg
class: bg-top
layoutClass: gap-14
---

<h1 class="!text-slate-100">And also!</h1>

- I run my own home server
- I play Dungeons and Dragons and airsoft
- I hate breaking flow, so I hate notifications


---
layout: statement
class: text-center
---

<h1 class="!text-slate-100">The goal</h1>

<div class="text-4xl leading-tight max-w-4xl mx-auto">
Increase your parallelism
<br>
without decreasing code quality
</div>




---
layout: default
---

## What you should leave with

- Ideas, tools and strategies to try for yourself to increase your own parallelism
- a better mental model for multi-threaded engineering
- A view into my setup

## What I won't discuss today

- Tools or SOPs for improving agent output
- Context engineering
- Claude Code Specific ideas
- Which models are best for what
- Skills, MCPs, subagents...

But if people are interested in some of that maybe I can come back at some point to chat about it





---
layout: statement
class: text-center
---

## Guilty admision

I was a coding agent skeptic until Dec 2025



---
layout: center
zoom: 0.82
---

<h1 class="!text-slate-100">Thinking in threads</h1>

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



<!--
Now we just have to run this in parallel as much as possible. That means doing as little ourselves as possible and delegating as much as possible to the agent
-->


---
layout: image
image: /assets/threads-of-work.png
---


<!--
Key idea here which is pretty obvious is that the less user involvement the more threads we can have at once
-->


---
layout: default
layoutClass: gap-10
---

<h1 class="!text-slate-100">Creator of OpenClaw</h1>

<Tweet id="2019903946056237516" scale="0.85" />



<!--
- Is vibe coding
- We cannot go that far yet without disaterous consequences
-->

---
layout: section
---

# Current solution shapes

---
zoom: 0.82
---

<h1 class="!text-slate-100">IDE's</h1>

<div class="mt-8 grid grid-cols-2 gap-6 text-left max-w-5xl mx-auto">
  <div class="overflow-hidden rounded-2xl border border-slate-200 bg-slate-50 shadow-sm">
    <img src="./assets/solution-shapes/cursor.png" class="h-64 w-full object-cover object-top" alt="Cursor homepage screenshot" />
    <div class="px-4 py-3 text-slate-800 text-lg font-semibold">
      <div class="font-semibold">Cursor</div>
    </div>
  </div>
  <div class="overflow-hidden rounded-2xl border border-slate-200 bg-slate-50 shadow-sm">
    <img src="./assets/solution-shapes/windsurf.png" class="h-64 w-full object-cover object-top" alt="Windsurf homepage screenshot" />
    <div class="px-4 py-3 text-slate-800 text-lg font-semibold">
      <div class="font-semibold">Windsurf</div>
    </div>
  </div>
</div>

---
zoom: 0.82
---

<h1 class="!text-slate-100">Canvan</h1>

<div class="mt-8 grid grid-cols-2 gap-6 text-left max-w-5xl mx-auto">
  <div class="overflow-hidden rounded-2xl border border-slate-200 bg-slate-50 shadow-sm">
    <img src="./assets/solution-shapes/vibe-kanban.png" class="h-72 w-full object-cover object-top" alt="Vibe Kanban homepage screenshot" />
    <div class="px-4 py-3 text-slate-800 text-lg font-semibold">
      <div class="font-semibold">Vibe Kanban</div>
    </div>
  </div>
  <div class="overflow-hidden rounded-2xl border border-slate-200 bg-slate-50 shadow-sm">
    <img src="https://automaker.app/card.png" class="h-72 w-full object-cover object-top" alt="Automaker share image" />
    <div class="px-4 py-3 text-slate-800 text-lg font-semibold">
      <div class="font-semibold">Automaker</div>
    </div>
  </div>
</div>


---
zoom: 0.76
---

<h1 class="!text-slate-100">Cloud agents</h1>

<div class="mt-8 grid grid-cols-3 gap-5 text-left text-sm">
  <div class="overflow-hidden rounded-2xl border border-slate-200 bg-slate-50 shadow-sm">
    <img src="./assets/solution-shapes/claude.png" class="h-52 w-full object-cover object-top" alt="Claude homepage screenshot" />
    <div class="px-4 py-3 text-slate-800 text-lg font-semibold">
      <div class="font-semibold">Claude</div>
    </div>
  </div>
  <div class="overflow-hidden rounded-2xl border border-slate-200 bg-slate-50 shadow-sm">
    <img src="./assets/solution-shapes/cursor.png" class="h-52 w-full object-cover object-top" alt="Cursor homepage screenshot" />
    <div class="px-4 py-3 text-slate-800 text-lg font-semibold">
      <div class="font-semibold">Cursor</div>
    </div>
  </div>
  <div class="overflow-hidden rounded-2xl border border-slate-200 bg-slate-50 shadow-sm">
    <img src="./assets/solution-shapes/devin.png" class="h-52 w-full object-cover object-top" alt="Devin homepage screenshot" />
    <div class="px-4 py-3 text-slate-800 text-lg font-semibold">
      <div class="font-semibold">Devin</div>
    </div>
  </div>
</div>

---
zoom: 0.76
---

<h1 class="!text-slate-100">Agent first</h1>

<div class="mt-8 grid grid-cols-4 gap-5 text-left text-sm">
  <div class="overflow-hidden rounded-2xl border border-slate-200 bg-slate-50 shadow-sm">
    <img src="./assets/solution-shapes/t3-codes.png" class="h-52 w-full object-cover object-top" alt="T3 Code homepage screenshot" />
    <div class="px-4 py-3 text-slate-800 text-lg font-semibold">
      <div class="font-semibold">T3 Code</div>
    </div>
  </div>
  <div class="overflow-hidden rounded-2xl border border-slate-200 bg-slate-50 shadow-sm">
    <img src="./assets/solution-shapes/cursor.png" class="h-52 w-full object-cover object-top" alt="Cursor 3.0 screenshot" />
    <div class="px-4 py-3 text-slate-800 text-lg font-semibold">
      <div class="font-semibold">Cursor 3.0</div>
    </div>
  </div>
  <div class="overflow-hidden rounded-2xl border border-slate-200 bg-slate-50 shadow-sm">
    <img src="./assets/solution-shapes/conductor.png" class="h-52 w-full object-cover object-top" alt="Conductor homepage screenshot" />
    <div class="px-4 py-3 text-slate-800 text-lg font-semibold">
      <div class="font-semibold">Conductor</div>
    </div>
  </div>
  <div class="overflow-hidden rounded-2xl border border-slate-200 bg-slate-50 shadow-sm">
    <img src="./assets/solution-shapes/superset.png" class="h-52 w-full object-cover object-top" alt="Superset homepage screenshot" />
    <div class="px-4 py-3 text-slate-800 text-lg font-semibold">
      <div class="font-semibold">Superset</div>
    </div>
  </div>
</div>

---
zoom: 0.82
layout: image
image: https://miro.medium.com/v2/resize:fit:700/1*ReBwrC1sc9USnhvYXcrd4A.jpeg
---

<!-- <h1 class="!text-slate-100">Gastown</h1> -->


<!--
Gastown. Oschestrator first
-->

---
layout: center
---

<h1 class="!text-slate-100 !text-6xl text-center">Build your own</h1>

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
layout: image
class: text-left
image: /assets/isolation.png
backgroundSize: contain
---

<h1 class="!text-slate-100">Shared repos are hostile to parallel agent work</h1>


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
