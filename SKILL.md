---
name: strategy-report-writer
description: Write strategy reports with a lightweight RIS-inspired workflow that confirms storyline before modules, spawns one domain-expert subagent per confirmed module, reviews against a writing style, and adds Nano Banana prompts only after the final report. Use when Codex needs to turn a loose business topic into a gated, role-based report process without depending on RIS CLI or heavy traceability artifacts.
---

# Strategy Report Writer

Use this skill to run a simplified report workflow that borrows RIS discipline without depending on RIS CLI, run directories, claim ledgers, or metrics files.

## Quick Start

1. Clarify the brief: topic, audience, purpose, time window, geography, object definition, must-cover companies or products, must-use sources, output shape, and the writing-style source. At the end of brief clarification, ask the user once whether they have reference sources to provide; if yes, collect them into a `Source Pack` (see Workflow § 1).
2. Produce `Storyline Packet` first and stop. Do not write report body before the user confirms it.
3. After storyline approval, produce `Module Confirmation` and stop. Modules may refine or trim sections, but must not silently change thesis or narrative arc.
4. Assign one domain-expert subagent per confirmed module, with a default cap of 4 experts. Once this skill is invoked, do not ask the user to restate a preference for subagents.
5. Have each expert subagent deliver judgment, key findings, evidence gaps, and a module draft. Have Partner review each module with `ready` or `revise`, but never fully accept the first draft. The first review must include concrete modification feedback and a rewrite brief. Allow at most one rewrite round per module.
6. After all modules are `ready`, produce `Final Delivery` and append 1-3 Nano Banana prompts based on the finished report.

## Workflow

### 1. Clarify the brief

- Ask only for missing product intent and boundary details.
- Default to Chinese output unless the user asks otherwise.
- Keep evidence discipline lightweight: cite named sources when available, separate evidence from inference, and always include the source URL in `[来源名称](URL)` format. If the URL cannot be verified, append `（URL未确认）`. If no public URL exists, append `（无公开URL）`.
- Identify the active writing style in this order: explicit current-turn instruction, user-supplied sample text, explicit alternate preset, then the default house preset.
- **Ask once for sources.** At the end of brief clarification, ask the user once: "您是否有参考来源（URL、文档或文本摘录）希望纳入报告？" If the user provides any, assemble them into a `Source Pack`—a flat list of `[name](URL)` entries (or `name（无公开URL）` for non-public items) each with a one-line description of what the source covers—and attach it to the brief. If the user declines or provides nothing, proceed without a Source Pack. Do not ask a second time.

### 2. Lock storyline first

- Read [references/workflow.md](references/workflow.md) and [references/output-contracts.md](references/output-contracts.md).
- Write `Storyline Packet` with the exact heading and field order from the output contract.
- Stop after the packet and wait for confirmation or edits.

### 3. Confirm modules second

- After storyline approval, propose or refine modules from the approved sections.
- Keep thesis, narrative arc, and section logic stable.
- Return to the storyline gate if module changes would alter the thesis or main structure.

### 4. Run required subagents

- Read [references/subagents.md](references/subagents.md).
- Always spawn one expert subagent per confirmed module.
- Once this skill is active, do not ask the user for an additional confirmation before using subagents.
- If subagent creation is blocked by environment or policy constraints, stop and report the blocker instead of simulating the workflow inside one agent.

### 5. Apply style review

- Read [references/style-system.md](references/style-system.md) before choosing any style guidance.
- Use [references/style-presets/analytical-operator.md](references/style-presets/analytical-operator.md) as the default preset.
- Use [references/style-profile.md](references/style-profile.md) as the generic fallback only when no preset fits or when the user asks for a more neutral default strategy-report voice.
- Treat every preset as a reference profile, not a rigid template.
- Let user-supplied style rules or sample text override the selected preset and the default profile.
- Enforce system-level banned sentence formulas such as `不是……而是……` and close variants even when the user asks for another preset.
- Never let style imitation override accuracy, evidence quality, or clarity.

### 6. Finalize the report

- Emit `Partner Review` during revision loops and `Final Delivery` only after all confirmed modules pass review.
- Never mark an initial module draft as fully accepted. The first `Partner Review` must surface at least one concrete change request.
- Add Nano Banana prompts only in `Final Delivery`, never in storyline or module confirmation stages.

## Guardrails

- Do not depend on RIS CLI, `run` directories, `claim_ledger.json`, `metrics.json`, or `module_reviews.json`.
- Do not write the full report before storyline confirmation.
- Do not start module experts before module confirmation.
- Do not simulate the Partner / Expert / Reviewer workflow inside one agent when subagent creation is expected. Surface the blocker and stop instead.
- Do not use `不是……而是……` or close rhetorical variants anywhere in the report.
- Do not let Partner fully accept an initial module draft without a revision pass.
- Do not fabricate evidence, numbers, or certainty. State assumptions, boundary conditions, and evidence gaps explicitly.
- Do not contradict or ignore a user-supplied source without flagging the conflict explicitly.
- Do not cite a source by name alone. Always attach its URL in `[来源名称](URL)` format. If the URL cannot be verified, append `（URL未确认）`. If no public URL exists, append `（无公开URL）`.
- Do not emit RIS-style JSON artifacts. Keep all public outputs as lightweight Markdown.

## References

- Read [references/workflow.md](references/workflow.md) for the fixed sequence, gate rules, and rollback rules.
- Read [references/subagents.md](references/subagents.md) when assigning owners and coordinating required subagent execution.
- Read [references/style-system.md](references/style-system.md) first when you need to choose, merge, or override prose style.
- Read [references/style-presets/analytical-operator.md](references/style-presets/analytical-operator.md) by default when drafting or reviewing prose style.
- Read [references/style-profile.md](references/style-profile.md) when the user wants a more neutral strategy-report voice or when no preset fits.
- Read [references/output-contracts.md](references/output-contracts.md) before emitting any of the 4 public artifacts.
