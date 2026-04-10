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

<div class="h-full flex flex-col items-center justify-center px-16">
  <div class="mb-10 flex items-center gap-2 text-[#888] text-sm tracking-wide uppercase">
    <div class="w-5 h-px bg-[#333]" />
    <span>Slidev Talk</span>
    <div class="w-5 h-px bg-[#333]" />
  </div>
  <h1 class="!text-[56px] !leading-[1.1] !font-bold text-white max-w-4xl tracking-tight">
    The future of IDE's in<br>the age of agents
  </h1>
  <p class="mt-6 text-lg text-[#888] max-w-2xl leading-relaxed">
    My AI-first coding workflow: the tools, prompts and flows I use to automate the simple parts of engineering work.
  </p>
  <div class="mt-12 flex gap-3 text-[13px]">
    <span class="rounded-full border border-white/10 bg-white/[0.03] px-4 py-1.5 text-[#888]">Agent orchestration</span>
    <span class="rounded-full border border-white/10 bg-white/[0.03] px-4 py-1.5 text-[#888]">Parallel threads</span>
    <span class="rounded-full border border-white/10 bg-white/[0.03] px-4 py-1.5 text-[#888]">Context engineering</span>
  </div>
</div>

<!--
Hey from comment
-->




---
layout: center
class: text-left
---

<h1 class="!text-white !text-4xl !font-bold !tracking-tight">Quick room check</h1>

<div class="mt-10 space-y-4 text-lg max-w-2xl">
  <div class="rounded-xl border border-white/8 bg-white/[0.03] px-6 py-5 text-[#ccc]">
    How many people have multiple versions of the repo they are working in?
  </div>
  <div class="rounded-xl border border-white/8 bg-white/[0.03] px-6 py-5 text-[#ccc]">
    How many people use worktrees specifically?
  </div>
  <div class="rounded-xl border border-white/8 bg-white/[0.03] px-6 py-5 text-[#ccc]">
    How many agents do you run in parallel on average?
  </div>
</div>

---
layout: default
layoutClass: gap-14
---

<h1 class="!text-white !text-4xl !font-bold !tracking-tight">Who am I?</h1>

<div class="mt-8 space-y-4 text-lg text-[#a1a1a1]">
  <div class="flex items-start gap-4">
    <span class="text-[#444] mt-0.5">/01</span>
    <span>Wrote my first line of code at 10 or 11 trying to build a Unity game</span>
  </div>
  <div class="flex items-start gap-4">
    <span class="text-[#444] mt-0.5">/02</span>
    <span>Founder of many failed or sunset startups and side projects</span>
  </div>
  <div class="flex items-start gap-4">
    <span class="text-[#444] mt-0.5">/03</span>
    <span>Before Eleven, I worked as an SDE on software for operating spacecraft</span>
  </div>
  <div class="flex items-start gap-4">
    <span class="text-[#444] mt-0.5">/04</span>
    <span>I do a lot of open source work; biggest claim to fame is <code>Zog</code>, a validation library for Go</span>
  </div>
  <div class="flex items-start gap-4">
    <span class="text-[#444] mt-0.5">/05</span>
    <span>I work mostly on the marketing website</span>
  </div>
</div>



---
layout: image-right
image: /assets/loot.jpeg
class: bg-top
layoutClass: gap-14
---

<h1 class="!text-white !text-4xl !font-bold !tracking-tight">And also!</h1>

<div class="mt-8 space-y-4 text-lg text-[#a1a1a1]">
  <div class="flex items-start gap-4">
    <span class="text-[#444]">--</span>
    <span>I run my own home server</span>
  </div>
  <div class="flex items-start gap-4">
    <span class="text-[#444]">--</span>
    <span>I play Dungeons and Dragons and airsoft</span>
  </div>
  <div class="flex items-start gap-4">
    <span class="text-[#444]">--</span>
    <span>I hate breaking flow, so I hate notifications</span>
  </div>
</div>


---
layout: default
---

<h1 class="!text-white !text-4xl !font-bold !tracking-tight">What I won't discuss today</h1>

<div class="mt-10 space-y-3 text-lg text-[#888]">
  <div class="flex items-center gap-3">
    <span class="w-1.5 h-1.5 rounded-full bg-[#333]" />
    Tools or SOPs for improving agent output
  </div>
  <div class="flex items-center gap-3">
    <span class="w-1.5 h-1.5 rounded-full bg-[#333]" />
    Context engineering
  </div>
  <div class="flex items-center gap-3">
    <span class="w-1.5 h-1.5 rounded-full bg-[#333]" />
    Claude Code specific ideas
  </div>
  <div class="flex items-center gap-3">
    <span class="w-1.5 h-1.5 rounded-full bg-[#333]" />
    Which models are best for what
  </div>
  <div class="flex items-center gap-3">
    <span class="w-1.5 h-1.5 rounded-full bg-[#333]" />
    Skills, MCPs, subagents...
  </div>
</div>

<p class="mt-10 text-sm text-[#555]">But if people are interested in some of that maybe I can come back at some point to chat about it</p>


---
layout: center
class: text-center
---

<div class="max-w-2xl mx-auto">
  <p class="text-sm uppercase tracking-widest text-[#555] mb-6">Confession</p>
  <h2 class="!text-4xl !font-bold !tracking-tight text-white">Guilty admission</h2>
  <div class="w-16 h-px bg-[#333] mx-auto mt-6 mb-6" />
  <p class="text-xl text-[#888]">I was a coding agent skeptic until ~Dec 2025</p>
</div>

<!--
I was using cursor every day, in fact I started in 2023 few months after they launched. 

- But to speed up the work I was doing at the time. very hands on
-->


---
layout: default
class: "!flex !flex-col !overflow-hidden"
---

<h1 class="!text-white !text-3xl !font-bold !tracking-tight !flex-shrink-0">But then something changed</h1>

<p class="!flex-shrink-0 text-[#888] mt-2">New Opus & GPT models. So I started using Cursor's background agents. With and without worktrees.</p>

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

<h1 class="!text-white !text-3xl !font-bold !tracking-tight">I had this problem every week</h1>


---
layout: center
---

<h1 class="!text-white !text-4xl !font-bold !tracking-tight">4 Cursor instances</h1>

<p class="text-[#888] mt-2">I found myself with 4 Cursor instances open, juggling between them.</p>

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

<div class="text-center">
  <p class="text-sm uppercase tracking-widest text-[#555] mb-6">Exploration</p>
  <h1 class="!text-6xl !font-bold !tracking-tight text-white">Cloud agents</h1>
</div>

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
layout: center
class: text-center
---

<div class="max-w-2xl mx-auto">
  <h2 class="!text-4xl !font-bold !tracking-tight text-white">What am I doing wrong?</h2>
  <div class="w-16 h-px bg-[#333] mx-auto mt-6 mb-6" />
  <p class="text-xl text-[#888]">Someone has to have figured this out already. Let's research.</p>
</div>


---
layout: center
class: text-center
---

<div>
  <p class="text-sm uppercase tracking-widest text-[#555] mb-4">Research</p>
  <h2 class="!text-5xl !font-bold !tracking-tight text-white">Current solution shapes</h2>
</div>

---
zoom: 0.82
---

<h1 class="!text-white !text-3xl !font-bold !tracking-tight">IDEs</h1>

<div class="mt-8 grid grid-cols-2 gap-5 max-w-5xl mx-auto">
  <div class="overflow-hidden rounded-xl border border-white/8 bg-white/[0.02]">
    <img src="./assets/solution-shapes/cursor.png" class="h-64 w-full object-cover object-top opacity-90" alt="Cursor homepage screenshot" />
    <div class="px-5 py-3 border-t border-white/8">
      <div class="text-white text-base font-medium">Cursor</div>
    </div>
  </div>
  <div class="overflow-hidden rounded-xl border border-white/8 bg-white/[0.02]">
    <img src="./assets/solution-shapes/windsurf.png" class="h-64 w-full object-cover object-top opacity-90" alt="Windsurf homepage screenshot" />
    <div class="px-5 py-3 border-t border-white/8">
      <div class="text-white text-base font-medium">Windsurf</div>
    </div>
  </div>
</div>

---
zoom: 0.82
---

<h1 class="!text-white !text-3xl !font-bold !tracking-tight">Kanban</h1>

<div class="mt-8 grid grid-cols-2 gap-5 max-w-5xl mx-auto">
  <div class="overflow-hidden rounded-xl border border-white/8 bg-white/[0.02]">
    <img src="./assets/solution-shapes/vibe-kanban.png" class="h-72 w-full object-cover object-top opacity-90" alt="Vibe Kanban homepage screenshot" />
    <div class="px-5 py-3 border-t border-white/8">
      <div class="text-white text-base font-medium">Vibe Kanban</div>
    </div>
  </div>
  <div class="overflow-hidden rounded-xl border border-white/8 bg-white/[0.02]">
    <img src="https://automaker.app/card.png" class="h-72 w-full object-cover object-top opacity-90" alt="Automaker share image" />
    <div class="px-5 py-3 border-t border-white/8">
      <div class="text-white text-base font-medium">Automaker</div>
    </div>
  </div>
</div>


---
zoom: 0.76
---

<h1 class="!text-white !text-3xl !font-bold !tracking-tight">Cloud agents</h1>

<div class="mt-8 grid grid-cols-3 gap-4 text-left text-sm">
  <div class="overflow-hidden rounded-xl border border-white/8 bg-white/[0.02]">
    <img src="./assets/solution-shapes/claude.png" class="h-52 w-full object-cover object-top opacity-90" alt="Claude homepage screenshot" />
    <div class="px-4 py-3 border-t border-white/8">
      <div class="text-white text-base font-medium">Claude</div>
    </div>
  </div>
  <div class="overflow-hidden rounded-xl border border-white/8 bg-white/[0.02]">
    <img src="./assets/solution-shapes/cursor.png" class="h-52 w-full object-cover object-top opacity-90" alt="Cursor homepage screenshot" />
    <div class="px-4 py-3 border-t border-white/8">
      <div class="text-white text-base font-medium">Cursor</div>
    </div>
  </div>
  <div class="overflow-hidden rounded-xl border border-white/8 bg-white/[0.02]">
    <img src="./assets/solution-shapes/devin.png" class="h-52 w-full object-cover object-top opacity-90" alt="Devin homepage screenshot" />
    <div class="px-4 py-3 border-t border-white/8">
      <div class="text-white text-base font-medium">Devin</div>
    </div>
  </div>
</div>

---
zoom: 0.76
---

<h1 class="!text-white !text-3xl !font-bold !tracking-tight">Agent first</h1>

<div class="mt-8 grid grid-cols-4 gap-4 text-left text-sm">
  <div class="overflow-hidden rounded-xl border border-white/8 bg-white/[0.02]">
    <img src="./assets/solution-shapes/t3-codes.png" class="h-52 w-full object-cover object-top opacity-90" alt="T3 Code homepage screenshot" />
    <div class="px-4 py-3 border-t border-white/8">
      <div class="text-white text-sm font-medium">T3 Code</div>
    </div>
  </div>
  <div class="overflow-hidden rounded-xl border border-white/8 bg-white/[0.02]">
    <img src="./assets/solution-shapes/cursor.png" class="h-52 w-full object-cover object-top opacity-90" alt="Cursor 3.0 screenshot" />
    <div class="px-4 py-3 border-t border-white/8">
      <div class="text-white text-sm font-medium">Cursor 3.0</div>
    </div>
  </div>
  <div class="overflow-hidden rounded-xl border border-white/8 bg-white/[0.02]">
    <img src="./assets/solution-shapes/conductor.png" class="h-52 w-full object-cover object-top opacity-90" alt="Conductor homepage screenshot" />
    <div class="px-4 py-3 border-t border-white/8">
      <div class="text-white text-sm font-medium">Conductor</div>
    </div>
  </div>
  <div class="overflow-hidden rounded-xl border border-white/8 bg-white/[0.02]">
    <img src="./assets/solution-shapes/superset.png" class="h-52 w-full object-cover object-top opacity-90" alt="Superset homepage screenshot" />
    <div class="px-4 py-3 border-t border-white/8">
      <div class="text-white text-sm font-medium">Superset</div>
    </div>
  </div>
</div>

---
zoom: 0.82
layout: image
image: https://miro.medium.com/v2/resize:fit:700/1*ReBwrC1sc9USnhvYXcrd4A.jpeg
---

<!-- <h1 class="!text-white">Gastown</h1> -->


<!--
Gastown. Orchestrator first
-->

---
layout: center
---

<div class="text-center">
  <p class="text-sm uppercase tracking-widest text-[#555] mb-6">My approach</p>
  <h1 class="!text-6xl !font-bold !tracking-tight text-white">Build your own</h1>
</div>



---
layout: center
zoom: 0.82
---

<h1 class="!text-white !text-3xl !font-bold !tracking-tight text-center mb-10">Thinking in threads</h1>

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

<h1 class="!text-white !text-3xl !font-bold !tracking-tight">Creator of OpenClaw</h1>

<Tweet id="2019903946056237516" scale="0.85" />



<!--
- Is vibe coding
- We cannot go that far yet without disastrous consequences
-->


---
layout: center
class: text-center
---

<div class="max-w-2xl mx-auto">
  <h2 class="!text-4xl !font-bold !tracking-tight text-white">Switched to Neovim <span class="text-[#555]">~btw</span></h2>
  <div class="w-16 h-px bg-[#333] mx-auto mt-6 mb-6" />
  <p class="text-xl text-[#888]">One persistent session per thread of work</p>
</div>

<!--
- Wanted one persistent session per thread of work
- Each thread gets its own neovim session that stays alive
- No more juggling multiple IDE windows or forgetting where things are
-->


---
layout: default
---

<h1 class="!text-white !text-4xl !font-bold !tracking-tight">How I work</h1>

<div class="mt-10 space-y-4 text-xl">
  <div class="flex items-center gap-4 text-[#ccc]">
    <span class="text-xs font-mono text-[#555] w-6 text-right">01</span>
    <div class="w-px h-4 bg-[#333]" />
    <span>Throw / kick off</span>
  </div>
  <div class="flex items-center gap-4 text-[#ccc]">
    <span class="text-xs font-mono text-[#555] w-6 text-right">02</span>
    <div class="w-px h-4 bg-[#333]" />
    <span>Work</span>
  </div>
  <div class="flex items-center gap-4 text-[#ccc]">
    <span class="text-xs font-mono text-[#555] w-6 text-right">03</span>
    <div class="w-px h-4 bg-[#333]" />
    <span>Go to what needs me</span>
  </div>
  <div class="flex items-center gap-4 text-[#ccc]">
    <span class="text-xs font-mono text-[#555] w-6 text-right">04</span>
    <div class="w-px h-4 bg-[#333]" />
    <span>Push PRs</span>
  </div>
  <div class="flex items-center gap-4 text-[#ccc]">
    <span class="text-xs font-mono text-[#555] w-6 text-right">05</span>
    <div class="w-px h-4 bg-[#333]" />
    <span>PR merge = session deleted</span>
  </div>
</div>

<p class="mt-10 text-[#555] text-base italic border-l-2 border-[#333] pl-4">Effectively I'm a pull-based system on what needs me</p>

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

<h1 class="!text-white !text-4xl !font-bold !tracking-tight">Why this works</h1>

<div class="mt-10 space-y-4 text-lg">
  <div class="rounded-xl border border-white/8 bg-white/[0.03] px-6 py-5 text-[#ccc]">No need to keep context of what I'm working on</div>
  <div class="rounded-xl border border-white/8 bg-white/[0.03] px-6 py-5 text-[#ccc]">Switching threads is instant</div>
  <div class="rounded-xl border border-white/8 bg-white/[0.03] px-6 py-5 text-[#ccc]">Everything is isolated — environment auto-setup</div>
  <div class="rounded-xl border border-white/[0.15] bg-white/[0.05] px-6 py-5 text-white font-medium">Hydration!</div>
</div>

<!--
- I only have to think about the next thing and poll from the queue. No juggling mental context across threads
- Moving from one thread of work to the next is instant — just switch to the session
- Each worktree is fully isolated. Environment is automatically set up at creation time
- Hydration: when I jump into a session, the agent has already done work and left me context. I hydrate into the thread quickly rather than rebuilding context from scratch
-->




---
layout: center
class: text-center
---

<div class="max-w-3xl mx-auto">
  <p class="text-sm uppercase tracking-widest text-[#555] mb-6">Takeaway</p>
  <h2 class="!text-4xl !font-bold !tracking-tight text-white leading-snug">Bottom line</h2>
  <div class="w-16 h-px bg-[#333] mx-auto mt-6 mb-6" />
  <p class="text-xl text-[#888] leading-relaxed">The future is probably agent-first apps</p>
  <p class="mt-4 text-lg text-[#555]">But I don't want to wait 8s for Cursor to open, so I'm stuck in crazy land</p>
</div>

<!--
- Agent-first apps like T3 Code, Conductor, etc. are likely the direction everything is heading
- But the overhead of GUI-heavy tools kills flow — 8 seconds to open Cursor is 8 seconds too many
- So for now, neovim + worktrees + custom orchestration is the sweet spot for me
- "Crazy land" = building your own workflow tooling, but it works
-->


---
layout: center
class: text-center
---

<div class="max-w-2xl mx-auto">
  <h2 class="!text-4xl !font-bold !tracking-tight text-white">But at least I can say</h2>
  <p class="mt-4 text-2xl text-[#888]">I use nvim btw</p>
</div>


---
layout: center
class: text-center
---

<div>
  <h1 class="!text-6xl !font-bold !tracking-tight text-white">Questions?</h1>
  <div class="w-16 h-px bg-[#333] mx-auto mt-8" />
</div>



---
layout: center
class: text-center
---

<div>
  <div class="w-16 h-px bg-[#333] mx-auto mb-8" />
  <p class="text-sm uppercase tracking-widest text-[#555] mb-4">Looking ahead</p>
  <h2 class="!text-5xl !font-bold !tracking-tight text-white">Into the future</h2>
  <p class="mt-4 text-lg text-[#666]">What I'm working on, what I'd like & where I think things are going</p>
  <div class="w-16 h-px bg-[#333] mx-auto mt-8" />
</div>


---
layout: default
zoom: 0.88
---

<h1 class="!text-white !text-4xl !font-bold !tracking-tight">Levels of autonomy</h1>

<div class="mt-8 space-y-3 text-lg">
  <div class="rounded-xl border border-white/8 bg-white/[0.03] px-5 py-4 flex items-center gap-4">
    <span class="font-mono text-sm text-[#666] bg-white/[0.05] rounded-md px-2.5 py-1 border border-white/8 min-w-[36px] text-center">L0</span>
    <span class="text-[#a1a1a1]">No autonomy — each step interrupts you</span>
  </div>
  <div class="rounded-xl border border-white/8 bg-white/[0.03] px-5 py-4 flex items-center gap-4">
    <span class="font-mono text-sm text-[#666] bg-white/[0.05] rounded-md px-2.5 py-1 border border-white/8 min-w-[36px] text-center">L1</span>
    <span class="text-[#a1a1a1]">Implementation — research, plan, implement, commit</span>
  </div>
  <div class="rounded-xl border border-white/8 bg-white/[0.03] px-5 py-4 flex items-center gap-4">
    <span class="font-mono text-sm text-[#666] bg-white/[0.05] rounded-md px-2.5 py-1 border border-white/8 min-w-[36px] text-center">L2</span>
    <span class="text-[#a1a1a1]">PR — previous + open PR</span>
  </div>
  <div class="rounded-xl border border-white/8 bg-white/[0.03] px-5 py-4 flex items-center gap-4">
    <span class="font-mono text-sm text-[#666] bg-white/[0.05] rounded-md px-2.5 py-1 border border-white/8 min-w-[36px] text-center">L3</span>
    <span class="text-[#a1a1a1]">Semi-full — previous + address feedback</span>
  </div>
  <div class="rounded-xl border border-white/[0.15] bg-white/[0.05] px-5 py-4 flex items-center gap-4">
    <span class="font-mono text-sm text-white bg-white/[0.08] rounded-md px-2.5 py-1 border border-white/[0.15] min-w-[36px] text-center">L4</span>
    <span class="text-white font-medium">Vibe — previous + merge</span>
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

<h1 class="!text-white !text-4xl !font-bold !tracking-tight"><s class="text-[#555]">Cloud agents</s> Cloud sessions</h1>
<p class="text-[#666] mt-1">Local-like IDE experience</p>

<div class="mt-8 space-y-4 text-lg">
  <div class="rounded-xl border border-white/8 bg-white/[0.03] px-6 py-5 text-[#ccc]">
    Sessions run remotely, not on your machine
  </div>
  <div class="rounded-xl border border-red-500/20 bg-red-500/[0.04] px-6 py-5">
    <span class="text-red-400/80 text-sm font-mono">Challenge:</span>
    <span class="text-[#ccc] ml-2">Secrets management</span>
  </div>
  <div class="rounded-xl border border-white/8 bg-white/[0.03] px-6 py-5 text-[#ccc]">
    <span class="text-[#666] text-sm font-mono">Provider model:</span>
    <span class="ml-2">fly.io design</span>
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

<h1 class="!text-white !text-4xl !font-bold !tracking-tight">Reset to step</h1>

<div class="mt-10">

```mermaid {scale: 0.85}
flowchart LR
  R[Research] --> P[Plan]
  P --> I[Implementation]
  I --> V[Review]
  R -. "reset" .- I
  P -. "reset" .- V
```

</div>

<p class="mt-8 text-[#888] text-lg">Go back to a previous step and iterate from there</p>

<!--
- Implementation is bad? Go back to plan, see what the issue is, iterate from there
- Plan is bad? Go back to research
- This is like git reset but for the agent workflow itself — you rewind the thread to an earlier stage
- Avoids starting from scratch when only one phase went wrong
-->


---
layout: center
class: text-center
---

<div class="max-w-2xl mx-auto">
  <h1 class="!text-5xl !font-bold !tracking-tight text-white">Port isolation</h1>
</div>
