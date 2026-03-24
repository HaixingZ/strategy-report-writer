# Output Contracts

Use these exact top-level headings for the 4 public artifacts. Keep the field order stable.

## Global prohibitions

- Do not write the full report before `Storyline Packet` is approved.
- Do not start expert work before `Module Confirmation` is approved.
- Do not include Nano Banana prompts outside `Final Delivery`.
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
# Partner Review

## Verdict

## Strengths

## Gaps

## Rewrite Brief
```

Field guidance:

- `Verdict`: `ready` or `revise` only. For the first review of an initial draft, it must be `revise`.
- `Strengths`: what already works.
- `Gaps`: what blocks acceptance. On the first review, include at least one concrete revision point.
- `Rewrite Brief`: concrete rewrite actions. On the first review, do not write `- none`.

## Artifact 4

```markdown
# Final Delivery

## Executive Summary

## Final Report

## Partner Acceptance Note

## Evidence Gap Register

## Nano Banana Prompts
```

Field guidance:

- `Executive Summary`: short management summary for fast reading.
- `Final Report`: the integrated report body with all approved modules.
- `Partner Acceptance Note`: why the report is acceptable, what assumptions remain, and where caution is still needed.
- `Evidence Gap Register`: a consolidated list of all material evidence gaps identified across modules, formatted for analyst use when scoping expert interviews. Use the standard gap template for each item:

```markdown
### Gap N
- Gap:
- Why it matters:
- What is needed:
- Who can provide it:
- Impact on current report:
```

  Include only gaps that materially limit confidence in the report's conclusions. Omit gaps already resolved during the module phase. Each "Who can provide it" entry should name the type of expert, function, or data source an analyst would realistically approach (e.g., 一线销售负责人、产品运营、行业分析师、内部财务数据). If no material gaps remain, write `- 无重大证据缺口`.

- `Nano Banana Prompts`: 1-3 prompts only, chosen from the finished report.

Use this structure for each Nano Banana prompt:

```markdown
### Prompt 1
- Section:
- Placement:
- Objective:
- Nano Banana Prompt:
```

Prefer sections such as executive summary, comparison, mechanism, risk, or scenario only after the report is complete.
