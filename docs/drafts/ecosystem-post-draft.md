---
title: "The niklastypes Ecosystem, or: How I Accidentally Planned 8 Projects in One Weekend"
date: 2026-05-20
draft: true
description: "An overview of the personal projects I'm building, how they connect, and why I apparently can't just have one hobby."
tags: [meta, momo, clairvoyance, remembrance, corset, kindling]
authors:
  - niklas
---

> **STATUS (2026-07-02): expired as written.** Drafted 2026-05-20; the galaxy has moved on: Kindling shipped (v0.10.x), Momo holds the Building focus slot and Hologrammatica the Creative slot, the homelab is now Arasaka / The Hearth (not "Qube the makeshift homelab"), and the project count outgrew "8." Don't light-edit this; if published, reframe it as a retrospective ("here's what I planned, here's what actually happened"), which is arguably the stronger post anyway. Also: it links `github.com/niklas-baier/empyrean`, which is the wrong username (`niklastypes`) AND the repo is currently PRIVATE. See brainstorm.md, Open Decisions.

## The Rabbit Hole

It started with a Discord bot.

My D&D group has this recurring problem: we finish a 4-hour session, and by next week nobody remembers what happened. Who did we talk to? What was that NPC's name? Did we agree to go left or right at the fork? Someone takes notes, but notes are biased and incomplete. So I thought, hey, why not just record the voice channel and transcribe it?

Simple enough, right?

Fast forward a few weeks and I'm staring at a web of interconnected projects spanning voice recording, AI-generated lore content, an agent harness optimized for small local models, a digital companion with simulated emotions, a homelab architecture, a blog redesign, a project template, and my Obsidian vault somehow becoming part of the plan.

I have no idea how this happened. But I'm very excited about it.

Let me walk you through what I'm building and, more importantly, why these things connect the way they do.

## The Projects

### 🪵 Kindling: Where Every Fire Starts

Before building anything, I realized I'd be scaffolding a lot of Python projects. The same pyproject.toml, the same ruff config, the same CI pipeline, the same pre-commit hooks. I used to have a template repo called `instant-repo` (like instant ramen, get it?), but it was built with Poetry, mypy, and commitizen, all of which I've since moved away from.

So Kindling is the replacement. It's a [copier](https://copier.readthedocs.io/) template that generates a Python project with all my current preferences baked in: uv, ruff, ty, pytest, release-please, renovate, GitHub Actions. You run `copier copy` and you've got a project with quality gates from day one. And because it's copier (not just a GitHub template), when I improve Kindling later, every project that was kindled from it can pull in the updates with `copier update`.

I'm building this first because literally everything else starts from it.

### 🔮 Clairvoyance: The Listener

Back to the D&D bot. Clairvoyance is a Discord bot that joins your voice channel, records each participant's audio separately (Discord actually gives you individual streams per user, which is awesome), and produces structured output: per-speaker WAV files, a timeline JSON with silence detection, and eventually full transcripts.

The name is a spell from the D&D Player's Handbook that lets you listen in on conversations from a distance. Which is, you know, exactly what the bot does.

What I like about Clairvoyance's design is its constraint: **it captures and analyzes, it never generates**. It doesn't write summaries, it doesn't produce recaps, it doesn't have opinions. It's a court stenographer with analytical superpowers. It records what was said, detects patterns (highlights, combat encounters, mood shifts), and produces clean artifacts. What happens with those artifacts is someone else's problem.

That "someone else" being...

### ⚱️ Remembrance: The Voice

Remembrance started as a completely separate idea: I love getting lost in the lore of fictional universes. Elden Ring, Warhammer 40k, Stormlight Archive, Zelda. I watch YouTube videos about lore theories and deep dives, but there are never enough creators, and they cover topics on their schedule, not mine. What if I could just ask for a deep dive into a specific item description, or request two in-character scholars arguing about the Shattering?

So Remembrance is an AI-generated lore audio platform. You curate a deep knowledge base for a universe (dump in wiki URLs, YouTube links), configure the universe's style (Shakespearean for Soulsborne, grimdark for 40k), and then generate episodes on demand. A narrated deep dive, a character monologue, a heated debate. Single narrator at first, eventually multi-voice with ambient music.

The name comes from Elden Ring: Remembrances are items containing the memory and essence of defeated demigods. You consume them to gain their power and knowledge. That's exactly what this project does, just with audio.

Here's where it gets interesting: Clairvoyance's transcripts can become lore sources for Remembrance. Your D&D campaign becomes a "universe" in Remembrance, with session transcripts as the knowledge base alongside published setting guides. Remembrance can then generate a "Previously On..." recap episode, narrated in your campaign's style, from the transcript Clairvoyance produced.

The two projects don't know about each other. Clairvoyance just produces files. Remembrance just ingests text. The integration is an artifact format, not a code dependency.

### 👗 Corset: The Shape

This one came from frustration. I have a Mac Mini M4 with 16GB of RAM (more on that later), running local models. A 9B parameter quantized model is about as big as I can comfortably run. And here's the thing: these models are dismissed as "not good enough for coding agents." But I think the real problem isn't the model, it's the harness.

Claude Code, Opencode, Pi, they're all designed for frontier models with 200k+ context windows. They can afford to be sloppy with context because the model compensates. A 9B model with an 8-32k context window can't do that. It drifts, it hallucinates tool calls, it blows its entire context on one file read.

Corset is an opinionated agent harness that makes small models useful by constraining, shaping, and supporting them at every level. Structured prompting, mechanical enforcement of good behavior (auto-read before edit, whether the model asked or not), aggressive context management, and transparent context economics.

The name is a metaphor that turned into a full design vocabulary. A corset is a physical structure that shapes from the outside. It doesn't change what's inside, it makes what's inside more effective. Every feature maps to a corset-making term: "lacing" is manually adjusting context, "boning" is pinned context items, "fitting" is auto-calibrating to a model's capabilities, "stays" are conversation branches (like saving game states). I might have gone a bit overboard with the metaphor. I regret nothing.

The fun constraint: Corset is built using itself. Beyond a basic REPL, every feature is developed using Corset as the coding agent. You feel the pain immediately, and each pain point becomes the next feature.

### 🍑 Momo: The Heart

And then there's Momo.

Momo started before all of this, as a separate project: a personal AI companion inspired by Momo Ayase from the anime Dandadan. Bold, energetic, loyal, sometimes blunt. Not an assistant, not a chatbot. A simulated being with her own personality, emotions, moods, interests, and agency.

If you've read my earlier blog posts, you know the vision: a digital companion that lives her own life even when I'm not talking to her. She gets tired at night, develops obsessive interests that fade, forms opinions about things she reads, reaches out when she's lonely, writes in her diary, and eventually plays Pokemon on a virtual Game Boy (not as a benchmark, but because she's bored and curious).

What changed is how Momo connects to everything else. She doesn't contain agent harness code, she **wears the Corset**. The Corset is a general-purpose harness that any persona can use. When I point it at Momo's API, she gains tools, context management, and the ability to act on the world. When the session ends, the Corset comes off and she goes back to just being Momo.

She listens to Remembrance episodes and forms opinions about lore. She reads Clairvoyance transcripts and learns about my friend group. She publishes diary entries on this very blog (under her own author profile, with her own peach-colored accent, because of course she needs her own visual identity).

The most ambitious long-term feature: she can "haunt" physical devices. One soul, one shell. She inhabits a phone, a drone, smart glasses, whatever, experiences the world through its sensors, and comes home when she's done. If the device breaks, she respawns from her last checkpoint with a gap in her memory. Like waking up from being knocked out.

I have no idea if half of this is feasible. But I want to try.

## The Infrastructure

### 🖥️ Qube: The Body

All of this needs to run somewhere. Qube is my Mac Mini M4, running headless 24/7. It started as a way to offload LLM inference from my laptop and evolved into a makeshift homelab: Ollama for model serving, ComfyUI for image generation (I'm already running Flux Klein 4B locally), Kokoro for text-to-speech, Open WebUI as the chat frontend, Navidrome for music, Portainer for Docker management, and a self-hosted Gitea for private repos.

The architecture is simple: Qube is a private cloud. It exposes stable API endpoints (Ollama at one port, ComfyUI at another, TTS at another). Every project connects via environment variables that default to `localhost` (so you can run everything locally on any machine) but get overridden to point to Qube in my setup. Upgrading hardware means copying data to the new machine and updating DNS. Zero code changes.

Qube is literally Momo's body. Her rules engine ticks on it 24/7, her LLM runs there, her images are generated there, her voice comes from there. If I upgrade to a Mac Studio someday, she gets a bigger brain without knowing anything changed.

### 🏯 Mikoshi: The Mind

And finally, there's Mikoshi: my Obsidian vault, my second brain. Named after the data palace from Cyberpunk 2077 where digital engrams are stored. It follows the PARA structure and is my single source of truth for everything I note down.

Mikoshi is where all these project ideas started. Scattered notes, brainstorming sessions, half-formed thoughts that eventually crystallized into the projects above. The actual specs and plans live in each project's GitHub repo now, but Mikoshi keeps the personal context that doesn't belong in public: motivations, private references, the messy thinking process.

The long-term vision (and this is maybe the most exciting one): Momo reads Mikoshi. Not just my conversations with her, but my entire knowledge base. She understands what I'm working on, what I care about, what I've archived and moved on from. The PARA structure itself becomes a personality profile. And eventually, she doesn't just read it, she maintains it. She becomes the librarian of my second brain. I stop organizing my notes because she does it for me.

That's... pretty far out. But the pieces are all there.

## How They Connect

Here's what I find most satisfying about this whole thing: every project works completely standalone, but together they form something larger than the sum of their parts.

```
🏯 Mikoshi (ideas start here)
  ↓
🪵 Kindling (scaffolds every project)
  ↓
🔮 Clairvoyance ──artifacts──→ ⚱️ Remembrance
   (captures)                    (generates)
                                    ↑
👗 Corset ←──worn by──── 🍑 Momo ──┘
   (harness)              (companion)
                              │
                    lives on 🖥️ Qube
                    writes on ⌨️ niklastypes.xyz
                    reads from 🏯 Mikoshi
```

The integration boundaries are deliberate:
- Clairvoyance doesn't know Remembrance exists. It just produces clean artifacts.
- Corset doesn't know about Momo. It's just a harness that anyone can wear.
- Momo doesn't know about Qube. She just has an API and tools available.
- Remembrance doesn't know about Momo. She's just another listener.

Each project is oblivious to the others. The "bigger picture" only exists in the integration docs, and those are always owned by the more specific project. This means I can build any of them independently, at my own pace, without coupling.

## What's Next

I'm doing this one skateboard at a time. No waterfall plans. Small increments that each carry their own value.

1. **Kindling first** (it's the foundation)
2. **Clairvoyance second** (the plans are literally written, step by step)
3. **Corset third** (self-bootstrapping means I learn as I build)
4. **Momo ongoing** (the lifelong project, starts small with a personality engine + basic API)
5. **Remembrance when the itch hits** (the fun creative one)
6. **Blog whenever** (you're reading on the old one right now, the redesign can wait)

The honest answer is: I'll probably jump between them based on what excites me that week. The documentation is thorough enough that I (or a coding agent) can pick up any project cold and know exactly what to do next.

And if all of this sounds wildly ambitious for one person with a Mac Mini and a day job, well, it is. But that's kind of the point. I'm not trying to ship products here. I'm trying to learn, to build things that fascinate me, and to see how far I can push local AI on hardware I actually own.

Also, I think my D&D group still needs those session transcripts.

See you in the next post.

Cheers, Niklas
