# 06 · Tidy Up: agent-assisted file upkeep in Figma

> **Goal:** Spend less time on file maintenance. Give the agent a reference (a template page or a convention) and let it do the repetitive alignment work, while you review the result.
> **Level:** Beginner → Intermediate
> **Tools:** Figma MCP (`use_figma`, `get_screenshot`, `get_metadata`, `search_design_system`) via Claude Code, Cowork, or Figma Agents.

---

## 1. How it works

The agent is good at repetitive, rule-based changes. It is bad at guessing what "clean" means to you. So we give it:

1. **A source of truth:** a template page or a written convention (the *Page Registry*, section 3).
2. **A scoped task:** a recipe from section 4.
3. **A safe process:** audit → report → approve → apply → verify (section 2).

If the agent has no reference, it will invent one. Always point it at the registry or a node link.

---

## 2. The golden process (always follow this)

| Step | What the agent does | Your role |
|---|---|---|
| **1. Scope** | Confirms the file, page(s), and recipe. Restates the task in one sentence. | Correct it if wrong |
| **2. Audit (read-only)** | Reads the target and the template. Lists every deviation. **Changes nothing.** | Skim the report |
| **3. Report** | Groups findings: *safe to auto-fix* / *needs your decision* / *leave alone*. Gives counts. | Approve, edit, or reject groups |
| **4. Apply in batches** | Changes one section or page at a time, not the whole file at once. | Spot-check the first batch |
| **5. Verify** | Takes before/after screenshots, re-runs the audit, confirms 0 remaining deviations in scope. | Final look |
| **6. Log** | Writes a short change log (what changed, how many nodes, what was skipped and why). | File it on the changelog page |

### Hard rules
- **Never delete** anything without presenting a list and getting explicit approval.
- **Never touch** pages or frames marked `🔒` (locked) or named in the "Do not touch" list.
- **Risky or wide changes:** work on a duplicate page (`<name> – tidy draft`) first.
- **Don't invent.** If something doesn't match any template or convention, flag it. Don't fix it creatively.
- **Prefer binding to variables and swapping to library components** over recreating things by hand.
- If a batch fails or looks wrong, **stop and report.** Don't push on.

---

## 3. The Page Registry

The one thing the agent can't infer. Keep this table current. Anything listed here can be referenced by name in a prompt ("use the *Component Doc* template").

> **Maintenance:** one owner, reviewed monthly. Use stable Figma links (node IDs) and don't point at pages that get renamed.

| Template name | Figma link / node ID | Purpose | Use when | Notes |
|---|---|---|---|---|
| **Cover** | `<link>` | File cover page: title, status, owner | New file, or cover is outdated | Status badges are components |
| **Component Doc** | `<link>` | Standard layout for documenting a component | Documenting or refreshing a component page | Includes anatomy, variants, states, usage |
| **Handoff** | `<link>` | Dev handoff page structure | Before design review → dev | Sections: flows, specs, edge cases |
| **Flow Overview** | `<link>` | Layout for user-flow pages | Presenting end-to-end journeys | |
| **Changelog** | `<link>` | Running log of changes | After any tidy-up or release | Append, never overwrite |
| **Archive** | `<link>` | Where old frames go | Retiring work | Move, don't delete |

**Do not touch:** `<list pages, frames, or sections that are locked or owned by others>`

### Conventions (written rules)

Fill these in. The agent will enforce them. Examples:

- **Page names:** `Section / Name` (e.g. `Components / Button`)
- **Frame names:** `Platform – Screen name – State` (e.g. `Web – Checkout – Error`)
- **Layer names:** no `Frame 123` / `Group 4`. Describe the role (`Header`, `Price row`).
- **Status badges:** `Draft`, `In review`, `Ready`, `Deprecated`
- **Sections:** one per flow or feature. Order top → bottom: Overview, Flows, Details, Archive.
- **Colors / type / spacing:** must be bound to variables or styles, with no raw hex values.
- **Instances:** must be linked to the library, with no detached copies unless marked `intentional`.

---

## 4. Recipes

Each recipe is a ready prompt. Replace `<…>` and run. Every one follows the golden process above.

### 4.1 Align a page to a template
```
Use the "<template name>" template from the Page Registry as the reference.
Target: <page or frame link>.
Audit the target against the template (structure, section order, headings,
spacing, status badge, naming). Report the deviations grouped as
safe-to-fix / needs-decision / leave-alone. Don't change anything yet.
```

### 4.2 Rename layers and frames to convention
```
Audit <page link> for layer and frame names that break the naming
conventions in the Page Registry (default names like "Frame 123", "Group 4",
inconsistent case). Propose a rename list as a table: current → proposed.
Wait for my approval before renaming.
```

### 4.3 Replace hardcoded values with variables
```
In <page link>, find fills, strokes, text styles, spacing, and radii that are
hardcoded (not bound to a variable or style). For each, find the closest
matching variable in our design system. Show exact matches (auto-fixable)
separately from near matches (needs my decision). Apply exact matches
only after I approve.
```

### 4.4 Detached instances → library components
```
Find frames in <page link> that look like library components but are
detached or hand-built. Use search_design_system to find the matching
component. List them with a screenshot of each, and propose swaps.
Don't swap anything until I approve. Preserve overrides (text, visibility).
```

### 4.5 Refresh cover and status
```
Update the Cover page using the "Cover" template: set title, owner (<name>),
status (<status>), and date (<date>). Keep all other content untouched.
```

### 4.6 Archive stale work
```
Find frames on <page link> not modified since <date> or marked "Old"/"WIP".
List them. After I approve, move (don't delete) them to the Archive
page under a section named "<YYYY-MM> archive".
```

### 4.7 Full pre-handoff sweep (combines 4.1–4.4)
```
Run a pre-handoff tidy-up on <file link>. Do an audit-only pass first,
covering: template alignment, naming, hardcoded values, detached
instances. Give me one consolidated report with counts per category and a
suggested order of fixes. Do not change anything.
```

---

## 5. Reading the audit report: what good looks like

A useful report is **specific and countable**:

```
Audit: "Checkout" page vs "Flow Overview" template
- Auto-fixable (23): 14 default layer names, 6 raw hex fills with exact variable matches, 3 text styles
- Needs decision (5): 3 detached buttons (screenshots attached), 2 frames with no matching template section
- Leave alone (2): locked frames "Legal copy v2", "Partner banner"
```

**Push back if the report is vague** ("some issues found") or has no counts, no node references, or no screenshots for judgment calls.

---

## 6. When to run it

- **Before handoff or design review**: run 4.7, fix, then share.
- **End of sprint**: run 4.6 (archive) and 4.5 (cover/status).
- **Onboarding an old file to the system**: run 4.1 → 4.3 → 4.4 in that order.
- **Weekly (optional)**: audit-only on active files, which makes a good scheduled task.

---

## 7. Common pitfalls

| Problem | Why it happens | Fix |
|---|---|---|
| Agent "improves" things you didn't ask about | Scope was vague | Name the page, the recipe, and say "change nothing outside this scope" |
| Wrong template used | Several look similar | Reference the template by registry name and link |
| Renames break handoff links or Code Connect | Mappings rely on names | Exclude component names from renames; check the Code Connect mapping first |
| Large batch partially fails | Too much at once | Batch per section; ask the agent to stop on first error |
| Near-match variable picked wrongly | Closest color ≠ intended token | Only auto-apply **exact** matches |
| Agent says "done" without proof | No verification step | Always require before/after screenshots and a re-audit with 0 remaining deviations |

---

## 8. Verify (copy to the end of any tidy-up prompt)

```
When finished: (1) re-run the audit on the same scope and show remaining
deviations (should be 0, or explain each), (2) take before/after screenshots
of the 3 most-changed areas, (3) write a change log: what changed, how many
nodes, what you skipped and why.
```

---

## 9. Setup checklist (do once)

- [ ] Fill in the Page Registry (section 3) with real links
- [ ] Write down your naming conventions
- [ ] List "Do not touch" areas
- [ ] Pick a **test file** and a **duplicate page** to try recipes on first
- [ ] Decide who owns the registry
- [ ] (Optional) Turn the registry plus golden process into a shared Claude **skill** so everyone gets the same behavior

---

*Version 0.1 · Draft for testing. Add what you learn to the changelog below.*

### Changelog
| Date | Change | By |
|---|---|---|
| 2026-10-07 | Initial draft | |
