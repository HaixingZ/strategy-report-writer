---
name: strategy-report-writer
description: Use when the user wants a strategy report, market study, industry analysis, or decision memo from a loose brief and the task needs thesis clarification, modular analysis, linked citations, source-pack handling, and explicit evidence-gap tracking.
---

# Strategy Report Writer

Use this skill to run a gated strategy-report workflow with staged approvals, modular drafting, and explicit evidence discipline.

## When to Use

- The brief is still loose and the thesis needs to be sharpened before drafting.
- The report needs staged approval of storyline and modules.
- Different sections need separate owners or research angles.
- Public evidence quality varies across modules and missing support must stay visible.
- The user wants a strategy-report workflow, not a one-pass generic essay.

## Core Workflow

1. Clarify only missing boundary details such as audience, decision problem, time window, geography, must-cover entities, and output shape. Ask once whether the user has reference sources and preserve them as a `Source Pack` if provided.
2. Produce `Storyline Packet` and stop for approval before any report drafting.
3. Produce `Module Confirmation` and stop again if the storyline is approved.
4. Produce one `Module Contract` per module and have Evaluator review contracts before drafting starts.
5. Spawn one Executor per approved module. If subagents are blocked, stop and report the blocker.
6. Review every module draft with Evaluator and allow at most one rewrite round per module.
7. Produce `Final Delivery` only after all modules are `ready`. `Final Report` must be the complete integrated research report, include an `Evidence Gap Register`, then append Nano Banana prompts.
8. Write every public artifact, every approved module draft, and `Final Delivery` to Markdown files in the current working directory.

## Evidence Standard

- Treat sufficiency as reasonable coverage of accessible public sources for the approved scope and time available.
- Treat a user-provided `Source Pack` as the highest-authority evidence tier inside the approved scope.
- When a public source is cited, cite it as a Markdown link in `[来源名称](URL)` format. Do not cite public sources by name alone.
- If support likely requires interviews, proprietary data, or other non-public inputs, mark the missing support as `Evidence Gap`.
- Fail drafts that skip accessible public evidence, hide evidence gaps, or overstate certainty.

## Guardrails

- No full report before storyline approval.
- No Executor before module approval and contract approval.
- No single-agent simulation of Planner / Executor / Evaluator when subagents are expected.
- No single Executor rewriting the whole report outside its assigned module. If there are too many modules, merge or batch them through the workflow rules instead of collapsing ownership.
- No public citation without a link.
- No dropping or contradicting a user-supplied `Source Pack` without flagging the conflict explicitly.
- No omitting the `Evidence Gap Register` from `Final Delivery`.
- No skipping the Markdown file write for public artifacts, approved module drafts, or `Final Delivery`.
- No fabricated evidence.

## References

- Read [references/workflow.md](references/workflow.md) for the exact sequence, evaluator gates, and rollback rules.
- Read [references/subagents.md](references/subagents.md) for Planner / Executor / Evaluator responsibilities.
- Read [references/output-contracts.md](references/output-contracts.md) before emitting any public artifact.
- Read [references/style-system.md](references/style-system.md) first when choosing or overriding prose style.
- Read [references/style-presets/analytical-operator.md](references/style-presets/analytical-operator.md) by default.
- Read [references/style-profile.md](references/style-profile.md) when the user wants a more neutral fallback voice.
