# ETG Design × AI Wiki

Minimal MkDocs Material wiki, auto-deployed to GitHub Pages.

## Run locally
```bash
python3 -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt
mkdocs serve        # http://127.0.0.1:8000
```

## Publish (one-time)
1. Create a GitHub repo and push this folder to `main`.
2. Repo → **Settings → Pages → Source: GitHub Actions**.
3. Set `site_url` (and optionally `repo_url`) in `mkdocs.yml`.
4. Push to `main`. The workflow builds with `--strict` and deploys. PRs are build-checked only.

## Theme
Edit the `--etg-*` tokens at the top of `docs/stylesheets/etg.css` with official brand values.

## With Claude Code
Open this folder and run `claude`. `CLAUDE.md` gives it the rules and page outlines, e.g.
*"Draft docs/01-prompting-and-context.md following CLAUDE.md."*
