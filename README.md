# strategy-report-writer

`strategy-report-writer` is a Codex skill for writing strategy reports with a gated workflow:

- confirm storyline first
- confirm modules second
- draft with role separation
- review against a configurable writing style
- finalize only after module review passes

## Contents

- `SKILL.md`: main workflow and guardrails
- `references/workflow.md`: sequence and gate rules
- `references/output-contracts.md`: public artifact formats
- `references/subagents.md`: role definitions
- `references/style-system.md`: style selection and override rules
- `references/style-profile.md`: generic fallback voice
- `references/style-presets/analytical-operator.md`: default house style preset
- `agents/openai.yaml`: UI metadata

## Install

Copy this repository into `$CODEX_HOME/skills/strategy-report-writer`

Example:

```bash
cp -R strategy-report-writer "$CODEX_HOME/skills/"
```

## Style behavior

By default, the skill uses the house style preset in `references/style-presets/analytical-operator.md`

If the user gives another sample, tone, or explicit format requirement in the current turn, the skill merges those instructions on top of the default preset

If no preset fits, the skill can fall back to `references/style-profile.md`

## Updating the default style

1. Add or edit a preset under `references/style-presets/`
2. Update the default preset rule in `references/style-system.md`
3. Keep `SKILL.md` focused on workflow, not style specifics
