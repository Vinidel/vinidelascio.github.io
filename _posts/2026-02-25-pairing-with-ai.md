---
layout: post
title: "How I’m Pairing With Codex/Cursor Using Roles, Gates, and Repeatable Artifacts"
date: 2026-02-25
description: "I turned my AI coding workflow into a structured, repeatable system using role-based agents, stage gates, and shared project context."
categories: engineering ai workflow
---

<figure class="diagram-figure">
  <img src="{{ '/assets/images/new-workflow-hero-diagram-2026-02-25-053213.svg' | relative_url }}" alt="AI Dev Cycle" />
</figure>

## I Stopped “Just Prompting” and Built a Repeatable AI Workflow

  I’ve been experimenting with AI-assisted development for a while, and I already wrote about the idea of using agents for software work.

  What changed recently is that the pattern stopped feeling like a clever setup and started feeling like a real workflow.

  I’ve been maturing it inside a real project (`my-menu`), and now I’m using **Codex** (and sometimes **Cursor**) to run the same set of agents from `.cursor/rules/`. The result is simple:

  AI is faster now, but more importantly, it’s becoming **structured, predictable, and repeatable**.

## The Core Shift

  The big change was moving from: **“ask the AI to do a task”**

  to: **“run a stage in a workflow with a clear role, inputs, outputs, and exit gate”**

  That sounds small, but it changes everything. Instead of hoping the model does the right thing, I give it a **job** inside a process.

## The Pattern I’m Using

  In this repo, I defined a stage-gated workflow in `workflow/WORKFLOW.md` with explicit roles:

- Orchestrator (brief/scope)
- Implementer (code)
- Tester (tests from acceptance criteria)
- Refactorer (structure only)
- Hardener (risk sweep)
- Documenter (decisions/gaps/ops notes)
- Critic (reviews every stage)

  This is the key idea: **the Critic reviews every stage before the next one starts**. That one rule alone reduces a lot of “AI momentum mistakes” (where something looks good and moves forward too quickly).

## Why This Works Better Than a Single “Super Prompt”

  Because each agent has:

- a narrow mission
- explicit allowed/not-allowed actions
- a stage exit gate
- required outputs

  Example: the Implementer is explicitly told to stay inside the brief and avoid refactors/optimization. The Tester is explicitly told to derive tests from the brief, not the
  implementation. The Hardener is explicitly focused on security/perf/observability/resilience.

  That separation makes the outputs more consistent and makes it easier for me to review.

## The Most Important File: `PROJECT.md`

  A big maturity improvement was introducing a real project context file (`PROJECT.md`) and making **every agent read it first**.

  That file became the shared memory for:

- product scope
- architecture
- conventions
- locked decisions
- constraints
- glossary
- current status

  This solved a recurring problem: agents making “reasonable” decisions that were wrong for *this* project.

  Now the workflow is reusable, but the project behavior is grounded.

## The Workflow Produces Artifacts, Not Just Code

  Another reason this is working: each stage leaves evidence.

  The repo now accumulates useful artifacts like:

- `docs/briefs/*.md` (scope and acceptance scenarios)
- `docs/critique.md` (stage review feedback)
- `docs/implementation-notes.md` (out-of-scope issues spotted during implementation)
- `docs/hardening-notes.md` (risks, assumptions, deferred items)
- feature delivery docs in `docs/*.md`

  This creates a lightweight audit trail of how a feature matured, not just the final code diff.

  That matters when working with AI because the real risk is not only bad code, it’s **hidden decisions**.

<figure>
  <img src="{{ '/assets/images/new-workflow-full-diagram-2026-02-25-053158.svg' | relative_url }}" alt="AI Dev Cycle" />
</figure>

## What Matured in the Last Few Days

  A few things made this feel much more stable recently:

### 1) Clear role boundaries in `.cursor/rules/`

  Each agent file is now explicit about mission, constraints, and exit gates.
  This reduced role drift a lot.

### 2) Critic as a mandatory gate (not optional review)

  The Critic is not “nice to have”. It’s the brake pedal.

### 3) Stage labels and PR progression

  The workflow maps stages to PR maturity states, so the process is visible and not just in my head.

### 4) A Gate Keeper for git/PR hygiene

  I added a `gatekeeper` rule to enforce commit/push/PR updates in the same staged workflow.
  This is important because process breaks often happen at the VCS/PR layer, not only in coding.

### 5) Reusability across tools (Codex and Cursor)

  The workflow lives in repo files, not in one vendor UI.
  That means I can run the same pattern with different AI tools and keep the process consistent.

## Real Benefit I’m Seeing

  The biggest win is not “AI writes more code”.

  It’s that I can now pair with the agent in a way that feels closer to working with a junior/mid engineer inside a defined team process:

- I set direction
- the agent executes a stage
- the critic reviews
- we move forward only when the stage is actually done

  This keeps velocity high without turning the project into chaos.

## What I’d Recommend If You Want to Try This

  Start small and make it boring:

  1. Create a `PROJECT.md` and force every agent to read it first.
  2. Split work into stages (brief, implement, test, refactor, harden, document).
  3. Give each stage a dedicated role with clear “not allowed” rules.
  4. Add a critic/reviewer step between stages.
  5. Require written artifacts (briefs, critique, hardening notes), not only code.
  6. Treat PR state as part of the workflow, not an afterthought.

  Don’t optimize for the smartest prompt.
  Optimize for a workflow you can run again next week.

## Final Thought

  AI gets impressive results quickly, but sustainable progress comes from structure.

  What I’m building now is less about “autonomous AI” and more about a **reliable collaboration system**: human direction + role-based agents + stage gates + artifacts.

  That combination has been working well for me, and it’s becoming my default way to ship features with AI.

  Repo-specific details I used

- Workflow definition: `workflow/WORKFLOW.md`
- Shared project context pattern: `PROJECT.md`
- Agent roles:
  - `.cursor/rules/orchestrator.mdc`
  - `.cursor/rules/implementer.mdc`
  - `.cursor/rules/tester.mdc`
  - `.cursor/rules/refactorer.mdc`
  - `.cursor/rules/hardener.mdc`
  - `.cursor/rules/documenter.mdc`
  - `.cursor/rules/critic.mdc`
- PR/VCS flow guard: `.cursor/rules/gatekeeper.md`
