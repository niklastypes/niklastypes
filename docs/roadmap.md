# Roadmap

> Migration from Hugo + Blowfish to Astro 6 with a custom theme. Deployed to the `*.github.io` preview URL from the very first slice; DNS cutover happens as soon as **parity** is reached, and everything after that ships incrementally on the live site. (An earlier version of this plan put deploy + DNS switch at the end of Bicycle: a big-bang cutover after an invisible rebuild. That's the waterfall pattern the rest of the galaxy rejects.)

## Parity Checklist (the DNS cutover gate)

- [ ] Existing posts migrated; every old Hugo URL preserved or redirected
- [ ] Giscus attached with unchanged pathname mapping, verified against the existing threads (a changed path silently orphans the comments)
- [ ] RSS feed reachable at the legacy-compatible path (existing subscribers survive)
- [ ] About page live (bio + hobby badges minimum)
- [ ] 404 page, canonical URLs, sitemap

## Momo's Diary (independent of the migration)

Momo's diary entries arrive from the Momo repo: she writes each one in her own platform-neutral format (Markdown plus frontmatter she defines and versions), it's reviewed and merged as her PR there, and her GitHub App (momo[bot]) commits it into `import/momo-diary/` here. Her first entries come at her Skateboard stage, on whatever the site is then.

- Slice: importer on Hugo: a content adapter renders `import/momo-diary/` as posts under her existing author entry, with CI validating her format (schema, size and rate limits)
- Slice: the same folder as an Astro content collection; part of the parity checklist once she has published

## Earliest Testable

### Bus Ticket (Astro scaffold)
Astro 6 (Node 22+), Tailwind v4 via `@tailwindcss/vite`, content layer collections, fonts via the built-in Fonts API, and `withastro/action@v6` deploying to the preview URL from day one. Every later slice is visible on a real URL.

### Skateboard (theme + parity content)
Dark mode only (no theme toggle until light tokens exist), the custom theme, and everything on the parity checklist.

- Slice: dark theme with design tokens from the visual spec (as Tailwind v4 `@theme` CSS)
- Slice: keycap navigation component (focus-visible + reduced-motion built in, not bolted on)
- Slice: blog post card + listing page
- Slice: URL inventory of the live Hugo site, then redirect map, 404, canonical URLs, sitemap
- Slice: migrate existing Hugo content (frontmatter to the new schema: single `author`, `series` where relevant)
- Slice: RSS feed at the legacy-compatible path
- Slice: Giscus with unchanged pathname mapping, existing threads verified
- Slice: about page (bio + hobby badges; the keylog timeline comes later)
- Slice: **DNS cutover** (parity checklist green). From here on, every slice ships straight to production.

## Earliest Usable

### Scooter (portfolio + projects)
- Slice: career keylog timeline on the about page
- Slice: project cards grid (all active projects)
- Slice: talks and CV download
- Slice: Momo's author identity (peach accent, author card)
- Slice: per-post OG images generated at build time (keycap-styled template)

### Bicycle (dual-author blog)
- Slice: author-based theming (accent color shifts per author)
- Slice: series landing pages at `/blog/series/[series]` (momo-diary, prisma-devlog)
- Slice: content filtering by project, author, tag
- Slice: per-author RSS feeds ("subscribe to Momo's diary")
- Slice: light mode tokens + FOUC-free theme toggle (the toggle ships only now, when light mode actually exists)
- Slice: Lighthouse CI budget in the deploy workflow (speed is the brand, so measure it)

## Earliest Lovable

### Car (Firmament + Momo's space)
- Slice: embed Firmament's public mode as the interactive galaxy map. Do NOT build a separate D3 force graph here; that plan lives with [Firmament](https://github.com/niklastypes/firmament), which owns the visualization, the layout, and the data contract (its aggregation job emits the public-mode JSON). The blog is a consumer.
- Slice: Momo's corner (her own section, peach-themed, whatever she wants to post)
- Slice: code block styling with purple-tinted Shiki syntax theme
- Slice: media pipeline hardening for the Prisma devlog (astro:assets, GIF converted to muted looping video)

## Beyond

- **Momo replying to Giscus comments:** deliberately parked behind its own safety design; autonomous public replies are a much bigger risk surface than publishing diary entries
- Snowglobe widget embed showing Momo's current state
- Search via Pagefind (if content grows enough to need it)
- SSR (only if ever needed): GitHub Pages can't do it; Cloudflare is the path of least resistance since the Astro acquisition
