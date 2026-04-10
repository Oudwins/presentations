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
layout: default
---

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

I was a coding agent skeptic until ~Dec 2025



<!--
I was using cursor every day, in fact I started in 2023 few months after they launched. 

- But to speed up the work I was doing at the time. very hands on
-->


---
layout: default
class: "!flex !flex-col !overflow-hidden"
---

<h1 class="!text-slate-100 !flex-shrink-0">But then something changed. New opus & GPT models</h1>

<p class="!flex-shrink-0">So I started using cursor's background agents. With and without worktrees</p>

<ImageContainer src="/assets/cursor-2.png" alt="Cursor agent interface" />



<!--

- editing, conflicts bringing agent code into current working branch to make edits
- Forgetting where I had threads open. What stuff is shipped, waiting for reviews, etc. Couldn't keep it all in my head. 
- Losing context of what I was doing inside a thread. What file was I looking at? What file was I editing? etc
-->

---
layout: image
class: text-left
image: /assets/isolation.png
backgroundSize: contain
---

<h1 class="!text-slate-100">I had this problem every week</h1>


---
layout: center
---

<h1 class="!text-slate-100">4 Cursor instances</h1>

<p class="!flex-shrink-0">I found myself with 4 cusor instances open juggling between them.</p>

<ImageContainer src="/assets/4-cursors.png" alt="Cursor agent interface" />


<!--
- I would often forget in what instance I had what. Would jump around
- PC crashed every day
- Often times I needed a new instance which meant opening a new worktree or project which took like 10s and completely killed my flow
- Ultimately I needed more than 4
-->


---
layout: center
---

<h1 class="!text-slate-100 !text-6xl text-center">Cloud agents</h1>

---
layout: image
image: /assets/cloud-agents/1st.png
backgroundSize: contain
---


---
layout: image
image: /assets/cloud-agents/2nd.png
backgroundSize: contain
---



---
layout: statement
---

## What am I doing wrong?
Someone has to have figured this out already. Lets research


---
layout: section
---

## Current solution shapes

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
layout: statement
---

## Switched to Neovim ~btw

One persistent session per thread of work

<!--
- Wanted one persistent session per thread of work
- Each thread gets its own neovim session that stays alive
- No more juggling multiple IDE windows or forgetting where things are
-->


---
layout: default
---

<h1 class="!text-slate-100">How I work</h1>

<div class="mt-6 space-y-4 text-xl">
  <div class="flex items-center gap-3"><span class="text-emerald-400 font-mono">1.</span> Throw / kick off</div>
  <div class="flex items-center gap-3"><span class="text-emerald-400 font-mono">2.</span> Work</div>
  <div class="flex items-center gap-3"><span class="text-emerald-400 font-mono">3.</span> Go to what needs me</div>
  <div class="flex items-center gap-3"><span class="text-emerald-400 font-mono">4.</span> Push PRs</div>
  <div class="flex items-center gap-3"><span class="text-emerald-400 font-mono">5.</span> PR merge = session deleted</div>
</div>

<p class="mt-10 text-slate-400 text-lg italic">Effectively I'm a pull-based system on what needs me</p>

<!--
- "Throw/kick off" creates a worktree, names the branch, sets up the environment automatically. Show how cursor does it. Worktree reuse is key here — don't create new ones unnecessarily
- "Work" is the agent doing its thing inside the session
- "Go to what needs me" — I poll across sessions, only jumping in where I'm actually needed
- PR merge triggers cleanup — the session and worktree get deleted automatically
- The mental model shift: I'm not pushing work forward, I'm pulling from a queue of things that need my attention
-->


---
layout: default
---

<h1 class="!text-slate-100">Why this works</h1>

<div class="mt-8 space-y-6 text-xl">
  <div class="rounded-xl bg-slate-800/60 px-6 py-4">No need to keep context of what I'm working on</div>
  <div class="rounded-xl bg-slate-800/60 px-6 py-4">Switching threads is instant</div>
  <div class="rounded-xl bg-slate-800/60 px-6 py-4">Everything is isolated — environment auto-setup</div>
  <div class="rounded-xl bg-emerald-900/40 border border-emerald-500/30 px-6 py-4">Hydration!</div>
</div>

<!--
- I only have to think about the next thing and poll from the queue. No juggling mental context across threads
- Moving from one thread of work to the next is instant — just switch to the session
- Each worktree is fully isolated. Environment is automatically set up at creation time
- Hydration: when I jump into a session, the agent has already done work and left me context. I hydrate into the thread quickly rather than rebuilding context from scratch
-->


---
layout: section
---

## Into the future
What I'm working on, what I would like & where I think things are going


---
layout: default
zoom: 0.88
---

<h1 class="!text-slate-100">Levels of autonomy</h1>

<div class="mt-6 space-y-3 text-lg">
  <div class="rounded-xl bg-slate-800/60 px-5 py-3 flex items-center gap-3">
    <span class="text-red-400 font-mono text-sm">L0</span> No autonomy — each step interrupts you
  </div>
  <div class="rounded-xl bg-slate-800/60 px-5 py-3 flex items-center gap-3">
    <span class="text-orange-400 font-mono text-sm">L1</span> Implementation — research, plan, implement, commit
  </div>
  <div class="rounded-xl bg-slate-800/60 px-5 py-3 flex items-center gap-3">
    <span class="text-yellow-400 font-mono text-sm">L2</span> PR — previous + open PR
  </div>
  <div class="rounded-xl bg-slate-800/60 px-5 py-3 flex items-center gap-3">
    <span class="text-emerald-400 font-mono text-sm">L3</span> Semi-full — previous + address feedback
  </div>
  <div class="rounded-xl bg-slate-800/60 px-5 py-3 flex items-center gap-3">
    <span class="text-cyan-400 font-mono text-sm">L4</span> Vibe — previous + merge
  </div>
</div>

<!--
- At creation time for the thread you define its level of autonomy, which defines your interception points
- L0: no autonomy, you're involved at every step — basically pair programming
- L1: agent does research, planning, implementation, and commits — you review after
- L2: agent also opens the PR for you
- L3: agent also addresses PR feedback from reviewers autonomously
- L4: full vibe mode — agent merges when approved. You trust the process end to end
-->


---
layout: default
---

<h1 class="!text-slate-100"> <s>Cloud agents</s> Cloud sessions</h1>
Local like IDE experience

<div class="mt-8 space-y-6 text-xl">
  <div class="rounded-xl bg-slate-800/60 px-6 py-4">Sessions run remotely, not on your machine</div>
  <div class="rounded-xl bg-red-900/30 border border-red-500/30 px-6 py-4">
    <span class="text-red-300">Challenge:</span> Secrets management
  </div>
  <div class="rounded-xl bg-slate-800/60 px-6 py-4">
    <span class="text-slate-300">Provider model:</span> fly.io design
  </div>
</div>

<!--
- Cloud sessions let you offload entirely — sessions don't consume local resources
- Biggest challenge is secrets. How do you give a cloud agent access to your credentials, API keys, etc. securely?
- Provider model reference: https://fly.io/blog/design-and-implementation/ — good design for how to think about remote execution environments
-->





---
layout: default
---

<h1 class="!text-slate-100">Reset to step</h1>

<div class="mt-8">

```mermaid {scale: 0.85}
flowchart LR
  R[Research] --> P[Plan]
  P --> I[Implementation]
  I --> V[Review]
  R -. "reset" .- I
  P -. "reset" .- V
```

</div>

<p class="mt-6 text-slate-300 text-lg">Go back to a previous step and iterate from there</p>

<!--
- Implementation is bad? Go back to plan, see what the issue is, iterate from there
- Plan is bad? Go back to research
- This is like git reset but for the agent workflow itself — you rewind the thread to an earlier stage
- Avoids starting from scratch when only one phase went wrong
-->


---
layout: statement
---

<h1 class="!text-slate-100">Port isolation</h1>


---
layout: statement
---

## Bottom line

The future is probably agent-first apps

But I don't want to wait 8s for Cursor to open, so I'm stuck in crazy land

<!--
- Agent-first apps like T3 Code, Conductor, etc. are likely the direction everything is heading
- But the overhead of GUI-heavy tools kills flow — 8 seconds to open Cursor is 8 seconds too many
- So for now, neovim + worktrees + custom orchestration is the sweet spot for me
- "Crazy land" = building your own workflow tooling, but it works
-->


---
layout: statement
---

## But at least I can say I use nvim btw


---
layout: center
class: text-center
---

<h1 class="!text-5xl !text-slate-100">Questions?</h1>

