---
title: "Against Ensloppification"
date: 2026-10-30
draft: true
description: "Code is basically free now. How that hooked me and burnt me out, and the small, sane 'factory for one' I built to turn fun ideas into well-engineered projects without losing myself."
tags: [factory-for-one, kindling, claude-code]
series: [factory-for-one]
series_order: 1
authors:
  - niklas
---

*Code is basically free now: with a coding agent, you can build pretty much anything you want, as fast as you can think of it. This is the story of how that hooked me, burnt me out, and how I came back with a small, sane "factory for one" that turns fun ideas into well-engineered projects.*

## Prelude
Players of [*Factorio*](https://www.factorio.com/) have a saying: "The factory must grow."
You start with a little mining drill, and a few weeks later you're designing train networks at 3am, wondering where your weekend went.

This spring, my factory grew.

On May 20, I sat down to write a blog post about my personal projects.
It was titled "The niklastypes Ecosystem, or: How I Accidentally Planned 8 Projects in One Weekend", and it never got published.
It described a web of projects: a Discord bot that records our D&D sessions, AI-generated lore audio, an agent harness for small local models, a digital companion, a homelab, a project template, a blog redesign.
And right at the top, it said:

> I have no idea how this happened. But I'm very excited about it.

Reading that today is a little like finding an old photo of yourself at a party, right before the night went sideways.

## Hooked
The next day, I started building.
Over the following seven weeks, I made more than 600 commits across five new repositories.
A project template, a worldbuilding vault template, an offline transcription tool, an AI lore audio app, and (my personal favorite in hindsight) a [Stream Deck](https://www.elgato.com/us/en/s/welcome-to-stream-deck) status board.
For keeping an eye on all the Claude Code sessions I had running at the same time.

Some of it turned out great: I use the transcription tool almost every day.
But AI is also what I work with all day at my day job, so there was no off switch anymore.
Work was agents, and my free time was more agents.

The moment that should have told me something: on our first wedding anniversary, my wife and I went on a hike.
And during that hike, I was on my phone, chatting with the Claude session that ran around the clock on the Mac Mini at home.
With `--dangerously-skip-permissions` on, of course.
(Yes, I know. On both counts.)

Code is free now.
The only limit left is you, and it turns out that I didn't have one.

## The Crash
In mid-July, it stopped: I was burnt out.
For about three months, I didn't touch a single personal project.
Remembrance, the lore audio app, had shipped its first milestone on July 10 and then simply sat there.

When I came back in late October, I didn't pick up where I left off.
I purged my incubator (the repo where my project ideas live before they get built) and started it over, with rules written for the person who had just burnt out.
More on those in a bit.

But first, I needed a name for what had happened.

## Ensloppification
You might know Cory Doctorow's word *enshittification*.
It describes how online platforms decay, and his [definition](https://pluralistic.net/2023/01/21/potemkin-ai/) is so good I'll just quote it:

> Here is how platforms die: first, they are good to their users; then they abuse their users to make things better for their business customers; finally, they abuse those business customers to claw back all the value for themselves. Then, they die.

I think there's a sibling of that for side projects in the age of coding agents, and I've started calling it **ensloppification**:

1. **The agents are good to you.** Features appear faster than you can think of them. It feels like magic.
2. **Output outruns understanding.** There's more code than you read, notes grow faster than code, decisions get re-made every session because nobody remembers the last one, and the docs quietly drift away from reality.
3. **The project serves the agent's momentum instead of you.** The code is plausible and wrong in ways nobody understands, you included. Every change breaks something else, and the only way forward is more prompting.

Then the project dies.
Or you burn out first.

And that's the twist: it's not just the project that gets ensloppified.
You do, too.
My spring had all three stages, and the anniversary hike was stage three with a nice view.

## A Factory for One
"Software factory" is one of the big buzzwords of 2026.
Dan Shapiro describes [five levels](https://www.danshapiro.com/blog/2026/01/the-five-levels-from-spicy-autocomplete-to-the-software-factory/) of AI adoption, from "spicy autocomplete" all the way up to the *Dark Factory*, where no human even looks at the code.
StrongDM's AI team [runs exactly that](https://factory.strongdm.ai), with two rules: "Code must not be written by humans" and "Code must not be reviewed by humans."
And Anthropic's own [trends report](https://claude.com/resources/guides/2026-agentic-coding-trends-report) describes the move from a single coding agent to whole teams of specialized agents working in parallel.

Impressive, all of it.
But I don't want a dark factory.
I want a *factory for one*: a pipeline that turns a fun idea (something I'd use myself, or that the people in my life would enjoy) into a well-engineered, well-designed project.

Claude writes most of the code in mine, too.
The difference is where I sit: at every decision.
Agents do the legwork (research, scaffolding, building, reviewing), and I decide what gets built, how, and when to stop.
And it runs on a hard budget of about five hours a week, with my sanity as a non-negotiable requirement.

Here's what that looks like, end to end:

{{< mermaid >}}
flowchart TB
  idea["Idea<br/><i>a few lines in a list</i>"] --> inc["Incubator<br/><i>brainstorm · research · roadmap</i>"]
  inc -->|graduates| repo["New repo from Kindling<br/><i>quality gates from commit one</i>"]
  repo --> forge["Docs, decisions, board"]
  forge --> issue["Issue"] --> pr["Pull request"] --> rel["Release"]
  rel -->|next slice| issue
  grill(["Grill"]) -.-> forge
  rel -.->|milestone done| roast(["Roast"])
  roast -.-> forge
{{< /mermaid >}}

The dashed parts are newer, and I'll get to them.
Let's follow one real project through the solid ones.

## One Idea, End to End
That project is **Remembrance**, my second-favorite project.
It started from a simple wish: I love getting lost in the lore of fictional universes (Elden Ring, Warhammer 40k, the Stormlight Archive, Zelda), but YouTube lore channels cover topics on their schedule, not mine.
What if I could just ask for a deep dive into one specific item, narrated, whenever I want?
(The name comes from Elden Ring, where *Remembrances* hold the memory and essence of a defeated demigod.)

At every stage below, I'll name the kind of slop that stage is there to prevent.

### An idea earns a folder
Every idea starts as a few lines in a list that is explicitly "not a backlog and not a queue".
An idea sits there until it pulls hard enough to earn its own folder in the incubator, or quietly stops mattering and gets deleted.

A project folder holds exactly three notes: a *brainstorm* (the vision, what it is and isn't, rejected ideas), *research* (prior art, technology deep dives), and a *roadmap*.
The roadmap follows Henrik Kniberg's ["skateboard, not car"](https://blog.crisp.se/2016/01/25/henrikkniberg/making-sense-of-mvp) stages: a skateboard that works, then a scooter, then a bicycle, and so on.
Each stage has to be useful on its own, and anything wilder goes into a *Beyond* section.

That last part is how I get to dream big without feature creep.
Remembrance's *Beyond* includes a 24/7 lore radio stream and live AI actors.
They're written down, so they don't nag at me, and they're nowhere near a milestone, so they don't sneak into the next one.

**The slop it prevents:** ideas that get built because building is cheap, and notes that grow into a second job.

### Graduation day
On June 27, Remembrance graduated: it got its own repository, and its notes moved in with it.

That repository isn't empty, though.
It's *kindled* from **Kindling**, my (currently private) [copier](https://copier.readthedocs.io/) template, and the first commit already comes with:

- [uv](https://docs.astral.sh/uv/) for dependencies, [ruff](https://docs.astral.sh/ruff/) for linting and formatting, [ty](https://docs.astral.sh/ty/) for type checking, and pytest;
- pre-commit hooks that refuse a commit message that isn't a conventional commit, and CI that runs every check on every pull request;
- [release-please](https://github.com/googleapis/release-please) for versioning and [Renovate](https://docs.renovatebot.com/) for dependency updates;
- an `AGENTS.md` with the project's standards, and a `docs/` skeleton for architecture and decisions;
- optionally a full-stack setup (Vue and FastAPI) and a backend whose layers are enforced by an import linter, so an agent can't quietly reach across a boundary.

Remembrance took the full-stack option.
And because copier remembers where a project came from, every improvement to Kindling can flow back into it later with a single `copier update`.

*[Placeholder: the anti-slop principles from Kent Beck, Martin Fowler, Dave Farley, Emily Bache and others that Kindling and the rules follow. Waiting on the "titans" research.]*

**The slop it prevents:** code nobody checked. Every line an agent writes has to pass the same gates mine would, from commit one.

### From notes to a board
The day after graduation, the notes turned into real structure.
A skill called `/forge` walks me through it as a conversation, one decision at a time, instead of dumping a giant plan on me.

Out came a slim roadmap, an architecture overview, nine *architecture decision records* (short documents that each record one decision with its reasons), and a [GitHub Project](https://docs.github.com/en/issues/planning-and-tracking-with-projects) board.
The first milestone, "Generate an episode from a vault", got sliced into seven thin issues.
Together, they make one tracer bullet through the whole system: read a vault, embed it, retrieve, write a script, synthesize speech, serve it, play it in the browser.

The decisions matter most here.
An agent with no memory of last week will happily re-argue a decision every session, and so will I at 11pm.
A decision record ends that discussion, and anyone (human or agent) can pick up the project cold by reading the docs in a fixed order.

**The slop it prevents:** decisions made by default, and docs that drift from what's built.

*[Screenshot placeholder: Remembrance's GitHub Project board, with the first milestone's slices.]*

### Issues, pull requests, releases
From there, every change follows the same small loop.
Pick an issue with no open blockers, branch, build it in atomic conventional commits, and open a pull request that says `Fixes #N`.
The board moves the issue along by itself, and merging closes it.

Then release-please takes over: it reads the conventional commits, bumps the version accordingly and writes the changelog.
Remembrance went from v0.2.0 on June 30 to v0.8.0 on July 10, and the last of those releases closed the first milestone.

Looking back, those two weeks show both sides of my spring at once.
The factory worked beautifully.
And I didn't stop.

**The slop it prevents:** piles of changes nobody can review, and releases nobody can explain.

### Pausing without guilt
And then Remembrance paused, right after its first milestone, and it's still paused today.

That's on purpose now: only one project gets the focus at any time, and everything else waits without guilt.
Remembrance's board, docs and roadmap are all still there, with the next milestone half sliced.
When it's its turn again, a fresh session (or a fresh me) can pick it up from the docs alone.

**The slop it prevents:** five half-finished projects competing for the same five hours.

## Factory v2: What Momo Taught It
Remembrance ran on what I'd now call factory v1.
Since then, the factory itself has grown, in small steps, mostly through Momo, my digital companion (she has her [own series](/projects/momo/)).
Two new habits are the dashed parts of the diagram.

Before a big decision, Claude researches the topic and then **grills** me: rounds of questions, each with a recommended answer, until we share an understanding.
And after a change, it runs a **roast**: a handful of fresh reviewer agents with no idea of our reasoning, each told to prove the project is set up wrong.
Each one looks through a single lens: a skeptical product manager, an architect, a security engineer, and so on.
Claude then checks every finding against its evidence, sorts it into right, partly right or ignore, and grills me on what survived before anything changes.

*[Screenshot placeholder: a grill round in Claude Code, with a question, its options and the recommended answer.]*

Two more rules came from Momo: research a milestone's open questions *before* slicing it into issues, and specify an issue's behavior as failing tests before building it.

**The slop it prevents:** plausible-but-wrong plans, and decisions nobody questioned.

## The Guardrails
None of this would help if I fell straight back into the spring.
So the restarted incubator opens with a few rules, written for exactly that person:

- **One project at a time.** Only the current focus gets active work, and everything else waits.
- **Lean notes.** "Notes growing faster than code is the warning sign."
- **No second-brain systems.** No knowledge-base upkeep, no elaborate note-taking methods, because "that kind of overhead fed the 2026 burnout".
- **About five hours a week.** Every plan has to earn its hours, and the roast checks plans against that budget, too.
- **Shelving is allowed.** A project can be deliberately dormant, with no attention at all until I un-shelve it.

And a project is only worth building if it solves a real problem my wife or I actually have, works on its own, and runs on my own hardware where possible.
Bonus points if it makes something I can listen to, look at or play, and has a name from a universe I love.

One more honest note while we're at it: this post went through the factory, too.
Claude drafted it from my notes and sources, in my voice, as a draft pull request.
I review it, rework it, and decide what ships, the same way I'll review Momo's own posts once she starts writing here.

## What's Next
This post is the map.
The next parts of *Factory for One* zoom into the stages:

1. **Incubator and graduation**: from a fun idea to a real repo, and the rules that keep it sane.
2. **Kindling and anti-slop engineering**: the template, its quality gates, decision records, a shared vocabulary, and tests first.
3. **Board, issues and pull requests**: `/forge`, milestones and slices, and how releases happen by themselves.
4. **Grill and roast**: decisions by interview, adversarial reviewers, and the reviewer that hunts for what's missing.

The factory is still growing, slowly this time, and on purpose.
And honestly?
It's the most fun I've had building things in years, *because* it doesn't eat me anymore.

So if you've been feeling the pull of free code yourself: the factory doesn't have to be dark, and it doesn't have to be big.
Mine has exactly one worker who can say no, and that's the whole point!

See you in the next post!

Cheers,
Niklas
