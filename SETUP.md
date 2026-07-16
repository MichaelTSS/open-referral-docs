# Repo setup (not published in the docs site)

This repository is a **GitBook Git Sync** source. GitBook builds the site from
`SUMMARY.md` (table of contents) and the Markdown pages; `.gitbook.yaml` points to them.

## Publish on docs.openreferral.io

1. Push this repo to GitHub (or GitLab).
2. In GitBook, create a Space, then **Configure Git Sync** and select this repo/branch.
   GitBook imports the structure from `SUMMARY.md` automatically.
3. In the Space: **Publish → Custom domain → `docs.openreferral.io`**.
4. Add the DNS record GitBook gives you (a `CNAME` on `docs` pointing to GitBook),
   then verify the domain in GitBook.

## Editing

* Add a page: create the `.md` file, then add it to `SUMMARY.md` under the right group.
* Screenshots go in `.gitbook/assets/` and are referenced from pages.
* Files not listed in `SUMMARY.md` (like this one) are ignored by the published site.
