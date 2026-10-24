# niklastypes

Hugo site for [niklastypes.xyz](https://niklastypes.xyz) (Blowfish theme, git submodule), deployed to GitHub Pages by `.github/workflows/` on every push to `main`. The repo doubles as the GitHub profile repo.

- **Root `README.md` is the GitHub profile card**, not project docs. It is also rendered on the About page via `layouts/shortcodes/profile.html`; keep it valid on both GitHub and the site.
- **Project docs live in [docs/](./docs/README.md)**: how to develop the current site, plus the brainstorm, design spec, roadmap, and writing style for the planned Astro migration.
- Run locally with `hugo server` (restart it after editing the root README).
- Conventional commits.
