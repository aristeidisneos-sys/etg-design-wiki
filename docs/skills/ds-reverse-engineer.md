# DS-Reverse-Engineer

> **Goal:** Work out whether a code UI library has a good Figma kit, what a design library for it should contain, and what building or fixing one would cost.
> **Level:** Intermediate · **Tier:** Experimental · **Safety level:** 1 (read-only on Figma)
> **Status:** <span class="status">Draft v0.1</span> Library listing: [Skills library](../registry/skills-library.md)

It is a repeatable, evidence-based process delivered as a set of Claude skills. It works for any code UI library (Mantine, MUI, Chakra, shadcn/ui, Ant Design and others). [Mantine](ds-reverse-engineer-mantine-example.md) is the worked example.

!!! note "Current limit"
    Only a Mantine adapter ships today. For other libraries the skill creates an adapter from a template on the first run. This has not been tested yet.

---

## 1. Principles

1. **Read-only on Figma.** It never creates or edits anything in a Figma file.
2. **Every claim cites a source:** a URL, a file path or a node ID. Anything unchecked is marked UNVERIFIED.
3. **Each phase stops at a gate.** It gives a verdict and asks one question, then waits for you.
4. **Results are files**, so you can stop and resume later.

## 2. The four phases

| # | Phase | Question it answers | Skill | Output |
|---|---|---|---|---|
| 1 | **Discover** | Is there an official or community Figma kit, how current is it, and what is the license? | `reverse-ds-discover` | `discover.md` |
| 2 | **Extract** | What exactly is in the code library at the version we use? | `reverse-ds-extract` | `spec.json`, `spec-summary.md` |
| 3 | **Audit** | How close is an existing Figma file to that spec? | `reverse-ds-audit` | `audit.md`, `audit.json` |
| 4 | **Cost** | What would patching, rebuilding or a mix cost? | `reverse-ds-cost` | `cost.md` |

Run any phase on its own ("just discover Mantine"). Audit needs `spec.json` and a Figma file you own. Cost needs `spec.json`. The `ds-reverse-engineer` skill runs them in order.

**Flow:** discover (kits and version gap) → extract (tokens, components, version changes) → audit (compare a Figma file to the spec) → cost (patch, rebuild or hybrid).

### Phase 1 · Discover
Checks the library's docs, GitHub discussions and maintainer statements for an official kit, then finds community kits. Each kit is rated **Current**, **Usable base**, **Stale** or **Dead**, with its license and how many versions behind it is.

- Figma Community pages load empty over plain web requests, so the skill uses the browser, with your approval.
- "Last updated N years ago" is the evidence, not the kit's own description. A kit that is online is not dead.

### Phase 2 · Extract
Builds the spec from the code: raw source files first, then changelogs and migration guides, then per-component docs, then demos.

- Tokens are read by hand from source. The component inventory is built by parallel helpers that each write one JSON file.
- Anything introduced after your target version is kept but marked `inScope: false`.
- It reports what was inferred (variant lists, sizes), where the docs are newer than your target version, and how much helper output was spot-checked.

### Phase 3 · Audit
Compares a Figma file you own against the spec. For a Community kit, you open it with "Open in Figma" so it is copied to your drafts, then share the link. The skill never copies files for you.

- It compares tokens and scales, palettes, text and effect styles, light/dark parity, component coverage, variant axes, naming and variable binding.
- It gives a keep / patch / rebuild call per component group, and says what was read in detail versus inferred from page names.

### Phase 4 · Cost
Estimates person-days for one designer, as a manual range and a Claude-assisted range, for patching an existing kit, rebuilding from code, or a hybrid.

- The numbers come from a model, not from measured team speed. Give it your real velocity and it rescales.
- It lists risks (license attribution, inherited naming, keeping in sync with the library) and which decisions change the numbers.

## 3. Decisions it will ask you for

| Decision | Why it matters |
|---|---|
| Target library version | Sets what counts as in scope |
| Spacing and radius scale | The library's real scale or a kit's reinterpretation |
| Font, for libraries that use a system font | Figma needs one concrete font |
| Which kit, if any, to use as a base | Changes the cost |

## 4. Install and run

1. Get the skills from the Drive `Skills/` folder (link to be added).
2. **Claude Code:** copy the `skills/*` folders to `~/.claude/skills/` (or `.claude/skills/` in a project) and `commands/ds-reverse-engineer.md` to `~/.claude/commands/`. Restart, then run a command below.
3. **Claude Desktop:** install the skills as described in [Step 8 · Team skills](../00-start-here.md#step-8-team-skills). (verify on first run)

**Needs:** the Figma connector (audit), web search and fetch, and a browser for Figma Community pages (discover).

```
/ds-reverse-engineer <library> discover
/ds-reverse-engineer <library> extract --to <version>
/ds-reverse-engineer <library> audit --figma <your file link>
/ds-reverse-engineer <library> cost
```

Results are written to `design-reverse/<library>/` in your working folder. A rerun keeps the previous file as `.prev`.

## 5. Adding a library
Create `skills/reverse-ds-core/references/adapters/<library>.md` from `_template.md`: the library's sources, conventions, translation notes and known kits.

---

### Changelog
| Date | Change | By |
|---|---|---|
| 2026-10-09 | Initial page | |
