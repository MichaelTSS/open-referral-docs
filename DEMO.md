# Onboarding — éditer la doc (pour Amandine)

> Fichier **interne**, non publié sur le site (le site est généré depuis `docs/`).

## Comment ça marche (en une phrase)

La doc vit dans ce repo GitHub, générée par **MkDocs Material** et hébergée sur
**Cloudflare Pages** : **chaque `git push` sur `main` redéploie automatiquement**
https://docs.openreferral.io. On édite du Markdown dans `docs/`, on pousse, c'est en ligne.

---

## Setup d'Amandine (GitHub `Lmenkikine`, déjà accès au repo)

Amandine utilise **son propre compte GitHub** — pas de compte partagé.

```bash
# 1. Installer GitHub CLI (macOS)
brew install gh

# 2. Se connecter à SON compte
gh auth login          # GitHub.com → HTTPS → Yes → Login with a web browser

# 3. Vérifier
gh auth status         # doit afficher "Logged in as Lmenkikine"

# 4. Cloner le repo
gh repo clone MichaelTSS/open-referral-docs
cd open-referral-docs
```

Prérequis : macOS avec [Homebrew](https://brew.sh) et `git`.

---

## Éditer et publier

```bash
# éditer un fichier dans docs/ (voir table ci-dessous), puis :
git add -A
git commit -m "docs: <décrire la modif>"
git push origin main
```

Attendre ~1-2 min → la modif est en ligne sur https://docs.openreferral.io
(Cloudflare rebuild automatiquement à chaque push).

### Où sont les pages

| Fichier | Page sur le site |
| --- | --- |
| `docs/index.md` | Accueil (`/`) |
| `docs/getting-started.md` | `/getting-started` |
| `docs/knowledge/index.md` | `/knowledge` |
| `docs/ats-integrations/index.md` | `/ats-integrations` |
| `docs/ai-assistant-integrations/claude.md` | `/ai-assistant-integrations/claude` |
| `mkdocs.yml` (clé `nav`) | La navigation (ajouter ici toute nouvelle page) |

### Ajouter une nouvelle page

1. Créer le fichier, ex. `docs/knowledge/best-practices.md`.
2. L'ajouter sous `nav:` dans `mkdocs.yml` — **sinon elle n'apparaît pas** dans le menu.
3. `commit` + `push`.

### Aperçu local (optionnel)

```bash
python3 -m venv .venv && ./.venv/bin/pip install -r requirements.txt
./.venv/bin/mkdocs serve      # http://127.0.0.1:8000
```

### Syntaxe utile (MkDocs Material)

Encadrés (admonitions) :

```markdown
!!! info

    Ceci est une note d'information.
```

Types : `note`, `info`, `tip`, `success`, `warning`, `danger`.
