# Open Referral — Documentation

Source of the documentation site published at **https://docs.openreferral.io**.

Built with [MkDocs Material](https://squidfunk.github.io/mkdocs-material/) and hosted on
**Cloudflare Pages**. Every push to `main` is built and deployed automatically.

## Editing

- Pages live in **`docs/`** (Markdown). The navigation is the `nav:` key in **`mkdocs.yml`**.
- Push to `main` → Cloudflare rebuilds and updates the live site in ~1–2 min.
- Full onboarding (setup, adding a page, local preview, syntax) is in **[DEMO.md](DEMO.md)**.

## Local preview

```bash
python3 -m venv .venv && ./.venv/bin/pip install -r requirements.txt
./.venv/bin/mkdocs serve      # http://127.0.0.1:8000
```

## Hosting

- **Repo → Cloudflare Pages** project `open-referral-docs` (Git integration, production branch `main`).
- Build: `pip install -r requirements.txt && mkdocs build`, output `site`, `PYTHON_VERSION=3.12`.
- Custom domain `docs.openreferral.io` — DNS is a CNAME in AWS Route 53 → `open-referral-docs.pages.dev`.
