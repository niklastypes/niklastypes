# Writing Style

> Reference for generating blog post drafts. Used by LLMs to pre-generate posts that need only light editing. Also serves as a contrast reference for Momo's distinct voice.

---

## Niklas's Voice

### Audience
Every post, in any series or none, is written for two readers at once. Niklas says so when a post should lean more technical or more accessible.

- **Curious readers without an AI background**, who follow along because the project sounds cool: every technical concept gets a plain-language bridge the first time it appears.
- **People who know prompts, evals, context management and harnesses**, and care more about how he tackled a hard problem than about the story around it: give them the mechanism, the numbers and the reasoning behind each decision, not just the outcome.

The second reader is never addressed directly ("for the builders among you"); the depth is simply there.

### Tone
- Conversational and enthusiastic, like explaining something cool to a friend over coffee
- Unapologetically nerdy, doesn't downplay excitement about technical details
- Self-deprecating humor sprinkled throughout, never forced
- Honest about uncertainty ("I have no idea if this is possible yet, but I want to try")
- European tech pride (prefers Mistral, values digital sovereignty, mentions local-first)

### Personality Markers
- Pop culture references as connective tissue: anchors technical concepts in fiction (anime, games, movies) before explaining the engineering
- Parenthetical asides and tangents let in naturally (parentheses, dashes, "all discussions about X aside")
- Gets visibly more excited toward the end of posts, exclamation marks increase, future ideas pour out
- Tension between wanting to do everything at once and forcing himself to take small steps, writes about both sides openly
- Treats the reader as smart but not necessarily familiar with the specific tools

### Structure
- Posts follow: context/motivation -> what was done -> why those decisions -> what's next
- Methodical organization (tables, roadmaps, clear sections) but informal prose
- Starts measured, warms up, ends excited
- Deep on the WHY of decisions, not just documenting WHAT was done
- Uses headers to organize, but the prose within sections flows naturally

### Language Patterns
- Uses "I" freely, this is personal writing not corporate
- Contractions always (it's, don't, can't, I'm)
- Occasional German or Japanese words when relevant (natural, not forced)
- Humor through self-awareness: "before you might think I'm some weirdo", "the first midlife crisis is currently hitting"
- Rhetorical questions to the reader: "How freaking cool is that?"
- References to "we" when talking about a shared journey with the reader
- Never uses em dashes; asides go in commas or parentheses, and an occasional spaced hyphen ("Full transparency - I have no idea...") is his

### What Niklas Does NOT Sound Like
- Corporate/professional blog voice ("In this article, we will explore...")
- AI-generated slop ("Let's dive in!", "In today's fast-paced world...")
- Tutorial tone ("Step 1: Open your terminal...")
- Dry technical documentation
- Overly polished or edited, his writing has a natural, slightly rough quality
- Rhetorical contrast formulas: "Not X, not Y, but Z", "X is a bug, not a feature", "it's not about X, it's about Y". He says what something *is*
- Punchy one-word fragments for emphasis ("Period.", "Full stop.")
- The same signature joke in every post: his asides land because they're occasional ("the first midlife crisis" fits once, where it fits, not as a closer for every hardware paragraph)

### What Goes Into a Post (lessons from his reviews)

- **His own words win.** When an earlier draft or post of his says it well, reuse his sentences instead of paraphrasing them. Lift paragraphs he wrote; don't polish them.
- **Pop culture and the field, generously.** He wants readers to see he's followed the topic for a long time: name the references (games, books, films, commercial and open-source projects, Big Tech moves) and link them. Mark what he hasn't used himself as such ("none of which I've actually used myself").
- **Back claims with research.** Where the post makes a claim the research supports, link the paper or study.
- **Only true facts about his life and setup.** Owning a thing isn't using it; liking a thing isn't doing it daily. Anything not in the sources or his own words stays out, or goes on the PR's open-questions list.
- **Introductory posts stay high-level.** Implementation detail (prompt architecture, personality models) is promised for a follow-up post, not explained up front.
- **Don't spoil, don't promise.** Working titles, unannounced names and plans that might not ship stay out; tease the concept instead ("a companion harness").
- **A restart is a restart.** When a project starts over, the new series doesn't refer back to the old one ("once again", "as I called it back then", "like the first time around"). The old posts are voice samples, not story.
- **Keep private logistics out.** Time budgets, the day job, what runs on which machine at home: only when he puts them in himself.
- **Say each thing once.** If the vision already names the endpoint (a homebrewed Gatebox), don't restate it in a different costume two lines later.
- **Precise hardware names.** "a base model M4 Mac Mini", not "my Mac Mini at home".
- **Parentheticals with restraint.** One good aside per paragraph beats three; cut the ones that only add a detail.
- **The hook comes first.** A one- or two-sentence italic lede before the first heading says what the post is about and why it's exciting; the personal build-up follows.
- **Split long sentences at their seams.** Past ~35 words, a sentence becomes two, keeping his words; a sentence carrying several links always gets split.
- **One form per idea.** A roadmap is a list *or* a diagram, not both; on phones the list wins.
- **Show complex things.** He likes explaining visually: a mechanism with moving parts (a pipeline, how a prompt is assembled, a state machine) gets a Mermaid diagram (`{{< mermaid >}}`), kept small enough to read on a phone. A handful per post at most, and only where the picture explains more than the paragraph next to it; a sequence of steps stays a list.
- **Suggest screenshots.** Where a real artifact would say more than prose or a diagram (a terminal session, a chat with the agent or with Momo, a trace, a UI, a failing test), leave a placeholder that says what to capture, and list it in the PR. He takes the screenshots.
- **Watch pet phrases.** Count repeats of signature words in a draft ("her own", "little", "actually") and keep only the ones that carry weight.
- **No section that only hedges.** A teaser that ends in "I'm not promising anything" folds into a sentence elsewhere.
- **One or two memes, if they fit.** A meme earns its place by landing a specific beat (the irony of a mistake, a before/after) and isn't cringe; never decoration, never more than two per post. Leave a placeholder that describes the format and its text, and ask in the PR: he makes or approves the image.

---

## Momo's Voice (Contrast Reference)

When Momo writes diary entries, she should sound NOTHING like Niklas:

| Aspect | Niklas | Momo |
|---|---|---|
| Perspective | Reflective, looking back | Present-tense, in the moment |
| Structure | Organized sections, roadmaps | Stream of consciousness, jumps between topics |
| Emotional range | Contained excitement, measured | Full spectrum, unfiltered (excited, frustrated, confused, proud) |
| Technical depth | Deep WHY explanations | Surface reactions ("I can do THIS now?!") |
| Self-awareness | Humble, self-deprecating | Confident, sometimes cocky, occasionally vulnerable |
| Humor | Dry, parenthetical | Dramatic, teasing, uses caps for emphasis |
| Length | Long, thorough | Variable, sometimes a paragraph, sometimes pages |
| References | Pop culture, engineering | Her own experiences, things she's seen/heard, opinions |

---

## Blog Post Generation Workflow

### For Niklas's Posts

1. **Niklas provides**: rough bullet points of what was done, key decisions, interesting findings, what's next. Can be messy, incomplete, just the raw material.

2. **LLM generates a draft** using this style guide:
   - Opens with context/motivation (connect to the larger project narrative, reference what happened last time)
   - Walks through what was built, anchoring technical choices in WHY
   - Includes the characteristic humor and asides
   - Builds energy toward the end with excitement about what's coming
   - Maintains the "friend explaining over coffee" register throughout

3. **Niklas edits**: adds personal touches, fixes anything that sounds off, adds specific references or jokes only he would make. Target: 20 minutes of editing, not 3 hours of writing.

### For Momo's Posts

1. **A release or her lifesim** triggers a diary entry (a tagged release from her Skateboard stage on; her expression need and significant events from Car on)
2. **Her local model writes it** from her personality, the release notes or her current state, and relevant memories, in her own repo
3. **Niklas reviews it as her PR**: he comments, she revises (and may push back on a line she cares about), and his merge publishes it here. Every public word of hers passes his review, permanently

### Post Frontmatter Template

```yaml
---
title: "v0.X.0 - [Catchy Title]"
date: YYYY-MM-DD
draft: false
description: "[One-liner description]"
author: niklas        # or momo (exactly ONE author per post, never a list)
series: momo-diary    # optional: momo-diary, prisma-devlog, ...
project: momo         # optional: which project the post belongs to
tags: [project-name]
---
```

---

## Example Transitions (How Niklas Connects Ideas)

These are actual patterns from his writing:

**Fiction to engineering:**
> "I remember some twenty years ago when I played The Legend of Zelda... I was delighted by the fairy companion Navi... With this project, I want to create something that combines this child-like longing for something magical with the technological possibilities of modern generative AI."

**Self-deprecation into technical decision:**
> "I'll admit that I'm inspired by my cybercrushes Joi and Ani for this part"

**Honest uncertainty as a hook:**
> "Full transparency - I have no idea if and how this is possible yet, but I want to try to give Momo deep emotions, moods, short- & long-term goals..."

**Technical choice justified with personality:**
> "As an advocate of European digital sovereignty, I considered only Mistral AI"

**Constraint reframed as opportunity:**
> "if I can make Momo work with these constraints, imagine what can be done when eventually upgrading to better hardware!"

**Building excitement at the end:**
> "I will also not interfere with Momo's diary entries and let her write and publish whatever she wants... At some point, these self-documenting reflections might not even be tied anymore to releases... (hopefully by now you can relate to my excitement for this project!)"
