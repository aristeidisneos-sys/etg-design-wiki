# 09 · AI & skills governance

> **Goal:** Make it easy for anyone on the team to contribute skills, while keeping quality high, the library tidy, and agents safe in shared Figma files.
> **Level:** All · **Owners:** Design AI working group
> **Status:** <span class="status">Draft v0.1</span> Proposed defaults. To be validated with the working group and IT/security.

---

## 1. Principles

1. **Easy to contribute, hard to break things.** Checks happen where skills enter the library, not before people can try ideas.
2. **Every skill has an owner.** No owner means a candidate for retirement.
3. **Least access.** Agents start read-only. Edits happen on duplicates or in approved scopes.
4. **Humans stay accountable.** Whoever runs an agent owns the result.

---

## 2. Roles

The working group has 2–4 people.

| Role | Responsibilities |
|---|---|
| **Group lead** | Runs the monthly review, breaks ties, owns this policy |
| **Design system rep** | Approves anything touching components, tokens, variables or Code Connect |
| **Engineering rep** | Reviews anything touching code, repos or CI |
| **Contributors** (everyone) | Propose skills, use Experimental skills, give feedback, report incidents |

!!! note "Tie-break"
    If reviewers disagree, the group lead decides. Record the reasoning in the skill's changelog.

---

## 3. Skill lifecycle

| Tier | Meaning | Who can use it | Moves up when |
|---|---|---|---|
| **Experimental** | Someone's draft | Author, plus anyone who opts in | Author submits with the [template](registry/skill-submission-template.md) |
| **Team-approved** | Reviewed and listed in the library | Whole team | Reviewer signs off on the [checklist](#4-review-checklist) **and** one successful test on a practice file is linked |
| **Deprecated** | Superseded or unused | No one | Auto-flagged after **90 days** with no use or review; owner can renew |

```
Idea → Experimental → (review) → Team-approved → (90d inactive / replaced) → Deprecated → Archived
```

**Rules**
- Anyone can create an Experimental skill without asking.
- Experimental skills must not be used on shared production files.
- One reviewer approves (two for skills that change files at safety level 3 or 4).
- Changes to a Team-approved skill go back through review, with small fixes handled as patch updates (see versioning).

---

## 4. Review checklist

Copy into the submission. A skill passes when all boxes are ticked or marked N/A with a reason.

**Identity**
- [ ] Name follows `area-action` (e.g. `figma-tidy-page`)
- [ ] One-line purpose and clear "use when" triggers
- [ ] Named owner and backup owner
- [ ] Not a duplicate. Checked the library, merged if overlapping

**Quality**
- [ ] Follows the design system: no hardcoded values, no invented components
- [ ] Uses library components and variables, with references linked
- [ ] Output format is clear (plan, report, screen, list)
- [ ] Includes a **verification step** (screenshots, re-audit, side-by-side)

**Safety**
- [ ] Declares its [safety level](#5-agent-safety-rules-for-figma) (1–4)
- [ ] Changes follow plan → approve → apply → verify
- [ ] Respects the registry's "do not touch" list
- [ ] No deletes without an approved list
- [ ] No secrets, tokens, customer data or confidential links inside

**Evidence**
- [ ] Tested on a practice file; link or screenshots attached
- [ ] Failure cases and known limits documented

---

## 5. Agent safety rules for Figma

Every skill declares one level. A skill can't exceed the level it declares.

| Level | Allowed | Where | Approval |
|---|---|---|---|
| **1 · Read-only** | Audit, report, explore | Any file you can view | None |
| **2 · Duplicate-only** | Edits on a copied page | Any file you can edit | None, but never on the original |
| **3 · Scoped edit** | Edits in named pages/sections, with a change log | Files you own | Plan approved before applying |
| **4 · Destructive** | Delete, detach, bulk rename, overwrite | Only on an approved list | Explicit list approval, plus a duplicate backup |

**Rules that always apply**
- Never delete without an approved list.
- Never touch locked pages or the registry's "do not touch" list.
- Apply changes in small batches and stop on first error.
- Always produce a change log (what, how many, skipped and why).
- Prefer restoring from Figma version history over trying to "undo" with another agent run.

---

## 6. Keeping the library tidy

**One library, one source of truth.** The Skills library page is generated from the Drive `Skills/` folder. If it isn't listed there, it doesn't officially exist.

| Field | Purpose |
|---|---|
| Name | `area-action` |
| Description | One line |
| Tier | Experimental / Team-approved / Deprecated |
| Safety level | 1–4 |
| Owner / backup | Who to ask |
| Last reviewed | Drives the 90-day rule |
| Last used | Self-reported or from usage notes |

**Anti-sprawl habits**
- Search the library before creating anything.
- Prefer **improving** an existing skill over creating a near-duplicate.
- Merge overlapping skills during the monthly review.
- Archive, don't delete. Deprecated skills move to `Skills/_archive/`.

**Versioning**
- `MAJOR.MINOR.PATCH` in the skill's frontmatter.
- Patch = typo or wording. Minor = new capability. Major = changes behavior or safety level (needs full review).
- Keep a short changelog at the bottom of each skill.

---

## 7. Cadence

| When | What | Who | Time |
|---|---|---|---|
| **Continuous** | Submit, test, give feedback | Everyone | n/a |
| **Monthly** | Review submissions, promote, merge, deprecate | Working group | 30 min |
| **Quarterly** | Audit the library, review incidents, update this policy | Working group | 60 min |

**Simple signals to track** (keep it cheap): number of Team-approved skills in use, self-reported time saved per skill, incidents, and skills deprecated or merged.

---

## 8. Incidents

If an agent changes something it shouldn't:

1. **Stop** the run.
2. **Restore** from Figma version history (or the duplicate backup).
3. **Tell** the skill owner and the working group.
4. **Log** a short note: what happened, impact, root cause, fix.
5. **Update** the skill or rule so it can't happen the same way again.

!!! tip "Blameless"
    The goal is to improve the system. Reporting early should always be the safe choice.

---

## 9. Data handling

!!! warning "To validate with IT/security"
    There's no confirmed company policy yet. Until there is, apply these defaults.

- Don't put customer data, credentials, tokens, or unreleased confidential material into prompts or skills.
- Don't paste links to restricted files into shared skills; use the registry instead.
- Check which tools and connectors are approved for company data before using them.
- When in doubt, ask the working group.

---

## 10. Open decisions

| Decision | Proposed default | Owner | Status |
|---|---|---|---|
| Reviewers per Team-approved skill | 1 (2 at safety level 3–4) | Group lead | Open |
| Tie-break authority | Group lead | Working group | Open |
| Deprecation window | 90 days | Working group | Open |
| Usage tracking | Self-reported | Group lead | Open |
| Company AI/data policy alignment | Placeholder above | IT/security | Open |

---

### Changelog
| Date | Change | By |
|---|---|---|
| 2026-10-07 | Initial draft | |
