# Style System

Use this file to choose and merge prose styles without hard-coding a single house voice into the whole skill.

## Style priority

Apply style constraints in this order:

1. Accuracy, evidence quality, and explicit boundaries
2. Explicit style instructions in the current user request
3. User-supplied sample text or formatting rules
4. Default preset
5. Fallback profile in [style-profile.md](style-profile.md)

If two style rules conflict, keep the higher-priority rule and drop the lower one.

## Default preset

Unless the user asks for another style in the current turn, load [style-presets/analytical-operator.md](style-presets/analytical-operator.md) as the default preset.

Switch away from the default preset only when one of these is true:

- The user explicitly asks for another tone, audience voice, or format
- The user provides a new writing sample and asks you to imitate that sample
- The user names another preset that exists in `references/style-presets/`

## Merge method

When the user gives only partial style constraints, merge them onto the default preset instead of replacing the whole preset.

Typical override dimensions:

- Title shape and heading density
- Paragraph length
- List density and whether to prefer bullets or prose
- Table usage
- Tone and terminology
- Allowed or banned sentence patterns
- Punctuation quirks

Only change the dimensions the user actually touched.

## Swap-friendly design

This skill is intentionally modular:

- Keep the workflow in `SKILL.md`
- Keep the default house voice in [style-presets/analytical-operator.md](style-presets/analytical-operator.md)
- Keep the generic fallback voice in [style-profile.md](style-profile.md)
- Keep house or audience-specific voices in `references/style-presets/`

To add or replace a style later, create or edit a preset file in `references/style-presets/` and change only the default preset rule here. Do not rewrite the whole workflow unless the reporting process itself changes.

## Review checklist

- Did you apply the right preset for this user and this deliverable
- Did you preserve any explicit format constraints from the current turn
- Did you avoid leaking house-style quirks into outputs that asked for a different tone
- Did you keep unsupported claims marked as `Assumption` or `Evidence Gap`
