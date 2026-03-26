# strategy-report-writer

`strategy-report-writer` is a Codex skill for running a gated strategy-report workflow with staged approvals, modular drafting, linked citations, and explicit evidence-gap tracking.

It is designed for market studies, industry research, strategy reports, and decision memos that should not be written as one-pass generic essays.

## What This Skill Does

- sharpens a loose brief into an approved thesis and section logic
- preserves a one-time `Source Pack` when the user provides reference links, files, or excerpts
- uses `Planner / Executor / Evaluator` role separation instead of one-pass drafting
- locks one `Module Contract` per module before drafting starts
- requires public citations to be Markdown links in `[来源名称](URL)` format
- requires `Final Delivery` to be a complete integrated report, not a compressed memo
- requires a final `Evidence Gap Register`
- writes public artifacts, approved module drafts, and the final report to Markdown files in the current working directory

## Workflow At A Glance

1. Clarify only missing boundaries such as audience, decision problem, geography, time window, must-cover entities, and output shape.
2. Ask once whether the user has reference material and preserve it as a `Source Pack` if provided.
3. Produce `Storyline Packet` and stop for approval.
4. Produce `Module Confirmation` and stop again for approval.
5. Produce one `Module Contract` per approved module.
6. Run Evaluator preflight on module contracts before any drafting begins.
7. Draft one module per Executor.
8. Review each module with Evaluator and allow at most one rewrite round.
9. Produce `Final Delivery` only after all modules are `ready`.
10. Write all required artifacts to Markdown files.

## Public Artifacts

The skill defines 5 public artifacts:

1. `Storyline Packet`
2. `Module Confirmation`
3. `Module Contract`
4. `Evaluation Report`
5. `Final Delivery`

`Final Delivery` must contain these top-level sections:

- `Executive Summary`
- `Final Report`
- `Acceptance Note`
- `Evidence Gap Register`
- `Nano Banana Prompts`

The `Final Report` section is the full integrated research body. It is not allowed to collapse this into a short conclusion memo when the user asked for a detailed report.

## Markdown Outputs

The skill writes durable Markdown outputs in the current working directory using predictable names such as:

- `source-pack-YYYYMMDD-{title-slug}.md`
- `storyline-YYYYMMDD-{title-slug}.md`
- `module-confirmation-YYYYMMDD-{title-slug}.md`
- `module-contract-YYYYMMDD-{module-slug}.md`
- `evaluation-report-YYYYMMDD-{module-slug}.md`
- `module-draft-YYYYMMDD-{module-slug}.md`
- `report-YYYYMMDD-{title-slug}.md`

## Evidence Rules

- Evidence sufficiency means reasonable coverage of accessible public sources for the approved scope and time budget.
- A user-provided `Source Pack` is the highest-authority evidence tier inside the approved scope.
- Public sources must be cited as Markdown links, never by bare source name alone.
- If support likely requires interviews, proprietary datasets, or other non-public inputs, the draft must label that gap explicitly as `Evidence Gap`.
- The skill should fail drafts that skip accessible public evidence, hide evidence gaps, or overstate certainty.

## Style Behavior

- By default, the skill uses the house preset in `references/style-presets/analytical-operator.md`.
- If the user gives another tone, sample, or explicit format requirement, the skill layers that on top of the default preset.
- If no preset fits, the skill can fall back to `references/style-profile.md`.

## Repository Contents

- `SKILL.md`: main workflow and guardrails
- `references/workflow.md`: sequence, gate rules, file-write rules, and rollback rules
- `references/output-contracts.md`: public artifact formats
- `references/subagents.md`: Planner / Executor / Evaluator responsibilities
- `references/pressure-scenarios.md`: verification scenarios for skill testing
- `references/style-system.md`: style selection and override rules
- `references/style-profile.md`: generic fallback voice
- `references/style-presets/analytical-operator.md`: default house style preset
- `agents/openai.yaml`: UI metadata
- `output/`: example artifacts

## Install

Copy this repository into `$CODEX_HOME/skills/strategy-report-writer`

Example:

```bash
cp -R strategy-report-writer "$CODEX_HOME/skills/"
```

## Updating The Default Style

1. Add or edit a preset under `references/style-presets/`
2. Update the default preset rule in `references/style-system.md`
3. Keep `SKILL.md` focused on workflow, not prose examples
