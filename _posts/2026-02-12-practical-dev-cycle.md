---
layout: post
title: "A Practical AI-Native Dev Cycle (With Real Files and PR Flow)"
date: 2026-02-12
description: "A concrete walkthrough of my stage-gated AI workflow — including file structure, markdown briefs, PR progression, and final documentation."
categories: engineering ai workflow
---
<figure class="diagram-figure">
  <img src="{{ '/assets/images/cycle-high-level.svg' | relative_url }}" alt="AI Dev Cycle" />
</figure>


In my previous post, I introduced my Personal Engineering Operating System — a stage-gated workflow for AI-assisted development.

This post is more practical.

Here’s exactly how a feature moves from idea to merged PR in my setup — including:

- The markdown files created  
- The folder structure  
- How AI uses those files  
- What changes in each stage  
- What the final PR looks like  

No theory. Just mechanics.

---

## The Repository Structure

Here’s the minimal structure that makes this work:

    docs/
      briefs/
        feature-name.md

      engineering/
        personal-engineering-os-v1.md

    .ai/
      WORKFLOW.md

    .github/
      pull_request_template.md

These files are not just documentation for humans.

They shape AI behaviour.

---

## Stage 0 — Feature Brief Creation

When a new feature starts, the first artifact is:

    docs/briefs/daily-mood-logging.md

The brief follows a strict structure:

# Feature Brief Template (Annotated)

This document explains what each section in a Stage 0 Feature Brief is for.

The goal of Stage 0 is clarity, not code.
This document exists to remove ambiguity before implementation begins.

<details class="expandable-template">
<summary><strong>Feature Brief Template (Annotated)</strong> — click to expand</summary>

{% highlight md %}
## Status

Indicates which stage the feature is currently in.

Example:
Stage 0 — Framing

This creates visibility and prevents premature coding.

---

## Alternative name

Optional.

Used to clarify terminology and avoid naming confusion early.
Helps prevent renaming drift during implementation.

---

## Problem

Purpose:
Define the real issue being solved.

This section should:
- Explain the gap in current behavior
- Clarify why the change is needed
- Avoid describing the solution

If this section is unclear, the feature is not ready.

---

## Goal

Purpose:
Define what success looks like.

This should:
- Be concrete
- Be testable
- Avoid future scope creep

If you cannot measure or verify it, it’s not a goal.

---

## Who

Purpose:
Define affected user segments.

This prevents:
- Hidden edge cases
- Partial implementations
- Missed flows

List all user types impacted by the feature.

---

## What We Capture / Change

Purpose:
Clarify data-level changes.

This section should:
- List new fields
- List updated fields
- Clarify storage implications

This helps Stage 1 and Stage 2 later.

---

## Success Criteria

Purpose:
Define the Stage 0 exit conditions.

This should:
- Be written as checkboxes
- Be verifiable
- Map directly to future tests

If these are vague, implementation will drift.

---

## Non-Goals (Out of Scope)

Purpose:
Prevent scope creep.

This is one of the most important sections.

Explicitly state:
- What is NOT included
- What might be future work
- What is intentionally excluded

If it's not here, it’s allowed to creep in later.

---

## Acceptance Scenarios

Purpose:
Translate goals into behavior.

Split into:

### Happy Paths
- Primary successful user flows

### Unhappy Paths
- Validation failures
- API failures
- Edge behaviors
- Retry logic

These become:
- Stage 1 guardrails
- Stage 2 tests

If unhappy paths are missing, refactors will break behavior later.

---

## Edge Cases

Purpose:
Surface unusual but realistic conditions.

Examples:
- Timezones
- Leap years
- Null fields
- Legacy users

This section reduces future surprise.

---

## Approach (Short Rationale)

Purpose:
Outline high-level implementation strategy.

This is not code.

It should:
- Describe DB changes
- Describe routing logic
- Describe flow positioning
- Describe UI intent

This prevents architectural drift in Stage 1.

---

## Decisions (Locked)

Purpose:
Freeze important product/architecture decisions.

Examples:
- Required vs optional
- Editable vs immutable
- Field format decisions
- Explicit flags vs derived state

This prevents re-litigating decisions during implementation.

If a decision changes, Stage 0 must be updated.

---

## Stage 0 Exit Gate

Purpose:
Declare readiness.

Stage 0 is complete when:

- Problem is clear
- Goals are testable
- Non-goals are defined
- Acceptance scenarios include unhappy paths
- Major decisions are locked
- Approach is coherent

{% endhighlight %}

</details>

No production code is written before this file exists.

---

## Stage 1 — Implementation

Now the AI works strictly within the brief.

It:

- Implements only what’s in scope  
- Handles happy + unhappy paths  
- Avoids refactoring or optimization  

If I notice unrelated issues (for example, another page bug), they are not addressed unless the brief changes.

The PR is opened as **Draft** during this stage.

**Label:** `stage-1-impl`

---

## Stage 2 — Tests

Now we lock behaviour.

Tests are generated directly from:

- Happy paths  
- Unhappy paths  
- Edge cases listed in the brief  

CI must pass.

**Label moves to:** `stage-2-tests`

This stage protects against “refactor regret.”

---

## Stage 3 — Refactor

Now that behaviour is protected:

- Improve structure  
- Align naming  
- Remove duplication  
- Tighten types  

Tests must remain green.

**Label:** `stage-3-refactor`

No behaviour changes are allowed.

---

## Stage 4 — Hardening

This is a risk sweep.

Checklist:

- Security concerns?  
- Dependency impact?  
- Performance issues?  
- Logging sufficient?  

If anything risky is found, it’s either fixed or explicitly documented.

**Label:** `stage-4-hardening`

---

## Stage 5 — PR Packaging

The final state of the PR includes:

- Clear summary  
- Link to the brief  
- Screenshots (if UI)  
- Risk section  
- Rollback plan  

The PR template enforces this structure.

**Label:** `ready-for-review`

Now it’s safe to merge.

---

## The PR Lifecycle

Here’s how a typical PR progresses:

    Draft
      → stage-1-impl
      → stage-2-tests
      → stage-3-refactor
      → stage-4-hardening
      → ready-for-review
      → merge

One PR.  
Multiple maturity states.  

Not multiple PRs.

---

## What Changed for Me

This workflow:

- Prevents premature optimization  
- Reduces scope drift  
- Synchronizes AI with human evaluation  
- Creates clear checkpoints  
- Reduces anxiety  
- Improves review quality  

The key insight is simple:

AI generates quickly.  
Integration requires cadence.

The stages create that cadence.

---

## Final Thought

If you’re experimenting with AI-assisted development, try this:

- Don’t optimize your prompts.  
- Optimize your structure.  
- Create stage boundaries.  
- Define exit gates.  
- Use markdown briefs as contracts.  
- Let the PR reflect maturity progression.  

You don’t need to control the AI.

You need to design the environment it operates in.
