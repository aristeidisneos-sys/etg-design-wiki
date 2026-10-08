# ETG Design × AI Wiki: context for Claude Code

Static wiki built with MkDocs Material, deployed to GitHub Pages by `.github/workflows/deploy.yml`.

## Commands
- Preview: `pip install -r requirements.txt && mkdocs serve`
- Check: `mkdocs build --strict` (must pass before commit)

## Rules
- Content lives in `docs/*.md`. Add new pages to `nav:` in `mkdocs.yml`.
- Theme tokens live only in `docs/stylesheets/etg.css` (`--etg-*`). Do not hardcode colors elsewhere.
- Keep it minimal: no extra plugins, no custom JS, no images unless asked. Exception: `docs/assets/screenshots/<connector>/` holds real screenshots added by a human. Markdown extensions `attr_list`/`md_in_html` are on only for the home page layout.
- Page style: short, scannable, tables and copy-paste prompts, a "Level" line at the top.
- Don't use official logos or brand assets unless the user provides them.

## Screenshots
- Pages use a visible placeholder (`!!! note "Screenshot needed"` with the target path `assets/screenshots/<connector>/<NN>-<name>.png` and what to capture).
- Never replace a placeholder with a fabricated, generated or mocked-up image. Only swap it when a human supplies the real screenshot.

## Content rules for 00 · Start here
- Don't invent UI labels or menu paths. If the exact wording is unverified, write the step generically and append `(verify on first run)`.
- Slack is read-only everywhere (set by IT Ops). Gmail and Calendar steps warn against sending or sharing.
- No Slack IDs or deep links, and no company or customer data in examples. Verification prompts ask for counts, not subjects, titles or message content.

## Governance (09)
- `docs/09-governance.md` is the policy: skill tiers (Experimental → Team-approved → Deprecated), review checklist, safety levels 1–4, incidents, data handling.
- The skills library lives in Google Drive (`Skills/`). Don't copy policy text into other pages; link to 09.
- New skills are submitted with `docs/registry/skill-submission-template.md`.

## Page outlines (for stubs marked Planned)
- 00 Start here: connect and set up. Claude Desktop, Figma, Drive, Atlassian, Slack (read-only), Gmail, Calendar, team skills; verification prompt; troubleshooting. Written: Draft v0.1.
- 01 How agents work: mental model, tool choice (Figma Agents / Figma MCP / Claude Code / chat), first win. Written.
- 02 Prompting & context: brief anatomy (goal, audience, constraints, references, definition of done), examples vs rules, small steps, plan-before-act, before/after prompt bank.
- 03 Design system hygiene: variables, layer naming, component descriptions, auto-layout, readiness checklist.
- 04 Code Connect: purpose, mapping, maintenance, verification.
- 05 Brief to Figma: use library components, build section by section, review checklist.
- 06 Components from a draft: inventory existing base → gap analysis → approval gate → build (variants, tokens, docs, states matrix, Code Connect stub).
- 07 Tidy up: written.
- 08 Pitfalls & verification: failure modes with fixes; screenshot comparison; token audit.
- 09 AI & skills governance: written (Draft v0.1).
