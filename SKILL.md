---
name: strategy-report-writer
description: Write strategy reports with a lightweight RIS-inspired workflow that confirms storyline before modules, assigns partner and domain-expert roles, reviews against a writing style, and adds Nano Banana prompts only after the final report. Use when Codex needs to turn a loose business topic into a gated, role-based report process without depending on RIS CLI or heavy traceability artifacts.
---

# Strategy Report Writer

Use this skill to run a simplified report workflow that borrows RIS discipline without depending on RIS CLI, run directories, claim ledgers, or metrics files.

## Quick Start

1. Clarify the brief: topic, audience, purpose, time window, geography, object definition, must-cover companies or products, must-use sources, output shape, and the writing-style source.
2. Produce `Storyline Packet` first and stop. Do not write report body before the user confirms it.
3. After storyline approval, produce `Module Confirmation` and stop. Modules may refine or trim sections, but must not silently change thesis or narrative arc.
4. Assign one domain expert per confirmed module, with a default cap of 4 experts.
5. Have each expert deliver judgment, key findings, evidence gaps, and a module draft. Have Partner review each module with `ready` or `revise`. Allow at most one rewrite round per module.
6. After all modules are `ready`, produce `Final Delivery` and append 1-3 Nano Banana prompts based on the finished report.

## Workflow

### 1. Clarify the brief

- Ask only for missing product intent and boundary details.
- Default to Chinese output unless the user asks otherwise.
- Keep evidence discipline lightweight: cite named sources when available and separate evidence from inference.
- Identify the active writing style in this order: explicit current-turn instruction, user-supplied sample text, explicit alternate preset, then the default house preset.

### 2. Lock storyline first

- Read [references/workflow.md](references/workflow.md) and [references/output-contracts.md](references/output-contracts.md).
- Write `Storyline Packet` with the exact heading and field order from the output contract.
- Stop after the packet and wait for confirmation or edits.

### 3. Confirm modules second

- After storyline approval, propose or refine modules from the approved sections.
- Keep thesis, narrative arc, and section logic stable.
- Return to the storyline gate if module changes would alter the thesis or main structure.

### 4. Run subagents or simulate them

- Read [references/subagents.md](references/subagents.md).
- Use one expert per module when subagents are available.
- If subagents are unavailable, simulate the same roles sequentially with `[Partner]`, `[Expert: <module>]`, and `[Partner Reviewer]` labels.

### 5. Apply style review

- Read [references/style-system.md](references/style-system.md) before choosing any style guidance.
- Use [references/style-presets/analytical-operator.md](references/style-presets/analytical-operator.md) as the default preset.
- Use [references/style-profile.md](references/style-profile.md) as the generic fallback only when no preset fits or when the user asks for a more neutral default strategy-report voice.
- Treat every preset as a reference profile, not a rigid template.
- Let user-supplied style rules or sample text override the selected preset and the default profile.
- Never let style imitation override accuracy, evidence quality, or clarity.

### 6. Finalize the report

- Emit `Partner Review` during revision loops and `Final Delivery` only after all confirmed modules pass review.
- Add Nano Banana prompts only in `Final Delivery`, never in storyline or module confirmation stages.

## Guardrails

- Do not depend on RIS CLI, `run` directories, `claim_ledger.json`, `metrics.json`, or `module_reviews.json`.
- Do not write the full report before storyline confirmation.
- Do not start module experts before module confirmation.
- Do not fabricate evidence, numbers, or certainty. State assumptions, boundary conditions, and evidence gaps explicitly.
- Do not emit RIS-style JSON artifacts. Keep all public outputs as lightweight Markdown.

## References

- Read [references/workflow.md](references/workflow.md) for the fixed sequence, gate rules, and rollback rules.
- Read [references/subagents.md](references/subagents.md) when assigning owners or simulating role-based execution.
- Read [references/style-system.md](references/style-system.md) first when you need to choose, merge, or override prose style.
- Read [references/style-presets/analytical-operator.md](references/style-presets/analytical-operator.md) by default when drafting or reviewing prose style.
- Read [references/style-profile.md](references/style-profile.md) when the user wants a more neutral strategy-report voice or when no preset fits.
- Read [references/output-contracts.md](references/output-contracts.md) before emitting any of the 4 public artifacts.
