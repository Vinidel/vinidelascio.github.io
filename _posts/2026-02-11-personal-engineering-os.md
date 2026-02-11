---
layout: post
title: "Building My Personal Engineering Operating System (With AI)"
date: 2026-02-11
description: "How I introduced stage-gated workflows to tame AI-assisted development — and why structure beats speed."
categories: engineering ai
---

Over the past few weeks, I’ve been experimenting with AI-assisted development on one of my side projects. At first, the experience felt incredibly fast. Then it started to feel chaotic.

The problem wasn’t the AI — it was the absence of structure.

So I introduced a stage-gated workflow — what I now call my Personal Engineering Operating System — and the difference was immediate.

## The Problem With Raw AI Speed

AI can generate:

- Hundreds of lines of code in seconds  
- Refactors instantly  
- Entire test suites on command  
- Architectural suggestions continuously  

The issue isn’t capability. It’s integration speed. AI can easily outpace your ability to:

- Review  
- Reflect  
- Evaluate trade-offs  
- Protect direction  
- Maintain architectural coherence  

When AI outruns you, you stop designing and start reacting. That’s when anxiety creeps in.

## The Solution: Stage-Gated Development

Instead of letting AI “run,” I introduced stages.

Not Jira stages. Not enterprise bureaucracy. Cognitive stages.

Each stage represents a different thinking mode.

## The Six Stages

### Stage 0 — Frame the Work

Before writing production code, I define:

- The problem  
- Success criteria  
- Non-goals  
- Happy and unhappy paths  
- Risks  

**Output:** a simple Feature Brief in `docs/briefs/`.

No code is allowed yet. This prevents scope drift and ambiguity.

### Stage 1 — Make It Work

Now the goal is simple: make it work.

Focus only on:

- The smallest vertical slice  
- Happy path first  
- Unhappy paths next  
- Basic logging  

No refactoring. No optimization. No architectural polishing. Just working behaviour.

### Stage 2 — Lock Behaviour With Tests

Once it works, we protect it.

- Characterisation tests (capture current behaviour)  
- Intent tests (assert desired behaviour)  
- CI must pass  

This stage prevents “refactor regret.”

### Stage 3 — Refactor and Align

Only after behaviour is protected do we improve structure:

- Simplify flows  
- Align naming and patterns  
- Tighten types  
- Reduce duplication  

Behaviour must remain unchanged.

### Stage 4 — Harden and De-Risk

Now we look for surprises:

- Security considerations  
- Dependency health  
- Performance sanity  
- Observability  

Anything risky must be fixed or explicitly documented.

### Stage 5 — PR and Rollout

Finally:

- Clear PR summary  
- Evidence (tests, screenshots)  
- Risks and rollback plan  

The goal is to make it easy to review and safe to ship.

## Why This Worked

Three things changed immediately.

### 1. Less Cognitive Load

I stopped thinking about everything at once. Each stage has a single focus. There’s no mixing of modes.

### 2. Less Scope Drift

For example, I noticed a small unrelated issue during implementation. Previously, I would have fixed it immediately.

Now, Stage 0 defines scope. If it’s not in the brief, it waits.

That alone reduced distraction significantly.

### 3. Less Anxiety

Anxiety often comes from:

- Undefined “done”  
- Too many simultaneous concerns  
- AI moving faster than you  

Stages created checkpoints. Exit gates created clarity. I always knew:

- Where we were  
- What “done” meant  
- What the next micro-step was  

Flow became easier.

## The Most Important Shift

I didn’t slow the AI down — I synchronized with it.

AI generates. I evaluate. We advance a stage. Repeat.

The structure ensures we follow my path, not the AI’s path.

## The Core Principle

AI accelerates execution.  
Structure preserves direction.

Raw AI speed feels productive. Structured AI collaboration feels sustainable.

I now optimize for sustainable throughput, not burst velocity.

## The Meta-Lesson

The real leverage isn’t better prompts. It’s designing environments where AI behaves predictably.

Once I added:

- A stage-based workflow  
- Clear exit gates  
- Structured briefs  
- PR enforcement  

The AI stopped feeling chaotic and started behaving like a disciplined teammate.

## Final Thought

If AI-assisted development feels overwhelming, don’t reduce AI usage.

Introduce structure.  
Separate thinking modes.  
Define exit gates.  
Control cadence.

You don’t need to control the AI.

You need to control the environment it operates in.

If you're experimenting with AI-native engineering workflows, I’d love to compare notes.
