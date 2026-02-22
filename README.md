# 2msloc.quest

Personal site. Hugo, no JS, no themes, no dependencies.

Deployed via GitHub Actions to GitHub Pages.

## Usage

    hugo server -D        # preview at localhost:1313
    hugo new content/blog/post-name.md

## Deploy

    git add .
    git commit -m "msg"
    git push              # triggers build + deploy

## Structure

    hugo.toml             # site config
    content/blog/         # posts (.md)
    layouts/              # HTML templates
    static/               # CNAME, robots.txt
    .github/workflows/    # CI/CD
