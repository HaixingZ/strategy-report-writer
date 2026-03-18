# Workflow

Use this workflow when the user wants a strategy report that keeps RIS-style checkpoints but avoids RIS runtime complexity.

## Operating principles

- Work independently of RIS CLI, run folders, and JSON traceability files.
- Confirm storyline before modules.
- Confirm modules before experts.
- Use real subagents for confirmed modules instead of a single-agent role simulation.
- Default to Chinese output unless the user asks for another language.
- Keep evidence discipline lightweight: cite known sources, distinguish inference from evidence, and label missing support as an assumption or evidence gap.
- When citing a source, always include its URL in `[来源名称](URL)` format. If the URL cannot be verified, append `（URL未确认）`. If no public URL exists, append `（无公开URL）`. Never cite a source by name alone.

## Fixed sequence

1. Clarify the brief.
   Gather the decision problem, audience, purpose, time window, geography, object definition, must-cover entities, must-use sources, and output shape.
2. Produce `Storyline Packet`.
   Use the exact contract from `output-contracts.md`. Do not write report body yet.
3. Stop for storyline confirmation.
   Revise the packet until the user accepts the title, thesis, narrative arc, boundaries, and proposed sections.
4. Produce `Module Confirmation`.
   Derive modules from the approved storyline. Modules may split, merge, or trim sections, but must not silently change thesis or narrative arc.
5. Stop for module confirmation.
   Confirm selected modules, out-of-scope items, owner map, and must-answer questions before starting expert work.
6. Assign domain expert subagents.
   Spawn one expert subagent per confirmed module, with a default cap of 4 experts. Do not ask the user to re-authorize subagent use once this skill is active. If more than 4 modules remain, merge adjacent modules or split execution into batches. If subagents cannot be started, stop and report the blocker rather than simulating expert roles in one agent.
7. Draft modules.
   Each expert owns one module end-to-end: judgment, key findings, evidence gaps, and first draft.
8. Run partner review.
   Review each module against the approved storyline and the active style profile. Use `ready` or `revise` only. The first review of an initial draft must be `revise` and must include at least one concrete modification request.
9. Allow one rewrite round.
   Send the module back to the same expert once with the concrete rewrite brief from the first review.
10. Finalize the report.
    Produce `Final Delivery` only after all confirmed modules are `ready`. Append 1-3 Nano Banana prompts based on the completed report.

## Gate rules

- Do not write the full report before storyline confirmation.
- Do not start any expert before module confirmation.
- Do not let module changes quietly rewrite the thesis.
- Do not add Nano Banana prompts before `Final Delivery`.
- Do not let Partner Reviewer fully accept an initial draft. The first review must create a real revision pass.
- Do not hide weak support. Explicitly label `Assumption` or `Evidence Gap` when support is incomplete.
- Do not silently collapse the workflow into one agent when subagent creation fails.

## Rollback rules

- Return to storyline confirmation if the user changes the thesis, narrative arc, boundaries, or section logic.
- Return to module confirmation if the user changes module scope, owner mapping, or must-answer questions after module lock.
- Stop after the single rewrite round if a module still fails review. Present the latest `Partner Review` and ask for either more evidence, tighter scope, or a changed standard before continuing.

## What to avoid

- Do not simulate RIS artifacts such as `quotes.json`, `claim_ledger.json`, `metrics.json`, or `module_reviews.json`.
- Do not confuse “style” with “accuracy”. Accuracy, clarity, and explicit boundaries always win.
- Do not let a single expert rewrite the whole report outside its assigned module.
