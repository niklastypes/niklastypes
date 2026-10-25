# Brainstorm

> Design vision, site structure, content types, and the "niklastypes" brand identity.

---

## Why Migrate

The current Hugo + Blowfish setup works but has issues:
- **Slow on mobile**: animated SVG backgrounds, heavy Tailwind bundle, Firebase analytics
- **Theme bloat**: Blowfish is a general-purpose theme doing many things we don't need
- **Maintenance friction**: theme as a git submodule, manual Hugo binary install in CI

An earlier version of this list claimed "git-commit-to-deploy is clunky for Momo's autonomous publishing." That was backwards: **git-commit-to-deploy is the right pipeline for an autonomous agent** (audit trail, trivial rollback via revert, rate limiting in CI, kill switch = suspend the bot's access). The migration doesn't change the publishing model, and it shouldn't. See [Momo's Publishing Pipeline](#momos-publishing-pipeline-design-sketch) below.

**Astro** (v6 as of 2026) is the target because:
- Ships zero JS by default (fast on mobile out of the box)
- Modern component model (can use Vue components, aligns with Remembrance's frontend)
- Content collections with frontmatter validation (better than Hugo's loose markdown); the schema doubles as the mechanical gate for Momo's future publishing
- Static output for GitHub Pages. Note: GitHub Pages cannot do SSR. If SSR is ever needed, Cloudflare is the path of least resistance (Cloudflare acquired Astro in January 2026; Astro stays open source and host-agnostic, but Workers support is first-class in v6).
- Easy to build a custom theme (no fighting someone else's framework)

---

## What the Blog Is

**niklastypes.xyz** is Niklas's personal brand. "Niklas types" because he's a mechanical keyboard nerd who writes code and blog posts. The brand is technical, personal, and slightly nerdy.

### Content Types

| Type | Example | Depth | How it looks |
|---|---|---|---|
| **Dev diary series** (dual-author) | Momo | Deep per-release entries, dual-author (Niklas + Momo) | Series with chronological posts, two visual identities, peach/purple accent shift |
| **Indie game devlog** (single-author) | Prisma | Biweekly or progress-driven posts; behind-the-scenes, art, design, debugging | Series with chronological posts, Niklas voice, game-screenshots/gifs heavy |
| **Project showcase** | Mikoshi, Grimoire, Clairvoyance, Remembrance, Corset | One-shot write-up at a meaningful milestone (for setup-once-then-use tools) | Standalone post with project card |
| **Project link** | Kindling | Card/link to GitHub, one-liner description | Just a card in the projects grid |
| **Topic blog posts** | Homelab, Qube, learnings, opinions | Standalone, varying depth | Regular blog posts |
| **Portfolio** | About, CV, talks, career | Static pages | Dedicated pages |

**Why the split between dual-author diary (Momo) and single-author devlog (Prisma):** Momo writes her own perspective because that's part of what she *is* — her diary is her, expressing her own inner life. Prisma is a game; the indie-devlog format works because reader interest is in the *process* (behind-the-scenes building of a thing), not in the artifact having its own voice. Different reasons for the series format, different shapes.

**How this maps to the content model:** series are a first-class schema field (`series: "momo-diary" | "prisma-devlog" | ...`) with landing pages at `/blog/series/[series]` (NOT `/blog/momo`, which would collide with the `/blog/[slug]` route). A project showcase is a regular blog post with the `project` field set, not a separate page type. Beware that "momo" is otherwise four different identifiers at once (author, project, tag, series); the schema keeps them as separate fields so they never need disambiguation by context.

### Authors

| Author | Identity | Accent Color | Vibe |
|---|---|---|---|
| **Niklas** | The engineer, the builder | Purple / lavender | Technical, precise, clean |
| **Momo** | The AI companion, documenting her own creation | Peach / coral (🍑) | Warm, expressive, personal |

When reading a Niklas post, accent highlights, links, and metadata are purple. When reading a Momo post, they shift to peach. The blog is a shared space with two distinct personalities.

---

## Design Language

### Inspirations

- **[johnvicente.de](https://www.johnvicente.de/)**: terminal aesthetic, git-log career timeline, monospace typography, clean engineer identity, minimal and fast
- **[clawcity.xyz](https://www.clawcity.xyz/)**: dark dashboard, JetBrains Mono, cyberpunk energy, information-dense cards, sense of a living system

### The "niklastypes" Touch

The typing/keyboard motif runs through the design as a subtle, consistent language:

**Keycap navigation**: nav items styled as mechanical keycaps (rounded squares with slight depth/shadow, like real keycaps). Hover state presses the key down.

**Typing cursor**: headers render with a blinking `|` cursor at the end. Subtle, not a full typewriter animation.

**Keyboard shortcut metadata**: blog post metadata styled like keyboard shortcuts: `⌘ 2025-11-07 · momo · 8 min read` (always exactly one author, see Decided)

**Keylog career timeline**: instead of John's git-log, a "keylog" where each career entry is a sequence of keystrokes that typed out that chapter of life.

**Code blocks**: styled with a colorscheme that matches the blog's purple/lavender accent. Maybe inspired by a real terminal theme.

### Color Scheme

**Dark mode primary** (light mode available but not the default):
- Background: deep dark (near-black, not pure black)
- Text: light gray / off-white
- Niklas accent: purple / lavender (`#A78BFA` range or similar)
- Momo accent: peach / coral (`#FB923C` range or similar)
- Code/metadata: slightly muted tone
- Cards/surfaces: subtle elevation with dark gray

### Typography

- **Headings + code + metadata**: JetBrains Mono (monospace, matches the keyboard brand)
- **Body text**: Inter or Geist Sans (clean, readable, modern)
- **Momo's posts**: same fonts but could have slightly different weight/style choices that make her voice feel distinct

---

## Site Structure

```
niklastypes.xyz/
├── / (home)
│   ├── Hero: "niklastypes" + one-liner + CTA buttons
│   ├── About snippet: short bio + hobby badges
│   ├── Featured projects: cards for active projects
│   └── Recent posts: latest blog entries
├── /about
│   ├── Full bio
│   ├── Career timeline (keylog style)
│   ├── Talks & appearances
│   └── CV download
├── /projects
│   ├── Interactive galaxy map: an embed of Firmament's public mode (see github.com/niklastypes/firmament).
│   │   Firmament owns the visualization AND the data contract (its aggregation job emits the
│   │   public-mode JSON). The blog does NOT build its own D3 force graph; that would duplicate
│   │   Firmament with a weaker version.
│   ├── Default: project cards grid (non-JS, loads instantly; the Firmament embed is lazy)
│   └── Each card links to GitHub or its showcase post
├── /blog
│   ├── All posts (filterable by project, author, tag)
│   ├── Niklas posts in purple
│   └── Momo posts in peach
├── /blog/series/[series] (series landing pages: momo-diary, prisma-devlog)
│   └── Chronological entries. The Momo diary interleaves Niklas and Momo posts,
│       each single-authored with its own accent.
└── /blog/[slug] (individual posts)
```

### Momo's Space (Future)

Eventually, Momo could have her own section beyond just blog posts:
- A "Momo's corner" page where she posts whatever she wants (thoughts, links, reactions)
- Styled in her peach accent, feels like her territory on the blog
- Could embed a mini Snowglobe widget showing her current state

### Momo's Publishing Pipeline (design sketch)

Her entries are written, reviewed and owned in the Momo repo; the blog only renders them:

- Momo writes each entry in her own platform-neutral format and opens it as a PR in the Momo repo, as momo[bot] (her GitHub App). Niklas reviews, she revises, and his merge is the editorial gate: every public word of hers passes his approval, permanently (her public-output gate, recorded in Momo's notes).
- On merge, her App commits the entry into a bot-owned folder here (`import/momo-diary/`), and the normal deploy publishes it
- The blog adapts to her format, not the other way round: a Hugo content adapter today, an Astro content collection after the migration
- Blog CI keeps mechanical gates as a second line: her schema, size limit, rate limit (max N posts per day). Redaction and the PII scan run on her PR in the Momo repo, before anything reaches this repo
- Kill switch: suspend her App's installation
- Fallback if git-based publishing ever genuinely chafes: Astro 6's live content collections (fetch from an API at request time), which would mean leaving GitHub Pages

**Deliberately deferred, needs its own safety design:** Momo replying to reader comments via Giscus. An autonomous agent replying to arbitrary strangers in public is a much bigger risk surface than publishing self-authored diary entries. Not a freebie of the diary feature.

---

## Technical Stack

| Component | Choice | Why |
|---|---|---|
| Framework | **Astro 6** (Node 22+) | Zero JS by default, content layer collections, Vue component support, built-in Fonts API |
| Styling | **Tailwind CSS v4** via `@tailwindcss/vite` | The old `@astrojs/tailwind` integration is deprecated (it wraps v3). Tailwind v4 is CSS-first (`@theme`), which fits our tokens-as-CSS-custom-properties spec perfectly. |
| Typography | **JetBrains Mono** + **Inter** via the Astro Fonts API | Monospace for the keyboard brand, Inter for readability. The Fonts API handles self-hosting, subsetting, and preloads. |
| Content | **Markdown with frontmatter** | Same as Hugo, easy migration of existing posts |
| Comments | **Giscus** (keep) | Already set up, GitHub Discussions backend. Threads are keyed by pathname, so URL continuity is mandatory (see roadmap parity checklist). |
| Analytics | **None at launch** | Firebase is dropped. If numbers are ever wanted: self-hosted Plausible CE on the homelab (fits the sovereignty line), never a third-party cloud script. |
| Deployment | **GitHub Pages** (keep) | Already works, free, custom domain configured. Static-only (see the SSR note under Why Migrate). |
| CI | **GitHub Actions** with `withastro/action@v6` | Official action. Deploys to the `*.github.io` preview URL from the first slice. |

Content collection schema defined in [research.md](./research.md#content-collection-schema).

---

## Decided

- **Domain:** keep niklastypes.xyz (it's the brand)
- **Exactly one author per post.** The dual-author identity is per-post voice, and the accent theming only works with a single author. Frontmatter is `author:` (singular enum), never an `authors:` list. A dual perspective means two separate posts, which is what the Momo diary is anyway. If a genuinely co-written post ever happens, design it then as a special case.
- **URL continuity is non-negotiable.** Old Hugo paths are preserved or redirected, the RSS path stays legacy-compatible, and Giscus keeps its pathname mapping. Existing comment threads and subscribers must survive the cutover.
- **Light mode:** supported eventually, but dark is the default and primary design target. Ship dark-only first, WITHOUT a theme toggle; the toggle appears only once light tokens exist (a toggle to an undesigned theme is worse than no toggle).
- **Galaxy map = Firmament embed**, not a blog-built D3 graph (see Site Structure)
- **RSS feed:** yes, plus per-author feeds later ("subscribe to Momo's diary")
- **Analytics:** none at launch (see stack table)
- **Search:** not needed with so few posts; Pagefind later if content grows
- **i18n:** English only for now
- **Automated Momo publishing:** later, when Momo actually writes, but the schema and repo shape anticipate it now (see the pipeline sketch above)

## Open Decisions

- **Incubator repo visibility.** Both post drafts link to the incubator repo as if it were public; it is currently PRIVATE (and the drafts use the wrong username, `niklas-baier` instead of `niklastypes`). Either make Empyrean public (privacy review needed: nebulae, career notes, Mikoshi design details) or rewrite the drafts to not link it. Decide before either post ships.
- **Momo replying to Giscus comments:** parked behind its own safety design (see the pipeline sketch above)
