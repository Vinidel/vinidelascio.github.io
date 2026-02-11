---
layout: post
title: "Building My Personal Engineering Operating System (With AI)"
date: 2026-02-11
description: "How I introduced stage-gated workflows to tame AI-assisted development — and why structure beats speed."
categories: engineering ai
---

Over the past few weeks, I've been experimenting with AI-assisted development on one of my side projects.

At first, it felt fast.
Then it felt chaotic.
Then I realized the problem wasn't the AI.
It was the lack of structure.

So I built a stage-gated workflow — what I now call my Personal Engineering Operating System.
This changed everything.

## The Problem With Raw AI Speed

AI can generate:

- Hundreds of lines of code in seconds
- Refactors instantly
- Entire test suites on command
- Architectural suggestions continuously

The issue isn't capability.

The issue is integration speed.

AI can outpace your ability to:

- Review
- Reflect
- Evaluate tradeoffs
- Protect direction
- Maintain architectural coherence

When AI outruns you, you stop designing and start reacting.

That's when anxiety creeps in.

## The Solution: Stage-Gated Development

Instead of letting AI "run", I introduced stages.

Not Jira stages.
Not enterprise bureaucracy.

Cognitive stages.

Each stage represents a different thinking mode.

## The Six Stages

### Stage 0 — Frame the Work

Before writing production code:

- Define the problem
- Define success criteria
- Define non-goals
- Write happy and unhappy paths
- Identify risks

**Output:** a simple Feature Brief in `docs/briefs/`.

No code allowed yet.

This prevents scope drift and ambiguity.

### Stage 1 — Make It Work

Focus only on:

- Smallest vertical slice
- Happy path first
- Unhappy paths next
- Basic logging

No refactoring.
No optimization.
No architecture polishing.

Just working behaviour.

### Stage 2 — Lock Behaviour With Tests

Now we protect what we built.

- Characterisation tests (capture current behaviour)
- Intent tests (assert desired behaviour)
- CI must pass

This stage prevents "refactor regret".

### Stage 3 — Refactor and Align

Only after behaviour is protected:

- Improve structure
- Align naming and patterns
- Tighten types
- Reduce duplication

Behaviour must remain unchanged.

### Stage 4 — Harden and De-Risk

Now we check:

- Security considerations
- Dependency health
- Performance sanity
- Observability

Anything risky must be fixed or documented.

### Stage 5 — PR and Rollout

Finally:

- Clear PR summary
- Evidence (tests/screenshots)
- Risks and rollback plan

Make it easy to review and safe to ship.

## Why This Worked

Three things changed immediately:

### 1. Less Cognitive Load

I stopped thinking about everything at once.

Each stage has a single focus.

No mixing modes.

### 2. Less Scope Drift

Example:
I noticed a small unrelated issue during implementation.

Before, I would have fixed it immediately.

Now?
Stage 0 defined scope.
If it's not in the brief, it waits.

That alone reduced distraction massively.

### 3. Less Anxiety

Anxiety often comes from:

- Undefined "done"
- Too many simultaneous concerns
- AI moving faster than you

Stages created checkpoints.

Exit gates created clarity.

I always knew:

- Where we were
- What "done" meant
- What the next micro-step was

Flow became easier.

## The Most Important Shift

I didn't slow the AI down.

I synchronized with it.

AI generates.
I evaluate.
We advance stage.
Repeat.

The structure ensures we follow my path, not the AI's path.

## The Core Principle

AI accelerates execution.
Structure preserves direction.

Raw AI speed feels productive.

Structured AI collaboration feels sustainable.

I now optimize for sustainable throughput, not burst velocity.

## The Meta-Lesson

The real leverage isn't better prompts.

It's designing environments where AI behaves predictably.

Once I added:

- A stage-based workflow
- Clear exit gates
- Structured briefs
- PR enforcement

The AI stopped being chaotic and started feeling like a disciplined teammate.

## Final Thought

If AI-assisted development feels overwhelming,
don't reduce AI usage.

Introduce structure.

Separate thinking modes.

Define exit gates.

Control cadence.

You don't need to control the AI.

You need to control the environment it operates in.

If you're experimenting with AI-native engineering workflows, I'd love to compare notes.
