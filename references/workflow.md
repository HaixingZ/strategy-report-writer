# Workflow

Use this workflow when the user wants a strategy report with staged checkpoints, modular drafting, and durable Markdown outputs.

## Operating principles

- Confirm storyline before modules.
- Confirm modules before module contracts.
- Confirm module contracts before executors.
- Default to Chinese output unless the user asks for another language.
- Keep evidence discipline lightweight: cite known sources, distinguish inference from evidence, and label missing support as an assumption or evidence gap.
- Treat `evidence sufficiency` as reasonable coverage of accessible public sources. Do not require private, interview-only, or proprietary inputs to be resolved inside the draft.
- Ask once for user-provided reference material and preserve it as a `Source Pack` when available.
- Use Markdown links for all public citations in `[来源名称](URL)` format. Do not cite public sources by name alone.

## Fixed sequence

1. Clarify the brief.
   Gather the decision problem, audience, purpose, time window, geography, object definition, must-cover entities, must-use sources, and output shape.
   Ask once: `您是否有参考来源（URL、文档或文本摘录）希望纳入报告？`
   If the user provides any, assemble them into a `Source Pack` as a flat list of linked entries plus one-line descriptions and attach it to the approved brief.
2. Produce `Storyline Packet`.
   Use the exact contract from `output-contracts.md`. Do not write report body yet.
   Immediately after emitting it in chat, write it to `storyline-YYYYMMDD-{title-slug}.md` in the current working directory.
3. Stop for storyline confirmation.
   Revise the packet until the user accepts the title, thesis, narrative arc, boundaries, and proposed sections.
4. Produce `Module Confirmation`.
   Derive modules from the approved storyline. Modules may split, merge, or trim sections, but must not silently change thesis or narrative arc.
   Immediately after emitting it in chat, write it to `module-confirmation-YYYYMMDD-{title-slug}.md`.
5. Stop for module confirmation.
   Confirm selected modules, out-of-scope items, owner map, and must-answer questions before starting executor work.
6. Produce one `Module Contract` per confirmed module.
   Define scope boundaries, must-answer questions, public evidence plan, known evidence limits, and done definition before drafting.
   Immediately after emitting each contract in chat, write it to `module-contract-YYYYMMDD-{module-slug}.md`.
7. Run evaluator preflight.
   Review each module contract against the approved storyline and module confirmation. Revise contracts before any executor begins drafting.
   Immediately after emitting each contract review in chat, write it to `evaluation-report-YYYYMMDD-{module-slug}-contract.md`.
8. Assign Executors.
   Use one Executor per approved module, with a default cap of 4 executors. If more than 4 modules remain, merge adjacent modules or split execution into batches.
9. Draft modules.
   Each Executor owns one module end-to-end: judgment, key findings, public evidence coverage, evidence gaps, linked citations, and first draft.
10. Run evaluator review.
   Review each module against the approved storyline, approved module contract, active style profile, and public-source coverage standard. Use `ready` or `revise` only.
   Immediately after emitting each module review in chat, write it to `evaluation-report-YYYYMMDD-{module-slug}.md`.
11. Allow one rewrite round.
   If a module is `revise`, send the module back to the same Executor once with a concrete rewrite brief.
   Once a module is `ready`, write the approved module draft to `module-draft-YYYYMMDD-{module-slug}.md`.
12. Finalize the report.
    Consolidate all material unresolved gaps into an `Evidence Gap Register`.
    Produce `Final Delivery` only after all confirmed modules are `ready`. `Final Report` must be the full integrated report body, not a compressed memo.
    Append 1-3 Nano Banana prompts based on the completed report.
    Immediately after emitting `Final Delivery` in chat, write it to `report-YYYYMMDD-{title-slug}.md`.

## Gate rules

- Do not write the full report before storyline confirmation.
- Do not start any Executor before module confirmation and evaluator approval of the module contract.
- Do not let module changes quietly rewrite the thesis.
- Do not add Nano Banana prompts before `Final Delivery`.
- Do not omit the `Source Pack` from the working brief when the user provided sources.
- Do not omit the `Evidence Gap Register` from `Final Delivery`. If no material gaps remain, write `- 无重大证据缺口`.
- Do not hide weak support. Explicitly label `Assumption` or `Evidence Gap` when support is incomplete.
- Do not fail a module only because some required evidence is non-public. Fail when accessible public evidence was skipped, evidence gaps were hidden, or certainty exceeds support.
- Do not cite a public source by name alone. Use a Markdown link.
- Do not skip writing the required Markdown files after emitting public artifacts, approved module drafts, or `Final Delivery`.

## Rollback rules

- Return to storyline confirmation if the user changes the thesis, narrative arc, boundaries, or section logic.
- Return to module confirmation if the user changes module scope, owner mapping, or must-answer questions after module lock.
- Return to module contract review if evaluator finds the public evidence plan, scope boundary, or done definition too weak for execution.
- Stop after the single rewrite round if a module still fails review. Present the latest `Evaluation Report` and ask for either more public evidence, tighter scope, or a changed standard before continuing.

## What to avoid

- Do not simulate the Planner / Executor / Evaluator workflow inside one agent when subagent creation is expected.
- Do not confuse “style” with “accuracy”. Accuracy, clarity, and explicit boundaries always win.
- Do not let a single Executor rewrite the whole report outside its assigned module.
