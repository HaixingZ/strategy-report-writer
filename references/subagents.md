# Subagents

Use these roles to keep the workflow structured and auditable through real subagent execution without RIS runtime dependencies.

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

Use one domain-expert subagent per confirmed module.

Responsibilities:

- Own one module end-to-end.
- Research the module question set.
- State the module judgment first.
- List key findings and evidence gaps.
- Draft the module body.
- **If a `Source Pack` was supplied in the brief, read every entry in it before drafting. Prioritize those sources as the highest-authority evidence tier. Use them directly to support claims whenever they are relevant.**

Domain Expert must not:

- Rewrite other modules.
- Change the approved thesis.
- Pretend unsupported claims are verified.
- Contradict or silently ignore a user-supplied source. If a source conflicts with other evidence, flag the conflict explicitly as a `Source Conflict` note.

Recommended label when presenting module ownership in text:

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
- Approve a module that ignores a relevant user-supplied source without explanation.

Recommended label when presenting reviewer feedback in text:

```text
[Partner Reviewer]
```

## Execution mode

### Required subagent mode

Use this skill in real subagent mode by default.

- Spawn one expert per module.
- Keep the default cap at 4 experts.
- Feed every expert the same approved storyline, active style profile, and `Source Pack` (if one exists).
- Run partner review after each expert draft returns.
- Once this skill is invoked, do not ask the user to restate a preference for subagents.
- If subagent creation is blocked by environment or policy constraints, stop the workflow and report the blocker.
- Do not simulate a sequential fallback inside one agent.

## Module draft contract

Each expert draft should cover these four elements before review:

1. Module judgment
2. Key findings
3. Evidence gaps
4. Module draft body

Keep these inside the expert workstream. The public artifact headings still come from `output-contracts.md`.

## Citation format

When citing any data source, report, article, or public document in a module draft, always include the URL in Markdown link format:

```
数据来源：[来源名称](URL)
```

Examples:
- 数据来源：[中国汽车流通协会（CADA）](https://www.cada.org.cn)
- 数据来源：[CADA《2024年度中国汽车流通行业二手车经销商百强排行榜分析报告》](https://www.cada.org.cn/info/xxxx)

Rules:
- If the URL is known or searchable, include it.
- If the URL cannot be verified, note it as `（URL未确认）` after the link.
- Never cite a source by name alone. A bare name without a URL must not appear in a `数据来源` line.
- If a source has no publicly accessible URL (e.g., internal document or subscription-only), write `（无公开URL）` in place of the URL.
