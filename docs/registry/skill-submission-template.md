# Skill submission template

Copy this page into your submission (Drive `Skills/` folder) and fill it in. A skill moves from **Experimental** to **Team-approved** when every box is ticked or marked N/A with a reason. See [AI & skills governance](../09-governance.md) for the rules behind each item.

---

## Skill details

| Field | Your answer |
|---|---|
| Name | `area-action` (e.g. `figma-tidy-page`) |
| Description | One line |
| Use when | Triggers: what situation should call this skill |
| Safety level | 1, 2, 3 or 4 (see [safety rules](../09-governance.md#5-agent-safety-rules-for-figma)) |
| Owner / backup owner | Names |
| Version | `0.1.0` |
| Practice file | Link to the Figma file you tested on |

## Review checklist

**Identity**
- [ ] Name follows `area-action`
- [ ] One-line purpose and clear "use when" triggers
- [ ] Named owner and backup owner
- [ ] Not a duplicate. Checked the library, merged if overlapping

**Quality**
- [ ] Follows the design system: no hardcoded values, no invented components
- [ ] Uses library components and variables, with references linked
- [ ] Output format is clear (plan, report, screen, list)
- [ ] Includes a **verification step** (screenshots, re-audit, side-by-side)

**Safety**
- [ ] Declares its safety level (1–4)
- [ ] Changes follow plan → approve → apply → verify
- [ ] Respects the registry's "do not touch" list
- [ ] No deletes without an approved list
- [ ] No secrets, tokens, customer data or confidential links inside

**Evidence**
- [ ] Tested on a practice file; link or screenshots attached
- [ ] Failure cases and known limits documented

## Reviewer sign-off

| Reviewer | Role | Decision | Date |
|---|---|---|---|
| | | Approve / Changes needed | |

One reviewer approves. Skills at safety level 3 or 4 need two.

## Changelog

| Version | Date | Change |
|---|---|---|
| 0.1.0 | | Initial submission |
