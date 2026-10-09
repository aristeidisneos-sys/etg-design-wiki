# Skills library

The listing of skills in the team library. The skill files themselves live in the Google Drive `Skills/` folder, which is the source of truth: if a skill isn't in Drive, it doesn't officially exist. See [09 · AI & skills governance](../09-governance.md) for tiers, safety levels and the review process, and the [submission template](skill-submission-template.md) to add a skill.

---

## Library

| Name | Description | Tier | Safety level | Owner / backup | Last reviewed | Last used |
|---|---|---|---|---|---|---|
| `ds-reverse-engineer` | Runs the four phases below in order, pausing at a gate after each. Start here. See [DS-Reverse-Engineer](../skills/ds-reverse-engineer.md) | Experimental | 1 · Read-only | TBD | Not yet | 2026-10-08 |
| `reverse-ds-discover` | Phase 1: finds Figma kits for a code UI library, how current they are, and the license | Experimental | 1 · Read-only | TBD | Not yet | 2026-10-08 |
| `reverse-ds-extract` | Phase 2: builds a machine-readable spec of the library for a target version | Experimental | 1 · Read-only | TBD | Not yet | 2026-10-08 |
| `reverse-ds-audit` | Phase 3: compares an existing Figma file against the spec | Experimental | 1 · Read-only | TBD | Not yet | 2026-10-08 |
| `reverse-ds-cost` | Phase 4: estimates effort to patch, rebuild or mix | Experimental | 1 · Read-only | TBD | Not yet | 2026-10-08 |
| `reverse-ds-core` | Shared rules, schema and library adapters used by the five above. Not run directly | Experimental | 1 · Read-only | TBD | Not yet | 2026-10-08 |

Source files: Drive `Skills/` folder (link to be added).

## Open items for review

- **Owner and backup** are not assigned yet for any of these skills.
- **No version** is recorded in the skill files yet (the policy asks for `MAJOR.MINOR.PATCH` and a changelog).
- **The safety level** is documented here but not yet declared inside the skill files.
- **Library coverage:** only a Mantine adapter ships. Other libraries need an adapter created first.

---

### Changelog
| Date | Change | By |
|---|---|---|
| 2026-10-09 | Added the DS-Reverse-Engineer skill set (Experimental) | |
