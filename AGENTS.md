# Repository purpose

This repository contains the source for DYmello.github.io, a Hugo + PaperMod research blog deployed through GitHub Pages.

# Architecture

- `hugo.yaml`: website configuration
- `content/`: authored Markdown content
- `assets/`: site-owned processed assets and custom CSS
- `layouts/`: local Hugo/PaperMod template overrides
- `static/`: static files
- `themes/PaperMod/`: upstream Git submodule
- `.github/workflows/hugo.yml`: GitHub Pages deployment

# Hard rules

- Never directly edit `themes/PaperMod/`.
- Never commit `public/`.
- Use local `layouts/` and `assets/` overrides for customization.
- Keep PaperMod as a Git submodule.
- Keep root site configuration in `hugo.yaml`.
- Avoid deprecated Hugo configuration.
- Do not fabricate biography or publication information.

# Required verification

Before completing changes, run:

```bash
git diff --check
git submodule status
hugo --gc --minify
```

When applicable, also verify the local development server.
