# Subagents

Use these roles to keep the workflow structured and auditable without RIS runtime dependencies.

## Role map

### Partner

Use Partner for pre-writing structure and final synthesis.

Responsibilities:

- Translate the brief into a sharp report thesis.
- Produce `Storyline Packet`.
- Produce `Module Confirmation`.
- Decide module ownership.
- Consolidate the final report after all modules pass review.
- Write the final acceptance note.

Partner must not:

- Draft the whole report before the storyline and modules are confirmed.
- Quietly change thesis or boundaries after confirmation.
- Skip expert ownership for confirmed modules.

### Domain Expert

Use one domain expert per confirmed module.

Responsibilities:

- Own one module end-to-end.
- Research the module question set.
- State the module judgment first.
- List key findings and evidence gaps.
- Draft the module body.

Domain Expert must not:

- Rewrite other modules.
- Change the approved thesis.
- Pretend unsupported claims are verified.

Recommended label when simulating sequentially:

```text
[Expert: <module-name>]
```

### Partner Reviewer

Use Partner Reviewer for module-level quality control.

Responsibilities:

- Review one module at a time.
- Check alignment with approved storyline.
- Check fit with the active style profile.
- On the first pass, always decide `revise` and provide at least one concrete modification point.
- After the rewrite round, decide `ready` or `revise`.
- Issue a focused rewrite brief every time the verdict is `revise`.

Partner Reviewer must not:

- Give vague feedback.
- Fully accept an initial draft on the first pass.
- Approve a module with hidden evidence gaps.
- Expand scope during review.

Recommended label when simulating sequentially:

```text
[Partner Reviewer]
```

## Execution modes

### Parallel mode

Use this when the environment supports subagents.

- Spawn one expert per module.
- Keep the default cap at 4 experts.
- Feed every expert the same approved storyline and active style profile.
- Run partner review after each expert draft returns.

### Sequential fallback

Use this when true subagents are unavailable.

- Keep the same role separation.
- Simulate the workflow in order with explicit labels:
  - `[Partner]`
  - `[Expert: module-a]`
  - `[Partner Reviewer]`
- Preserve the same artifact format and review loop.
- Do not collapse the flow into a single undifferentiated answer.

## Module draft contract

Each expert draft should cover these four elements before review:

1. Module judgment
2. Key findings
3. Evidence gaps
4. Module draft body

Keep these inside the expert workstream. The public artifact headings still come from `output-contracts.md`.
