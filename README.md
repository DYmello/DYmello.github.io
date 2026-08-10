# DYmello's Log

Source for [DYmello.github.io](https://dymello.github.io/), an AI and PhD research blog built with Hugo and PaperMod and deployed with GitHub Pages.

## Technology stack

- [Hugo](https://gohugo.io/) 0.164.0 or newer compatible version
- [PaperMod](https://github.com/adityatelange/hugo-PaperMod) as a Git submodule
- GitHub Actions and GitHub Pages

## Repository structure

- `hugo.yaml` — site configuration and navigation
- `content/` — posts and site pages
- `assets/` — processed site assets and custom CSS
- `layouts/` — local PaperMod extension points
- `static/` — files copied directly into the built site
- `themes/PaperMod/` — upstream theme submodule
- `.github/workflows/hugo.yml` — production deployment workflow

## Prerequisites

Install the Hugo extended edition. The deployment workflow uses Hugo 0.164.0.

Clone the repository and its theme:

```bash
git clone --recurse-submodules \
  https://github.com/DYmello/DYmello.github.io.git
```

For an existing clone:

```bash
git submodule update --init --recursive
```

## Local development

```bash
hugo server -D
```

The local site is available at `http://localhost:1313/`.

## Create a new post

Posts use leaf bundles so figures and other article-specific resources can live beside the Markdown file:

```bash
hugo new content posts/my-new-post/index.md
```

New posts are drafts by default. Set `draft: false` only when an article is ready to publish.

## Production build

```bash
hugo --gc --minify
```

The generated `public/` directory is intentionally ignored and must not be committed.

## Deployment

A push to `main` triggers `.github/workflows/hugo.yml`. GitHub Actions checks out submodules, builds the production site, uploads `public/` as a Pages artifact, and deploys it to GitHub Pages. The workflow can also be run manually.

## Update PaperMod

Review upstream changes before committing the updated submodule reference:

```bash
git submodule update --remote --merge
hugo --gc --minify
```

Do not directly modify `themes/PaperMod`. Keep site-specific changes in root-level configuration, content, assets, and layouts.
