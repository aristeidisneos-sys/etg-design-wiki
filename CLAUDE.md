# ETG Design × AI Wiki: context for Claude Code

Static wiki built with MkDocs Material, deployed to GitHub Pages by `.github/workflows/deploy.yml`.

## Commands
- Preview: `pip install -r requirements.txt && mkdocs serve`
- Check: `mkdocs build --strict` (must pass before commit)

## Rules
- Content lives in `docs/*.md`. Add new pages to `nav:` in `mkdocs.yml`.
- Theme tokens live only in `docs/stylesheets/etg.css` (`--etg-*`). Do not hardcode colors elsewhere.
- Keep it minimal: no extra plugins, no custom JS, no images unless asked.
- Page style: short, scannable, tables and copy-paste prompts, a "Level" line at the top.
- Don't use official logos or brand assets unless the user provides them.

## Page outlines (for stubs marked Planned)
- 00 Start here: mental model, tool choice (Figma Agents / Figma MCP / Claude Code / chat), 15-min first win.
- 01 Prompting & context: brief anatomy (goal, audience, constraints, references, definition of done), examples vs rules, small steps, plan-before-act, before/after prompt bank.
- 02 Design system hygiene: variables, layer naming, component descriptions, auto-layout, readiness checklist.
- 03 Code Connect: purpose, mapping, maintenance, verification.
- 04 Brief to Figma: use library components, build section by section, review checklist.
- 05 Components from a draft: inventory existing base → gap analysis → approval gate → build (variants, tokens, docs, states matrix, Code Connect stub).
- 07 Pitfalls & verification: failure modes with fixes; screenshot comparison; token audit.
