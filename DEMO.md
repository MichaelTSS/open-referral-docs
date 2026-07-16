# Démo / onboarding — édition de la doc (pour Amandine)

> ⚠️ Fichier **interne**, non publié sur le site (absent de `SUMMARY.md`).
>
> 🔐 **Note sécurité** : cette procédure utilise le compte GitHub **de Michel** (compte
> partagé). C'est un dépannage temporaire. À terme, mieux vaut qu'Amandine utilise **son
> propre compte** ajouté comme collaborateur (`gh repo add-collaborator MichaelTSS/open-referral-docs <user>`),
> pour la traçabilité et pour ne pas partager d'accès personnels.

## Comment ça marche (en une phrase)

La doc vit dans ce repo GitHub. GitBook y est branché en **Git Sync** : **chaque `git push`
sur `main` redéploie automatiquement** https://docs.openreferral.io. Pas d'AWS, pas de build
manuel — on édite du Markdown, on pousse, c'est en ligne.

## Prérequis

- macOS avec [Homebrew](https://brew.sh) installé.
- Git installé (`git --version`).

## Étape 1 — Installer GitHub CLI

```bash
brew install gh
```

## Étape 2 — Se connecter (compte de Michel)

Dans **le terminal d'Amandine** :

```bash
gh auth login
```

Répondre :

- **What account do you want to log into?** → `GitHub.com`
- **Preferred protocol?** → `HTTPS`
- **Authenticate Git with your GitHub credentials?** → `Yes`
- **How would you like to authenticate?** → `Login with a web browser`

`gh` affiche un **code à usage unique** puis ouvre le navigateur.

> 👉 C'est **Michel** qui saisit ses identifiants / valide la connexion dans le navigateur.
> Amandine ne tape jamais de mot de passe elle-même. Aucun identifiant n'est écrit ni stocké
> dans ce repo.

Vérifier :

```bash
gh auth status
```

## Étape 3 — Récupérer le repo

```bash
gh repo clone MichaelTSS/open-referral-docs
cd open-referral-docs
```

## Étape 4 — Éditer une page (exemple)

Les pages sont des fichiers `.md`. Exemple : modifier l'accueil.

```bash
# ouvrir README.md dans l'éditeur, faire une petite modif, sauvegarder
```

Structure utile :

| Fichier | Page sur le site |
| --- | --- |
| `README.md` | Accueil (`/`) |
| `getting-started.md` | `/getting-started` |
| `knowledge/README.md` | `/knowledge` |
| `ats-integrations/README.md` | `/ats-integrations` |
| `ai-assistant-integrations/claude.md` | `/ai-assistant-integrations/claude` |
| `SUMMARY.md` | Le sommaire / la navigation (ajouter ici toute nouvelle page) |

## Étape 5 — Publier

```bash
git add -A
git commit -m "Docs: <décrire la modif>"
git push origin main
```

## Étape 6 — Vérifier en ligne

Attendre ~1 min, puis ouvrir https://docs.openreferral.io et vérifier la modif.
GitBook resynchronise automatiquement après le push.

## Ajouter une nouvelle page

1. Créer le fichier `.md` (ex. `knowledge/best-practices.md`).
2. L'ajouter dans `SUMMARY.md` sous le bon groupe — **sinon elle n'apparaît pas** sur le site.
3. `commit` + `push`.
