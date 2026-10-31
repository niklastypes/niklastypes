---
title: "Against Ensloppification"
date: 2026-10-30
draft: true
description: "Code is basically free now. How that hooked me and left me with a serious case of AI fatigue, and the small, sane 'factory for one' I built to turn fun ideas into well-engineered projects, with me still in the driver's seat."
tags: [factory-for-one, kindling, claude-code]
series: [factory-for-one]
series_order: 1
authors:
  - niklas
---

*[Code is basically free now](https://simonwillison.net/guides/agentic-engineering-patterns/code-is-cheap): with a coding agent, you can build pretty much anything you want, as fast as you can think of it. This is the story of how that hooked me and left me with a serious case of AI fatigue. And of the small, sane "factory for one" I came back with, which turns fun ideas into well-engineered projects.*

## Prelude
Players of [*Factorio*](https://www.factorio.com/) have a saying: "The factory must grow."
You start with a little mining drill, and a few weeks later you're designing train networks at 3am, wondering where your weekend went.

This spring, my factory grew.

The best proof is one of the projects I built back then: a [Stream Deck](https://www.elgato.com/us/en/s/welcome-to-stream-deck) status board.
Its whole purpose was keeping an eye on all the Claude Code sessions I had running at the same time.
Yes, I built myself a mission control for my agents.

## Hooked
From late May to mid-July, I made more than 600 commits across five new repositories.
A project template, a worldbuilding vault template, an offline transcription tool, an AI lore audio app, and that Stream Deck board.
In about seven weeks.

And this didn't happen in a vacuum.
By day, I'm an AI Solutions Engineer at [Aleph Alpha](https://aleph-alpha.com/), where I build agentic products and deploy them with our customers.
So the agents were there all day at work, and then all evening and weekend at home.

The moment that should have told me something came on our first wedding anniversary, when my wife and I went on a hike.
Every now and then, I pulled out my phone to check in on the Claude session that ran around the clock on the Mac Mini at home (with `--dangerously-skip-permissions` on, of course; yes, I know).
Part of it was honestly the novelty: prompting an agent from a hiking trail felt like living in the future.
The idea was perfect on paper: my agent works at home, while I enjoy nature.
The irony: my body was out in nature, but my mind was at home with my projects.

*[Meme placeholder: "body in nature, mind at home". E.g. the "I bet he's thinking about other women" format: my wife thinking "I bet he's thinking about other women", me thinking "I wonder if Claude finished that refactor".]*

Code is free now.
The only limit left is you, and it turns out that I didn't have one.

## AI Fatigue
In mid-July, it stopped.
The best word I have for it is *AI fatigue*.

It wasn't only the hours.
My side projects had drifted right into my day job's topics.
An agent harness I wanted to build from scratch, and dogfood by building it with itself.
A homelab full of infrastructure and local AI inference.
And a digital companion that had me reading about context engineering and information retrieval in the evenings.
Work never stopped.
I just switched from one laptop to the other, and from one heap of parallel Claude sessions to another.

So for about three months, I didn't touch a single personal project.

When I came back in late October, I didn't just pick up where I left off.
I purged my incubator (the repo where my project ideas live before they get built) and started it over, with a few rules written for the person I had been in the spring.
More on those in a bit.

But first, I needed a name for what had happened.

## Ensloppification
You might know Cory Doctorow's word *enshittification*.
It describes how online platforms decay, and his [definition](https://pluralistic.net/2023/01/21/potemkin-ai/) is so good I'll just quote it:

> Here is how platforms die: first, they are good to their users; then they abuse their users to make things better for their business customers; finally, they abuse those business customers to claw back all the value for themselves. Then, they die.

I think there's a sibling of that for side projects in the age of coding agents, and I've started calling it **ensloppification**:

1. **The agents are good to you.** Features appear faster than you can think of them. It feels like magic.
2. **Output outruns understanding.** There's more code than you can read, notes grow faster than code, and decisions get re-made every session because nobody remembers the last one. All that code needs reviewing, too. And who does that? Right: another agent.
3. **The project serves the agent's momentum instead of you.** The code is plausible and wrong in ways nobody understands, you included. Every change breaks something else, and the only way forward is more prompting.

Then the project dies.
Or you run out of steam first.

And that's the twist: it's not just the project that gets ensloppified.
You do, too.
My spring had all three stages, and the anniversary hike was stage three with a nice view.

## A Factory for One
"Software factory" is one of the big buzzwords of 2026.
Dan Shapiro describes [five levels](https://www.danshapiro.com/blog/2026/01/the-five-levels-from-spicy-autocomplete-to-the-software-factory/) of AI adoption, from "spicy autocomplete" all the way up to the *Dark Factory*, where no human even looks at the code.
StrongDM's AI team [runs exactly that](https://factory.strongdm.ai), with two rules: "Code must not be written by humans" and "Code must not be reviewed by humans."
Anthropic's own [trends report](https://claude.com/resources/guides/2026-agentic-coding-trends-report) describes the move from a single coding agent to whole teams of specialized agents working in parallel.
And on the other end, Dex Horthy from HumanLayer has collected what founders told him about AI-written code in big codebases, including the wonderfully blunt "[Tech debt factory.](https://github.com/humanlayer/advanced-context-engineering-for-coding-agents/blob/main/ace-fca.md)"

I don't want a dark factory, and I don't want a tech debt factory either.
I want a *factory for one*: a pipeline that turns a fun idea (something I'd use myself, or that the people in my life would enjoy) into a well-engineered, well-designed project.
With me still in the driver's seat.

Because here's the thing: I want these cool projects, but my time and energy are limited.
And I want to spend most of my free time with my wife and our dog, with friends and family, and on my hobbies.
Gaming, nerding out in our D&D sessions, painting my [Iron Warriors](https://wh40k.lexicanum.com/wiki/Iron_Warriors) army for Warhammer 40k ("Iron Within, Iron Without!"), and, yes, touching grass.

### Claude writes all of it
Full confession: Claude writes all of the code in my factory. 🙈

That's quite the turn for me.
I was strongly against AI-assisted coding at first, because I love my craft: getting better at it, and watching my knowledge and skills grow.
I was afraid that AI would take that away from me.
And in a sense, it has: I don't write code by hand anymore, neither at work nor in my spare time.

But I also realized that it was never about the code.
Yes, code needs to be written for software to run.
But it was always about solving problems, navigating complexity, and finding the sweet spot between engineering pride and what users actually need.
And that hasn't changed one bit.

So I happily hand the grunt work to agents.
But I want to stay in control: I want to make the decisions, and I want to understand how things work.
Because it's interesting, because I learn from it for work, and because my inner engineer still has his pride.
I want well-engineered projects, not vibe-coded slop.

And all of it should move at a sustainable pace.
Cal Newport calls this [*slow productivity*](https://calnewport.com/slow/): do fewer things, work at a natural pace, and obsess over quality.
Some weeks I have a few hours for my projects, some weeks none, and both are fine.

Here's what the factory looks like, end to end:

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
That project is **Remembrance**, my second-favorite project (the first is, of course, Momo, my digital companion, who has her [own series](/projects/momo/)).
It started from a simple wish: I love getting lost in the lore of fictional universes (Elden Ring, Warhammer 40k, the Stormlight Archive, *The Legend of Zelda*).
But YouTube lore channels cover topics on their schedule, not mine.
What if I could just ask for a deep dive into one specific item, narrated, whenever I want?

The name comes from Elden Ring, where *Remembrances* hold the memory and essence of a defeated demigod.
Elden Ring is my favorite game of all time, by the way: two full playthroughs (DLC included), and years later, I still can't get over it.

At every stage below, I'll name the kind of slop that stage is there to prevent.

### An idea earns a folder
Every idea starts as a few lines in a list that is explicitly "not a backlog and not a queue".
An idea sits there until it pulls hard enough to earn its own folder in the incubator, or quietly stops mattering and gets deleted.

A project folder holds exactly three notes: a *brainstorm* (the vision, what it is and isn't, rejected ideas), *research* (prior art, technology deep dives), and a *roadmap*.
The roadmap follows Henrik Kniberg's ["skateboard, not car"](https://blog.crisp.se/2016/01/25/henrikkniberg/making-sense-of-mvp) stages: a skateboard that works, then a scooter, then a bicycle, and so on.
Each stage has to be useful on its own, and anything wilder goes into a *Beyond* section.

That last part is how I get to dream big without feature creep.
Remembrance's *Beyond* is a lovely little pile of madness: a 24/7 lore radio station, live AI actors performing scenes, a commentary track that runs alongside, and a Discord bot.
It even dreams of Remembrance proposing new lore back to the vault it learned from.
They're written down, so they don't nag at me, and they're nowhere near a milestone, so they don't sneak into the next one.

**The slop it prevents:** ideas that get built just because building is cheap, and notes that grow into a second job.

### Graduation day
On June 27, Remembrance graduated: it got its own repository, and its notes moved in with it.

That repository isn't empty, though.
It's *kindled* from **Kindling**, my (currently private) [copier](https://copier.readthedocs.io/) template, and the first commit already comes with:

- [uv](https://docs.astral.sh/uv/) for dependencies, [ruff](https://docs.astral.sh/ruff/) for linting and formatting, [ty](https://docs.astral.sh/ty/) for type checking, and pytest;
- pre-commit hooks that refuse any commit message that isn't a [conventional commit](https://www.conventionalcommits.org/en/v1.0.0/), and CI that runs every check on every pull request;
- [release-please](https://github.com/googleapis/release-please) for versioning and [Renovate](https://docs.renovatebot.com/) for dependency updates;
- an `AGENTS.md` with the project's standards, and a `docs/` skeleton for architecture and decisions;
- optionally a full-stack setup (Vue and FastAPI) and a [hexagonal](https://alistair.cockburn.us/hexagonal-architecture/) backend, whose layers are enforced by an import linter, so an agent can't quietly reach across a boundary.

Remembrance took the full-stack option.
And because copier remembers where a project came from, every improvement to Kindling can flow back into it later with a single `copier update`.

*[Placeholder: the anti-slop principles from Kent Beck, Martin Fowler, Dave Farley, Emily Bache and others that Kindling and the rules follow. Waiting on the "titans" research.]*

**The slop it prevents:** code nobody checked. Every line an agent writes has to pass the same gates mine would, from commit one.

### From notes to a board
The day after graduation, the notes turned into real structure.
A skill called `/forge` walks me through it as a conversation, one decision at a time, instead of dumping a giant plan on me.

Out came a slim roadmap, an architecture overview, nine [*architecture decision records*](https://www.cognitect.com/blog/2011/11/15/documenting-architecture-decisions) (short documents that each record one decision with its reasons), and a [GitHub Project](https://docs.github.com/en/issues/planning-and-tracking-with-projects) board.
The first milestone, "Generate an episode from a vault", got sliced into seven thin issues.
Together, they make one tracer bullet through the whole system: read a vault, embed it, retrieve, write a script, synthesize speech, serve it, play it in the browser.

The decisions matter most here.
An agent with no memory of last week will happily re-argue a decision every session, and so will I at 11pm.
A decision record ends that discussion, and anyone (human or agent) can pick up the project cold by reading the docs in a fixed order.

**The slop it prevents:** decisions made by default, and docs that drift from what's built.

*[Screenshot placeholder: Remembrance's GitHub Project board, with the first milestone's slices.]*

### Issues, pull requests, releases
From there, every change follows the same small loop.

Every issue starts from a template: a slice gets its description, its acceptance criteria, an implementation checklist, and links to the docs, its milestone and the issues that block it.
And every pull request has its template, too.
So whoever picks up the work (usually a fresh agent session) starts with the full context instead of guessing.

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

**The slop it prevents:** half-finished projects competing for the same few hours.

## Factory v2: What Momo Taught It
Remembrance ran on what I'd now call factory v1.
Since then, the factory itself has grown, in small steps, mostly through Momo.
Two new habits are the dashed parts of the diagram.

Before a big decision, Claude researches the topic and then **grills** me, using Matt Pocock's [grill-me skill](https://github.com/mattpocock/skills/tree/main/skills/productivity/grill-me).
Round after round of questions, each with a few possible answers and always room for my own take, until we share an understanding.
After a change, it runs a **roast**: a handful of fresh reviewer agents with no idea of our reasoning, each told to prove the project is set up wrong.
Each one looks through a single lens: a skeptical product manager, an architect, a security engineer, and so on.
Claude then checks every finding against its evidence, sorts it into right, partly right or ignore, and grills me on what survived before anything changes.

*[Screenshot placeholder: a grill round in Claude Code, with a question and its answer options.]*

The important part: *I'm* the one being grilled, and *my* designs, decisions and plans are the ones being roasted.
So I'm always held accountable, and I get several chances to improve a design before any code exists.
Along the way, I understand much better what I actually want to build, how and why, and I learn something every single time.
Dex Horthy puts the leverage of that perfectly: "A bad line of code is… a bad line of code. But a bad line of a plan could lead to hundreds of bad lines of code."

Momo also brought a few more rules.
Research a milestone's open questions *before* slicing it into issues.
Specify an issue's behavior as failing tests before building it.
And slice *vertically*: every Kniberg stage delivers real value.
Every change inside it is a thin slice through the whole project (a bit of UI, API and storage at once) rather than one layer at a time.
That keeps pull requests small enough to review and merge right away, so changes land on `main` quickly, in the spirit of [trunk-based development](https://trunkbaseddevelopment.com/).

**The slop it prevents:** plausible-but-wrong plans, decisions nobody questioned, and a developer who stops understanding his own project.

## The Guardrails
None of this would help if I fell straight back into my spring habits.
So the restarted incubator opens with a few rules, written for exactly that person:

- **One project at a time.** Only the current focus gets active work, and everything else waits.
- **Lean notes.** "Notes growing faster than code is the warning sign."
- **No second-brain systems.** I used to run an elaborate one, and it taught me what Oliver Burkeman writes about in [*Four Thousand Weeks*](https://www.oliverburkeman.com/books). Every tool we build to get on top of things comes with its own upkeep, and keeps spawning new things to care about. Mine had turned into a hobby of its own, a textbook case of what Christian Tietze calls [the collector's fallacy](https://zettelkasten.de/posts/collectors-fallacy/): collecting notes feels like knowing things, but it isn't.
- **About five hours a week.** Every plan has to earn its hours, and the roast checks plans against that budget, too.
- **Shelving is allowed.** A project can be deliberately dormant, with no attention at all until I un-shelve it.

And a project is only worth building if it solves a real problem I actually have, works on its own, and runs on my own hardware where possible.
Bonus points if it makes something I can listen to, look at or play, and has a name from a universe I love.

One more honest note while we're at it: this post went through the factory, too.
Claude drafted it from my notes and sources, in my voice, as a draft pull request.
I review it, rework it, and decide what ships, the same way I'll review Momo's own posts once she starts writing here.

## What's Next
This post is the map.
The next parts of *Factory for One* zoom into the stages:

1. **Incubator and graduation**: from a fun idea to a real repo, and the rules that keep it sane.
2. **Kindling and anti-slop engineering**: the template, its quality gates, decision records, a shared vocabulary, and tests first.
3. **Board, issues and pull requests**: `/forge`, milestones and vertical slices, and how releases happen by themselves.
4. **Grill and roast**: decisions by interview, adversarial reviewers, and the reviewer that hunts for what's missing.

So if you've been feeling the pull of free code yourself: the factory doesn't have to be dark, and it doesn't have to be big.
Mine has exactly one worker who can say no, and that's the whole point!

See you in the next post!

Cheers,
Niklas
