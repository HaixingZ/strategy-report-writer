# Subagents

Use these roles to keep the workflow structured, auditable, and source-aware.

## Role map

### Planner

Use Planner for pre-writing structure, module contracts, and final synthesis.

Responsibilities:

- Translate the brief into a sharp report thesis.
- Produce `Storyline Packet`.
- Produce `Module Confirmation`.
- Produce one approved `Module Contract` per module before drafting begins.
- Carry forward any approved `Source Pack` into module execution.
- Decide module ownership and batching.
- Consolidate the final report after all modules pass review.
- Write the final acceptance note.
- Consolidate the final `Evidence Gap Register`.

Planner must not:

- Draft the whole report before the storyline and modules are confirmed.
- Quietly change thesis or boundaries after confirmation.
- Skip evaluator review of module contracts.
- Skip Executor ownership for confirmed modules.

### Executor

Use one Executor per approved module.

Responsibilities:

- Own one module end-to-end.
- Research the module question set using the approved module contract.
- Cover user-provided `Source Pack` items before expanding to lower-priority public evidence.
- State the module judgment first.
- List key findings and evidence gaps.
- State public evidence coverage before claiming completeness.
- Use Markdown links for public citations instead of bare source names.
- Draft the module body.

Executor must not:

- Rewrite other modules.
- Change the approved thesis.
- Ignore accessible public sources that fit the approved scope.
- Pretend unsupported claims are verified.

### Evaluator

Use Evaluator for contract-level and module-level quality control.

Responsibilities:

- Review one module contract or one module draft at a time.
- Check alignment with the approved storyline and approved module contract.
- Check whether accessible public sources were reasonably covered for the approved scope.
- Check whether `Source Pack` items were used or explicitly reconciled.
- Distinguish acceptable evidence limits from missed public research.
- Check whether public citations are written as Markdown links.
- Check fit with the active style profile.
- Decide `ready` or `revise`.
- Issue a focused rewrite brief when needed.

Evaluator must not:

- Give vague feedback.
- Fail a module only because some needed information is private, interview-only, or proprietary.
- Approve a module with hidden evidence gaps.
- Expand scope during review.

## Evaluation standard

Use these checks during evaluator review:

- `Thesis and scope alignment`: the draft stays inside the approved thesis, module boundaries, and question set.
- `Public-source coverage`: the draft uses the accessible public evidence that could reasonably be found for this scope and time budget.
- `Source-pack handling`: user-provided sources were covered first or any conflict was flagged explicitly.
- `Evidence-gap disclosure`: missing private or interview-only support is labeled clearly instead of being smuggled in as fact.
- `Analytical clarity`: the judgment is explicit and the logic chain is readable.
- `Citation integrity`: public sources are cited with Markdown links, not bare names.
- `Style fit`: the prose matches the selected style profile without overriding accuracy.

Fail the draft when accessible public sources were skipped, `Source Pack` items were ignored, certainty exceeds support, citations lack links, or evidence gaps were hidden. Do not fail the draft only because some answers require expert interviews or proprietary data.

## Execution modes

### Required subagent mode

- Spawn one Executor per module.
- Keep the default cap at 4 Executors.
- Feed every Executor the same approved storyline, approved module contract, and active style profile.
- Run Evaluator once before drafting begins and again after each module draft returns.

### Blocked mode

- If the environment does not support subagents, stop and report the blocker.
- Do not simulate Planner / Executor / Evaluator sequentially inside one agent.

## Module draft contract

Each Executor draft should cover these five elements before review:

1. Module judgment
2. Key findings
3. Public evidence coverage
4. Evidence gaps
5. Module draft body

Keep these inside the Executor workstream. The public artifact headings still come from `output-contracts.md`.
