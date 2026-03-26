# Output Contracts

Use these exact top-level headings for the 5 public artifacts. Keep the field order stable.

## Global prohibitions

- Do not write the full report before `Storyline Packet` is approved.
- Do not start executor work before `Module Confirmation` is approved.
- Do not start executor work before the relevant `Module Contract` is approved.
- Do not include Nano Banana prompts outside `Final Delivery`.
- Do not cite a public source by name alone. Use a Markdown link.
- Do not hide weak support. Use `Assumption` or `Evidence Gap` when necessary.

## Artifact 1

```markdown
# Storyline Packet

## Title

## Thesis

## Narrative Arc

## Proposed Sections

## Open Questions

## Boundaries
```

Field guidance:

- `Title`: one report title only.
- `Thesis`: the main judgment the report is trying to prove.
- `Narrative Arc`: 3-6 bullets that explain the logic flow.
- `Proposed Sections`: ordered sections with one-line purpose each.
- `Open Questions`: unresolved issues that may change the storyline.
- `Boundaries`: what is out of scope, what assumptions are already fixed, and what the report will not claim.

## Artifact 2

```markdown
# Module Confirmation

## Selected Modules

## Out-of-Scope

## Owner Map

## Must-answer Questions
```

Field guidance:

- `Selected Modules`: the confirmed module list that will be drafted.
- `Out-of-Scope`: dropped sections, deferred topics, or questions intentionally excluded.
- `Owner Map`: one owner per module.
- `Must-answer Questions`: the key questions each module must answer before it can be accepted.

## Artifact 3

```markdown
# Module Contract

## Module

## Scope Boundaries

## Must-answer Questions

## Public Evidence Plan

## Known Evidence Limits

## Done Definition
```

Field guidance:

- `Module`: one module name only. Write one contract per module.
- `Scope Boundaries`: what the module covers, what it excludes, and what claims it must not make.
- `Must-answer Questions`: the smallest question set that must be answered before the module can pass review.
- `Public Evidence Plan`: the public sources or source types the Executor is expected to cover before drafting.
- `Known Evidence Limits`: what likely requires expert interviews, proprietary data, or other non-public inputs.
- `Done Definition`: what Evaluator should treat as enough for this module to be `ready`.

## Artifact 4

```markdown
# Evaluation Report

## Target

## Verdict

## Strengths

## Gaps

## Evidence Coverage

## Rewrite Brief
```

Field guidance:

- `Target`: the module contract or module draft being reviewed.
- `Verdict`: `ready` or `revise` only.
- `Strengths`: what already works.
- `Gaps`: what blocks acceptance.
- `Evidence Coverage`: whether accessible public sources were reasonably covered, what remains unavailable publicly, and whether those limits were disclosed correctly.
- `Rewrite Brief`: concrete rewrite actions. If the target is `ready`, write `- none`.

## Artifact 5

```markdown
# Final Delivery

## Executive Summary

## Final Report

## Acceptance Note

## Evidence Gap Register

## Nano Banana Prompts
```

Field guidance:

- `Executive Summary`: short management summary for fast reading.
- `Final Report`: the complete integrated research report body with all approved modules. Do not compress it into a short memo when a full report was requested.
- `Acceptance Note`: why the report is acceptable, what assumptions remain, and which evidence gaps likely require expert interviews or proprietary data.
- `Evidence Gap Register`: a consolidated list of unresolved material evidence gaps across modules. If no material gaps remain, write `- 无重大证据缺口`.
- `Nano Banana Prompts`: 1-3 prompts only, chosen from the finished report.

Use this structure for each evidence gap item:

```markdown
### Gap 1
- Gap:
- Why it matters:
- What is needed:
- Who can provide it:
- Impact on current report:
```

Use this structure for each Nano Banana prompt:

```markdown
### Prompt 1
- Section:
- Placement:
- Objective:
- Nano Banana Prompt:
```

Prefer sections such as executive summary, comparison, mechanism, risk, or scenario only after the report is complete.
