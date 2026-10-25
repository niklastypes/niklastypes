# Writing Style

> Reference for generating blog post drafts. Used by LLMs to pre-generate posts that need only light editing. Also serves as a contrast reference for Momo's distinct voice.

---

## Niklas's Voice

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
- Never uses em dashes

### What Niklas Does NOT Sound Like
- Corporate/professional blog voice ("In this article, we will explore...")
- AI-generated slop ("Let's dive in!", "In today's fast-paced world...")
- Tutorial tone ("Step 1: Open your terminal...")
- Dry technical documentation
- Overly polished or edited, his writing has a natural, slightly rough quality

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
