# Worked example: Mantine

> **Goal:** See what a full [DS-Reverse-Engineer](ds-reverse-engineer.md) run produces.
> **Level:** Intermediate · **Run date:** 2026-10-08 · **Target version:** 9.5.0

Mantine is a public React UI library. This run used all of phases 1 to 3.

## Result in one paragraph
There is no official Mantine Figma kit. Five community kits exist and none is current. The best candidates are two version 7 kits, while the library is at 9.7. Neither is a good base: one covers about two-thirds of the components, the other about a fifth. The recommendation is to rebuild the tokens from code, use the most complete kit's structure as a reference, and borrow the other's token layering.

## Phase 1 · Discover
- **Official:** none. The docs and the maintainer both say there are no official Figma files.
- **Community kits:** five, all under the CC BY 4.0 license (use with attribution), all two or more major versions behind.
- **Version gap:** newest kit content is v7. Mantine is at v9.7, so two majors (v8 and v9) are missing.

## Phase 2 · Extract
- **Components:** 169 in total, 159 in scope for 9.5.0, of which 143 have visual output. The rest are behavior-only.
- **Version changes** from v7: 218 records, 188 in scope.
- **Largest visual changes:** default radius moved from 4px to 8px, "light" variants became solid colors, the medium weight became 600, inputs gained success and loading states, and about 25 components are new.
- **Open decision:** the font. Mantine's default is a system font and Figma needs a concrete one.

## Phase 3 · Audit
| | Components covered (of 143) | Strengths | Weaknesses |
|---|---|---|---|
| Kit A (most complete) | 91 (64%) | Sizes, colors and 13 palettes | Different spacing scale, different font, transparent light variants |
| Kit B (leaner) | 31 (22%) | Component-level tokens layered over primitives, with light and dark | Only 3 color families, no size options |

Coverage for Kit A was counted from page names, not verified variant by variant. This is the kind of caveat the skill always states.

## Decisions and recommendation
- **Decided:** use Mantine's real spacing and radius scale; target 9.5.0.
- **Recommendation (hybrid):** neither kit as a base. Rebuild the tokens from the spec, use Kit A's component anatomy as a reference, and borrow Kit B's token layering.

---

### Changelog
| Date | Change | By |
|---|---|---|
| 2026-10-09 | Initial page | |
