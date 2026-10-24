# Mikoshi Blog Post — Draft Outline

> **Type:** Project showcase (one-shot, higher-level)
> **Author:** Niklas (purple accent)
> **Target publish:** when Mikoshi v1 (Slice 1+2 minimum, ideally Slice 3) is shipping and the new vault is in active daily use
> **Status:** bullet-point outline; prose draft happens at publish time

---

## Working titles (pick one)

- **"My second brain learned to clean itself while I sleep."** (Gardener hook; poetic)
- **"Rebuilding my second brain to think with me, not just for me."** (Vision-led)
- **"PARA, Karpathy, and a gardener: making my Obsidian vault AI-native."** (Stack-led, SEO-friendly)
- **"What changed when I rebuilt my second brain for the agent era."** (Reflective)

Lean **first one** for hook strength; pivot if the post ends up more about architecture than about the gardener.

---

## Section beats

### 1. The hook
- A small concrete scene that lands the why
- Candidate openings:
  - Niklas's wife handed ChatGPT her self-written notes; got a richer self-picture than she'd built alone
  - The realization that a vault with years of curated taste data IS an identity, if something can read it
  - The Karpathy LLM-wiki thread (Karpathy's tweet / pattern) and how it reframed what a vault is for
  - The brain-glymphatic-system analogy: vault accumulates "metabolic waste" (broken links, stale claims, missed connections); a gardener cleans it while you sleep
- Probably: open with the gardener metaphor, drop the wife's example as the moment-of-resonance later

### 2. The starting point
- Years of Mikoshi already there (PARA, 1445 notes, 52 Bases, deep INTERESTS/CAREER subtrees)
- What worked: PARA structure, the folder-note vocabulary, the year-retrospective Bases lifecycle, Media DB for media tracking
- What was missing: agent-native conventions, hygiene automation, a self-knowledge synthesis layer, schema governance
- The vault was a great file system; not yet a thinking partner

### 3. The reframing — vault as substrate, not destination
- Old mental model: vault is where I put things to find them later
- New mental model: vault is structured data that humans AND agents read, write, maintain, and reflect against
- This means conventions matter more than ever (so an agent can read consistently)
- It also means hygiene matters more (more entropy if no one's tending it)
- And it opens a third use: the vault knows things about me that I can ask back

### 4. The architecture (light touch, not exhaustive)
- 5 layers (vault content / `.claude/` / `99_META/` / MCP / agent / web view)
- Mention: kepano's official Agent Skills shipped (game-changer for not-rolling-our-own)
- Official Obsidian CLI (Feb 2026, also a game-changer)
- `aaronsb/obsidian-mcp-plugin` for Bases/graph queries to the agent
- Nooscope for local embeddings (Ollama + nomic-embed-text + SQLite)
- All local, all on Qube, no cloud dependency
- Don't go full architecture diagram in prose; one good visual

### 5. The maxims that mattered most
- **Folder-note vocabulary** (3 patterns: prose-md / base / eponymous-md-with-assets) — already present in old vault but never named
- **Organic grouping over upfront hierarchy** — folders emerge from content density, gardener proposes them
- **One canonical note, multi-home via properties** — PARA folders are primary, additional memberships are tags/properties
- **Inbox is flat** — subfolders in inbox are failures of triage
- **Files over apps** (kepano's maxim) — vault outlives any tool

### 6. The Karpathy three-layer pattern
- raw/ (immutable sources) + wiki/ (LLM-distilled topic pages) + schema (CLAUDE.md governing both)
- Nested inside RESOURCES/dev/
- Three operations: ingest, query, lint
- Concrete example: "I want to learn SSE" → agent defuddles authoritative sources into raw/sse/, synthesizes wiki/SSE.md per the schema, suggests backlinks, lists what to study next
- Frees time from note-writing to actual learning

### 7. The Gardener (the most fun part)
- Brain glymphatic system: cleans metabolic waste during sleep
- Brain hippocampus: consolidates memories during sleep
- Vaults need the same thing: hygiene + connection + insight surfacing
- Backed by Letta AI's "sleep-time compute" paper (April 2025) — academic framing, not just metaphor
- Nightly cron on Qube; runs while I sleep; drops a briefing note for morning coffee
- 4 phases: hygiene (auto-applied), decay tracking (surfaced), connection enrichment (surfaced), insight surfacing (surfaced)
- Plus a 5th phase: self-knowledge surfacing (next section)
- Safety contract: never deletes, always reversible via git, never modifies authored content

### 8. The unexpected dimension — `niklas.md`
- The wife's story: write notes about yourself, hand to ChatGPT, get a rich self-picture
- My version: niklas.md at vault root, hand-authored core (identity, values, anti-values, motivations, fascinations, dreams, growth edges) plus agent-augmented sections (observed patterns, surfaced questions)
- The gardener's 5th phase surfaces patterns: "7 notes on agent harnesses this quarter, may reflect shift toward orchestration"
- Calibrated epistemic humility: assert obvious, propose uncertain
- Quarterly review cadence; opt-in for non-companion agents
- Not a psychoanalyst — a lens for reflection
- The synthesis benefits from years of vault data, not just a blank page

### 9. Cross-project benefits
- The same agent-managed-vault patterns work for **Grimoire-generated campaign vaults** (Hologrammatica, Prisma's worldbuilding side): Karpathy three-layer maps to canon/world/sources naturally, the gardener becomes a session-prep digest, uncertainty extends Grimoire's `canon` flag
- **Momo** gets a foundation: when she comes online with vault read-access, she loads niklas.md first as anchor; her own observed-via-conversation lorebook layers on top. She's not building her understanding of me from zero
- The pattern compounds across projects

### 10. What surprised me along the way
- How much was already there (Bases were already proven, folder-note vocabulary was already used unconsciously, year-retrospective bases were already a query pattern not a folder pattern)
- How much the existing tooling has matured in 2026 (kepano's skills shipped, official CLI shipped, multiple mature MCP plugins, Nooscope existed when I was about to build my own)
- The "don't build, compose" instinct paid off — almost everything I was going to write from scratch was already there
- The Mikoshi inspection grounded the vision; the vision shaped what to do with what I found

### 11. What's next
- Open invitations: anyone running an Obsidian vault can apply most of this; link the design docs in [empyrean](https://github.com/niklastypes/empyrean) only if the repo is public by then (it is currently PRIVATE; see brainstorm.md, Open Decisions)
- The Mikoshi rebuild itself is staged in slices (skateboard → scooter → bicycle...); I'll know it's working when daily use feels lighter and the morning briefing is genuinely useful
- The next rebuild is figuring out the same pattern for Grimoire-generated vaults (Hologrammatica is the test)

### 12. Reflective close
- Tools that maintain themselves let you spend energy on what only you can do
- The vault knowing me a bit better than I know myself in some narrow ways is unsettling and useful
- A second brain isn't valuable because it stores things; it's valuable because it can reflect things back
- Brief plug for niklastypes.xyz dual-author setup (Momo's diary is next on the writing list)

---

## Visuals to include

- Architecture diagram (the 5 layers; reuse from `empyrean/mikoshi/design.md`)
- Gardener flow (4+1 phases → briefing note)
- Screenshot of the briefing note (when one actually exists, post-Slice 4)
- Maybe: before/after of a note that the gardener cleaned up (broken link repair + backlink suggestion accepted)
- The folder-note vocabulary illustrated (3 patterns shown side-by-side)
- niklas.md structure (sections only, no actual content; intimate by design)

## What to NOT include

- The full criteria/research/design docs verbatim — link to them in empyrean
- Anything from niklas.md's actual content (intimate)
- Specific embedded vault data (recipes, books, etc.)
- Critique of any specific Obsidian plugin/tool by name unless it's a genuine recommendation
- Promises about Momo's timeline (she has her own diary; let her speak)

## Tone reminders (per writing-style.md)

- Niklas voice: technical, precise, clean; informal but thoughtful
- No em dashes (commas/colons/parens/separate sentences)
- Sparring-partner energy when discussing trade-offs
- Architecture + system-design framing
- Pop culture / personal interest references welcome
- Capture the "why" behind decisions, not just the "what"

## Cross-references in the post

- Link to [empyrean repo](https://github.com/niklastypes/empyrean) for design docs (blocked on the visibility decision; drop the link if it stays private)
- Link to kepano/obsidian-skills
- Link to the Letta sleep-time-compute paper
- Link to Karpathy's LLM-wiki tweet/post
- Link to aaronsb/obsidian-mcp-plugin and Nooscope
- Cross-link to future Grimoire showcase post (when written) and Momo dual-diary entries

## Pre-publish checklist

- [ ] Mikoshi v1 in active daily use for at least 2 weeks
- [ ] The Gardener has produced at least 5 useful briefings
- [ ] niklas.md has been hand-authored and reviewed once
- [ ] At least one screenshot of the morning briefing exists
- [ ] One concrete "gardener caught X" anecdote ready to include
- [ ] Empyrean visibility decided (repo is currently PRIVATE; this post wants to link it)
