# 2msloc.quest

Sito personale e blog costruito con [Hugo](https://gohugo.io/), deployato automaticamente su GitHub Pages.

## Setup iniziale

### Prerequisiti

- Git con SSH configurato
- [Hugo](https://gohugo.io/installation/) installato localmente (per preview)

### Creare il repository su GitHub

```bash
cd ~/git/2msloc.quest

git init
git add .
git commit -m "Initial commit"

git remote add origin git@github.com:2msloc/2msloc.quest.git
git branch -M main
git push -u origin main
```

### Abilitare GitHub Pages

1. Vai su **Settings > Pages** nel repository
2. In **Source** seleziona **GitHub Actions**
3. Il workflow `.github/workflows/hugo.yml` si occuperà del build e deploy automatico ad ogni push su `main`

### Configurare il dominio custom (opzionale)

Il file `static/CNAME` è già configurato con `2msloc.quest`. Per collegarlo:

1. Nel pannello DNS del tuo dominio, aggiungi un record:
   - **A** → `185.199.108.153` (e gli altri 3 IP di GitHub Pages)
   - oppure **CNAME** → `2msloc.github.io`
2. In **Settings > Pages** su GitHub, inserisci `2msloc.quest` come custom domain
3. Abilita **Enforce HTTPS**

## Uso quotidiano

### Scrivere un nuovo post

Crea un file Markdown in `content/blog/`:

```bash
hugo new content/blog/nome-del-post.md
```

Oppure crea il file a mano con questo formato:

```markdown
---
title: "Titolo del Post"
date: 2026-02-22
description: "Breve descrizione per SEO e anteprima."
---

Contenuto del post in Markdown.

## Sottotitolo

Testo, `codice inline`, ecc.
```

Il codice viene evidenziato automaticamente:

````markdown
```go
func main() {
    fmt.Println("Hello")
}
```
````

### Preview locale

```bash
hugo server -D
```

Il sito sarà disponibile su `http://localhost:1313/`. Le modifiche ai file vengono ricaricate in tempo reale.

### Pubblicare

```bash
git add content/blog/nome-del-post.md
git commit -m "Add: nome del post"
git push
```

Il push su `main` triggera il workflow GitHub Actions che builda e deploya automaticamente il sito.

## Struttura del progetto

```
.
├── hugo.toml              # Configurazione Hugo (metadata, parametri sito)
├── content/
│   └── blog/              # Post del blog (file .md)
├── layouts/
│   ├── index.html         # Template homepage
│   ├── 404.html           # Pagina 404
│   └── _default/
│       ├── baseof.html    # Template base (head, nav, footer, CSS)
│       ├── list.html      # Lista post
│       └── single.html    # Singolo post
├── static/
│   ├── CNAME              # Dominio custom
│   └── robots.txt         # SEO
└── .github/workflows/
    └── hugo.yml           # CI/CD GitHub Actions
```
