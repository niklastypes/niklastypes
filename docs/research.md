# Research

> Visual design specification: design tokens, component specs, page layouts, responsive behavior. A coding agent builds from this.

---

## Design Tokens

### Colors (Dark Mode, Primary)

```css
:root {
  /* Backgrounds */
  --bg-canvas: #0d1117;       /* page background, GitHub-dark inspired */
  --bg-surface: #161b22;      /* cards, nav, elevated surfaces */
  --bg-raised: #1c2128;       /* nested elements, badges, code blocks */

  /* Text */
  --text-primary: #e6edf3;    /* main body text */
  --text-secondary: #8b949e;  /* metadata, dates, muted text */
  --text-dim: #484f58;        /* very subtle, dividers, inactive */

  /* Niklas accent (purple/lavender) */
  --accent-niklas: #a78bfa;        /* links, highlights, active states */
  --accent-niklas-dim: #7c3aed33;  /* subtle backgrounds, borders */
  --accent-niklas-hover: #c4b5fd;  /* hover state */

  /* Momo accent (peach/coral) */
  --accent-momo: #fb923c;         /* links, highlights on Momo posts */
  --accent-momo-dim: #ea580c33;   /* subtle backgrounds, borders */
  --accent-momo-hover: #fdba74;   /* hover state */

  /* Functional */
  --border: #21262d;          /* card borders, dividers */
  --border-hover: #30363d;    /* border on hover */
  --commit-hash: #e3b341;     /* yellow for git hashes, keycap legends */
}
```

### Colors (Light Mode)

Light mode should exist but is a secondary concern. Invert the hierarchy: light canvas, dark text, same accent hues but slightly deeper. Design dark mode first, adapt later.

### Typography

```css
:root {
  /* Fonts */
  --font-mono: 'JetBrains Mono', monospace;
  --font-sans: 'Inter', sans-serif;

  /* Scale */
  --text-xs: 0.75rem;     /* 12px - badge labels, tiny metadata */
  --text-sm: 0.875rem;    /* 14px - metadata, nav items, dates */
  --text-base: 1rem;      /* 16px - body text */
  --text-lg: 1.125rem;    /* 18px - lead paragraphs */
  --text-xl: 1.25rem;     /* 20px - section headers */
  --text-2xl: 1.5rem;     /* 24px - page titles */
  --text-3xl: 1.875rem;   /* 30px - hero heading */
}
```

| Context | Font | Weight | Size |
|---|---|---|---|
| Body text | Inter | 400 | base (16px) |
| Headings (h1-h3) | JetBrains Mono | 600 | 2xl-3xl |
| Subheadings (h4-h6) | JetBrains Mono | 500 | lg-xl |
| Navigation | JetBrains Mono | 400 | sm (14px) |
| Metadata (dates, tags, reading time) | JetBrains Mono | 400 | xs-sm |
| Code (inline + blocks) | JetBrains Mono | 400 | sm |
| Badge labels | JetBrains Mono | 400 | xs |

### Spacing

```css
:root {
  --space-page-x: clamp(1.5rem, 5vw, 2.5rem);  /* responsive page padding */
  --space-section-y: clamp(2.5rem, 6vw, 3.5rem); /* between major sections */
  --space-card-padding: 1rem;
  --space-card-gap: 1rem;
  --max-width: 72rem;   /* max-w-6xl, ~1152px */
  --max-width-prose: 48rem; /* max-w-3xl for blog post content */
}
```

### Borders & Radius

```css
:root {
  --radius-sm: 0.25rem;   /* small elements, inline badges */
  --radius-md: 0.375rem;  /* cards, buttons */
  --radius-lg: 0.5rem;    /* large cards, keycaps */
  --border-width: 1px;
}
```

---

## Components

### 1. Keycap Button (Navigation + CTAs)

The signature "niklastypes" element. Nav items and CTA buttons styled as mechanical keyboard keycaps.

```
┌─────────┐
│  /blog  │  <- monospace text, centered
└─────────┘
```

**Styling:**
- Background: `var(--bg-surface)`
- Border: 1px `var(--border)`
- Border-radius: `var(--radius-lg)` (slightly rounded, like a real keycap)
- Box-shadow: `0 2px 0 var(--border)` (bottom shadow creates the "depth" of a keycap)
- Padding: `0.375rem 0.75rem`
- Font: JetBrains Mono, `var(--text-sm)`
- Text color: `var(--text-secondary)`

**Hover state (key press):**
- Box-shadow shrinks: `0 1px 0 var(--border)` (keycap pushes down)
- Transform: `translateY(1px)` (moves down with the shadow)
- Border-color: `var(--accent-niklas-dim)`
- Text-color: `var(--accent-niklas)`
- Transition: `all 0.1s ease` (snappy, like a keypress)

**Active state:**
- Box-shadow: `0 0 0` (fully pressed)
- Transform: `translateY(2px)`

### 2. Typing Cursor

Blinking cursor after page headings (h1 only).

```css
.heading-cursor::after {
  content: '|';
  animation: blink 1s step-end infinite;
  color: var(--accent-niklas);
  margin-left: 0.125rem;
}

@keyframes blink {
  0%, 100% { opacity: 1; }
  50% { opacity: 0; }
}
```

On Momo's pages, the cursor color uses `var(--accent-momo)`.

### 3. Blog Post Card

Used in the blog listing and "recent posts" sections.

```
┌──────────────────────────────────────┐
│  ⌘ 2025-11-07 · momo · 8 min read   │  <- metadata row, monospace
│──────────────────────────────────────│
│  v0.1.0 - Building Momo             │  <- title, JetBrains Mono 600
│  The idea is to create my own...     │  <- excerpt, Inter 400, text-secondary
│                                      │
│  🏷 momo  lifesim  personality       │  <- tags as small badges
└──────────────────────────────────────┘
```

**Styling:**
- Background: `var(--bg-surface)`
- Border: 1px `var(--border)`
- Border-radius: `var(--radius-md)`
- Padding: `var(--space-card-padding)`
- No box-shadow (flat, border-defined)

**Metadata row:**
- Font: JetBrains Mono, `var(--text-xs)`
- Color: `var(--text-secondary)`
- The `⌘` prefix is the keyboard shortcut motif
- Separator: ` · ` (middle dot)

**Author accent:**
- Left border or top accent line: 3px solid in the author's accent color
- Niklas posts: purple left border
- Momo posts: peach left border
- This is the immediate visual distinction between authors

**Hover:**
- Border-color: author's accent-dim color
- Background: `var(--bg-raised)`
- Transition: `colors 0.15s ease`

### 4. Project Card

Used in the /projects grid and homepage featured projects.

```
┌──────────────────────────────────────┐
│  🍑 Momo                        →   │  <- emoji + name + arrow
│  Digital being with personality,     │  <- description, text-secondary
│  emotions, and agency                │
│                                      │
│  Python · FastAPI · PydanticAI       │  <- tech badges
└──────────────────────────────────────┘
```

**Styling:**
- Same card base as blog post card
- Arrow (→) translates right on hover (`transform: translateX(2px)`)
- Tech badges: inline, `var(--bg-raised)` background, `var(--radius-sm)`, monospace xs

### 5. Career Keylog Entry

The about page timeline. Instead of a git-log, a "keylog" where each career chapter is a keystroke sequence.

```
> e3b341  2024-present  Aleph Alpha       AI Engineer  ████████░░
> a1f290  2022-2024     ProSiebenSat.1    ML Engineer  ██████░░░░
> d4c8e2  2019-2022     Deloitte          Consultant   ████░░░░░░
```

**Styling:**
- Grid: `grid-cols-[70px_120px_1fr_120px]` on desktop, stacks on mobile
- Commit hash: JetBrains Mono, `var(--commit-hash)` (yellow), xs
- Date range: JetBrains Mono, `var(--text-secondary)`, sm
- Company: JetBrains Mono, link styled in blue/accent
- Role: Inter, `var(--text-primary)`
- Row divider: 1px `var(--border)` between entries
- Optional: progress bar showing tenure length relative to career total
- Prompt character `>` in `var(--text-dim)` before each row

### 6. Hobby/Interest Badge

Used in the about snippet on the homepage.

```
┌──────────────────┐
│  ⌨️ mech keebs   │
└──────────────────┘
```

**Styling:**
- Display: inline-flex, items-center, gap-2
- Background: `var(--bg-raised)`
- Border: 1px `var(--border)`
- Border-radius: `var(--radius-sm)`
- Padding: `0.375rem 0.75rem`
- Font: JetBrains Mono, xs
- Emoji + text label

### 7. Author Card

Displayed at the top or bottom of blog posts.

**Niklas variant:**
```
┌─────────────────────────────────────┐
│  [photo]  Niklas Baier              │
│           AI Engineer               │
│           ⌨️ 🎲 🏃 ☕               │
└─────────────────────────────────────┘
```
- Accent border: purple

**Momo variant:**
```
┌─────────────────────────────────────┐
│  [avatar] Momo (もも) 🍑            │
│           AI companion              │
│           "documenting my own       │
│            creation"                │
└─────────────────────────────────────┘
```
- Accent border: peach
- Avatar could eventually be animated or show current state

### 8. Navigation Bar

```
  niklastypes                    [/]  [/about]  [/projects]  [/blog]   ☀/🌙
  ───────────────────────────────────────────────────────────────────────────
```

- Left: "niklastypes" in JetBrains Mono, `var(--text-primary)`, bold
- Right: keycap buttons for each route + theme toggle
- Border-bottom: 1px `var(--border)`
- Sticky on scroll
- Max-width: `var(--max-width)`, centered
- Background: `var(--bg-canvas)` with slight backdrop-blur when scrolled

### 9. Code Block

```
┌─ filename.py ────────────────────────┐
│  1 │ def hello():                    │
│  2 │     return "niklastypes"        │
└──────────────────────────────────────┘
```

- Background: `var(--bg-raised)`
- Border: 1px `var(--border)`
- Border-radius: `var(--radius-md)`
- Font: JetBrains Mono, sm
- Line numbers: `var(--text-dim)`
- Filename tab: `var(--bg-surface)` with top border-radius
- Syntax highlighting: use a purple-tinted theme (e.g., based on GitHub Dark Dimmed but with purple accents)

---

## Page Layouts

### Homepage

```
┌─────────────────────────────────────────────────────┐
│  [nav bar]                                          │
├─────────────────────────────────────────────────────┤
│                                                     │
│  niklastypes|                                       │  <- hero, JetBrains Mono 3xl
│  AI Engineer. Keyboard nerd.                        │     with blinking cursor
│  Building things that type back.                    │
│                                                     │
│  [⌘ Contact]  [📄 CV]                               │  <- keycap CTAs
│                                                     │
├─────────────────────────────────────────────────────┤
│                                                     │
│  About                                              │
│  [short bio paragraph]                              │
│  ⌨️ mech keebs  🎲 D&D  🏃 running  ☕ coffee  ... │  <- hobby badges
│                                                     │
├─────────────────────────────────────────────────────┤
│                                                     │
│  Projects                                           │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐          │
│  │ 🍑 Momo  │  │ ⚱️ Remem │  │ 👗 Corset│          │  <- project cards grid
│  └──────────┘  └──────────┘  └──────────┘          │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐          │
│  │ Clairv.  │  │ 🪵 Kindl │  │ 🏠 Home  │          │
│  └──────────┘  └──────────┘  └──────────┘          │
│                                                     │
├─────────────────────────────────────────────────────┤
│                                                     │
│  Recent Posts                                       │
│  ┌─────────────────────────────────────────────┐    │
│  │ ⌘ 2025-11-07 · niklas                      │    │  <- blog post cards
│  │ v0.1.0 - Building Momo                      │    │     (one author per post)
│  └─────────────────────────────────────────────┘    │
│  ┌─────────────────────────────────────────────┐    │
│  │ ⌘ 2025-12-11 · momo                        │    │
│  │ v0.2.0 - Project Setup                      │    │
│  └─────────────────────────────────────────────┘    │
│                                                     │
├─────────────────────────────────────────────────────┤
│  [footer: social links, "built with Astro", ©]     │
└─────────────────────────────────────────────────────┘
```

### Blog Post Page

```
┌─────────────────────────────────────────────────────┐
│  [nav bar]                                          │
├─────────────────────────────────────────────────────┤
│                                                     │
│  ┌─ max-w-prose ─────────────────────────────────┐  │
│  │                                               │  │
│  │  v0.1.0 - Building Momo|                      │  │  <- title with cursor
│  │  ⌘ 2025-11-07 · 12 min read                   │  │  <- metadata
│  │                                               │  │
│  │  [author card: niklas, purple accent]          │  │
│  │                                               │  │
│  │  ─────────────────────────────────             │  │
│  │                                               │  │
│  │  [blog post content in Inter]                 │  │
│  │  [code blocks in JetBrains Mono]              │  │
│  │  [images with rounded corners]                │  │
│  │                                               │  │
│  │  ─────────────────────────────────             │  │
│  │                                               │  │
│  │  🏷 momo  lifesim  personality                │  │  <- tags
│  │                                               │  │
│  │  [prev/next post navigation]                  │  │
│  │                                               │  │
│  │  [giscus comments]                            │  │
│  │                                               │  │
│  └───────────────────────────────────────────────┘  │
│                                                     │
└─────────────────────────────────────────────────────┘
```

### About Page

```
┌─────────────────────────────────────────────────────┐
│  [nav bar]                                          │
├─────────────────────────────────────────────────────┤
│                                                     │
│  About|                                             │  <- heading with cursor
│                                                     │
│  [full bio, 2-3 paragraphs]                         │
│  [hobby badges row]                                 │
│                                                     │
│  Career                                             │
│  > e3b341  2024-now    Aleph Alpha    AI Engineer   │  <- keylog entries
│  > a1f290  2022-2024   P7S1           ML Engineer   │
│  > d4c8e2  2019-2022   Deloitte       Consultant    │
│                                                     │
│  Talks & Writing                                    │
│  ┌──────────┐  ┌──────────┐                         │  <- talk cards
│  │ Talk 1   │  │ Article  │                         │
│  └──────────┘  └──────────┘                         │
│                                                     │
│  [📄 Download CV]                                    │  <- keycap CTA
│                                                     │
└─────────────────────────────────────────────────────┘
```

---

## Author-Based Theming

When a page belongs to a specific author, the accent color shifts globally:

```css
/* Default (Niklas) */
:root {
  --accent: var(--accent-niklas);
  --accent-dim: var(--accent-niklas-dim);
  --accent-hover: var(--accent-niklas-hover);
}

/* Momo pages */
[data-author="momo"] {
  --accent: var(--accent-momo);
  --accent-dim: var(--accent-momo-dim);
  --accent-hover: var(--accent-momo-hover);
}
```

This means the typing cursor, link colors, card borders, hover states, and any accent-colored element automatically shift when reading a Momo post. No per-component overrides needed.

---

## Responsive Behavior

| Breakpoint | Layout changes |
|---|---|
| **Mobile (<640px)** | Single column, keycap nav collapses to hamburger or horizontal scroll, career keylog stacks vertically, project cards single column |
| **Tablet (640-1024px)** | Two-column grids for cards, keylog stays grid |
| **Desktop (>1024px)** | Full layout, max-w-6xl centered, all grids at full column count |

---

## Animation Budget

Keep animations minimal and purposeful. This site should feel fast and crisp, not flashy.

| Animation | Duration | Easing | Purpose |
|---|---|---|---|
| Keycap press | 0.1s | ease | Tactile button feedback |
| Cursor blink | 1s | step-end | Typing motif |
| Card hover | 0.15s | ease | Surface state change |
| Arrow translate | 0.15s | ease | "Go to" affordance |
| Theme toggle | 0.2s | ease | Color transition |

No animated backgrounds, no parallax, no scroll-triggered animations. Speed is the brand.

---

## Accessibility & Keyboard

A keyboard-branded site must be the best keyboard-navigable site the visitor has used all week. This is brand, not compliance.

- **`prefers-reduced-motion`:** the blinking cursor, keycap press, and every animation in the budget above get a reduced-motion variant (cursor static, transitions instant)
- **Focus states:** `:focus-visible` on every interactive element. On keycap buttons, style the focus state as a *pressed keycap* (reuse the hover/active depth treatment), turning an obligation into the signature motif.
- **Skip link** to main content, styled as a keycap sliding down from the top edge
- **Contrast caveat:** `--text-secondary` (#8b949e on #0d1117) sits at the WCAG AA boundary for small text. Fine for metadata; never use it for body copy.
- Semantic landmarks, alt text on all images, focus order matching visual order

---

## Assets Needed

| Asset | Format | Notes |
|---|---|---|
| Niklas photo | WebP, 200x200 | For author card, about page |
| Momo avatar | WebP or SVG, 200x200 | For author card. Eventually animated. |
| JetBrains Mono | via Astro Fonts API | Weights 400 + 600; the Fonts API handles hosting, subsetting, preloads |
| Inter | via Astro Fonts API | Weights 400 + 500 |
| Favicon | SVG + PNG | Keycap or ⌨️ motif, simple |
| OG images | PNG, 1200x630 | Per-post, generated at build time (keycap-styled template); one static fallback for non-post pages |

---

## Tech Implementation Notes

### Content Collection Schema

```typescript
// src/content.config.ts (Astro 6 content layer; legacy collections are gone)
import { defineCollection } from "astro:content";
import { glob } from "astro/loaders";
import { z } from "astro/zod"; // `z` from astro:content is deprecated in v6

const blog = defineCollection({
  loader: glob({ pattern: "**/*.md", base: "./src/content/blog" }),
  schema: z.object({
    title: z.string(),
    date: z.date(),
    updated: z.date().optional(),
    description: z.string(),
    author: z.enum(["niklas", "momo"]), // exactly one author per post (decided)
    series: z.string().optional(),      // "momo-diary", "prisma-devlog", ...
    project: z.string().optional(),
    tags: z.array(z.string()).optional(),
    draft: z.boolean().default(false),
  }),
});

const projects = defineCollection({
  loader: glob({ pattern: "**/*.md", base: "./src/content/projects" }),
  schema: z.object({
    name: z.string(),
    emoji: z.string(),
    description: z.string(),
    tech: z.array(z.string()),
    repo: z.string().url().optional(),
    featured: z.boolean().default(false),
    order: z.number().optional(),
  }),
});

export const collections = { blog, projects };
```

Reading time is computed via a remark plugin, never stored in frontmatter (it's a derived value).

**Astro setup (Astro 6, Node 22+):**
- Tailwind CSS v4 via `@tailwindcss/vite` in `vite.plugins` (`npx astro add tailwind` does this). The old `@astrojs/tailwind` integration is deprecated (it wraps Tailwind v3); do not use it.
- Content collections via the content layer API (schema above)
- Fonts via the built-in Fonts API (self-hosting, subsetting, preload for JetBrains Mono + Inter)
- Shiki for syntax highlighting (built in, supports custom themes)
- `@astrojs/sitemap`, canonical URLs, and a 404 page
- RSS feed via `@astrojs/rss`, served at a path compatible with the old Hugo feed; per-author feeds later
- Per-post OG images generated at build time (satori, or astro-og-canvas which Astro's own docs use); keycap-styled template plus one static fallback for non-post pages
- Images through `astro:assets`; GIFs converted to muted looping `<video>` (webm/mp4). Matters most for the screenshot/gif-heavy Prisma devlog: GIFs are a performance disaster and speed is the brand.
- Any JS island (Firmament embed, Giscus) loads lazily (`client:visible` or on interaction); nothing interactive on the initial homepage paint

**Tailwind v4 config (CSS-first, no `tailwind.config.js`):**
- The design tokens above live in CSS as `@theme` custom properties; the token spec maps 1:1, no JS config to maintain
- Dark mode: class strategy via a custom variant for the manual toggle
- Theme toggle must be FOUC-free: an inline `<head>` script applies the stored theme class before first paint. The toggle itself ships only once light tokens exist (dark-only until then).

**Deployment:**
- GitHub Actions with `withastro/action@v6` (Node 22+)
- Deploy to the `*.github.io` preview URL from the very first slice; DNS cutover to niklastypes.xyz only when the parity checklist in roadmap.md is green
- Custom domain: niklastypes.xyz (already configured)
- Lighthouse CI budget in the workflow: "speed is the brand" is a measured invariant, not a vibe
- GitHub Pages is static-only; SSR would mean moving host (Cloudflare is the natural target since the Astro acquisition)

**Migration from Hugo (URL continuity is the critical part):**
- Inventory every URL on the live Hugo site (posts, about, RSS, sitemap) BEFORE building anything
- Preserve paths where possible; anything that moves gets an entry in Astro's `redirects` config (emits meta-refresh pages on static builds)
- Giscus discussions are keyed by pathname mapping: a changed path silently orphans the existing comment threads. Verify threads attach on the new site before cutover.
- Keep the RSS feed reachable at the old path (Hugo serves `/index.xml` by convention); existing subscribers must survive
- Copy 3 existing markdown posts, adjust frontmatter to the new schema (single `author`, `series` where relevant)
- Port author data from JSON to content collection
- Drop: Firebase, animated SVGs, Blowfish theme, Hugo binary
