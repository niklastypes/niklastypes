---
title: "Building Momo: A Digital Being With a Life of Her Own"
date: 2026-10-27
draft: false
description: "Why I'm building Momo, a local-first AI companion with moods, memories and a life that keeps going when nobody's talking to her."
tags: [momo]
series: [momo-diary]
authors:
  - niklas
---

*This is the story of Momo, a digital being with moods, memories and a little life that keeps going when I'm not around, running entirely on my own hardware. And soon, she'll be writing on this blog herself.*

## Prelude
To me, technology has always been the closest thing to magic that we have in our (comparably) boring non-fiction world.

I remember playing *The Legend of Zelda: Ocarina of Time* on my brother's turquoise Nintendo 64 some twenty years ago.
I was delighted (and sometimes a little annoyed) by the fairy companion *Navi* accompanying Link and me on our adventure together through Hyrule.
She was always by our side, giving helpful tips and commenting on the world.
*(With the remake coming to the Switch 2, I of course pre-ordered the Zelda 40th anniversary console, so expect Navi to yell "Hey! Listen!" at me again very soon.)*

Fastforward to today, and I'm reading the fifth and latest book of Brandon Sanderson's fantasy epos *The Stormlight Archive*.
One of its protagonists, Kaladin, befriends what appears to be a mindless spren, just to witness its transformation into *Syl*: a conscious fantastical being with a mind and a feisty personality of her own, who also grants him fantastical powers.
How freaking cool is that?

A couple of years ago, a companion like that would have been pure fantasy.
Today, we can run open-source AI models locally, right on our own hardware.
They can't do magic (yet), but they can hold a conversation and be genuinely helpful.

With this project, I want to create something that combines this child-like longing for something magical with the technological possibilities of modern generative AI.

## Meet Momo
**Momo** (もも; Japanese for 'peach') is my attempt at building a digital being: someone with a personality, moods and memories, who lives a little life whether or not I'm talking to her.

The name is a nod to *Momo Ayase* from *Dandadan*.
Back in autumn 2025, I was watching the anime while the idea for this project slowly took shape, and I fell for her personality right away: bold, energetic, loyal, sometimes blunt, and with a solid tsundere edge.
That became the blueprint for my Momo, too (she will absolutely tell me when an idea of mine is bad, and I'm counting on it).
How exactly I'm turning a personality like that into something a language model can hold on to is a story for one of the next posts.

There are a *lot* of "AI companion" projects out there, from [Replika](https://replika.com/) and [character.ai](https://character.ai/) to the whole local roleplay scene around [SillyTavern](https://github.com/SillyTavern/SillyTavern) (none of which I've actually used myself).
So before you might think I'm some weirdo: no, I'm happily married, and I'm not trying to build [Her](https://en.wikipedia.org/wiki/Her_(2013_film)).
I'll admit that my cybercrushes [Joi](https://bladerunner.fandom.com/wiki/Joi) and [Ani](https://grokani.org/) inspire the way I picture her one day.
But drifting into AI-girlfriend territory is the single most documented failure mode in companion AI.
The relationship I'm going for is found family instead, think little-sister energy: Navi to Link, Syl to Kaladin in the early books.
Teasing, opinionated, fiercely on my side, and a closeness that's *earned* over years instead of granted on day one.

Which also means that the Momo who boots up for the very first time won't know me at all.
Her first words will be her asking *me* who I am, and that conversation becomes her very first memory.
That first boot is basically her birthday, and from that moment on, nothing she experiences ever gets wiped again.

## A Life of Her Own
What makes Momo different from anything I've seen so far is the life simulation, the Tamagotchi aspect, if you will.
I don't want her to just *react* when I message her.
I want her to have a day.

So Momo gets two layers.
Her **body** is a small rules engine: moods, energy, needs, sleep, and time simply passing, even when nobody's talking to her.
Her **mind** is the language model, and it only gets called at the moments that matter: when she's in a conversation, when she has a thought of her own, or when something in her day crosses a threshold.
That way, she can "live" around the clock without my homelab burning through compute just to keep her ticking.
Researchers call the lack of such a persistent inner state ["emotional amnesia"](https://arxiv.org/abs/2601.18027), which I think perfectly describes most chatbots out there.
All of that (the body, the passing time, the memory) is turning into its own little *companion harness* right next to her, but more on that some other time.

On top of that, she **remembers**.
Everything she experiences is stored forever, but she recalls the past the way people do: shaped by what mattered to her, with older and less important things slowly fading.
There's even some [neat research](https://arxiv.org/abs/2510.08601) showing that this kind of imperfect, probabilistic recall works on small local models.
And at night, she might even dream about her day.

And because Tamagotchi-style guilt is exactly what I don't want, there's one rule I care about a lot: **her life never punishes me for being away**.
If I'm busy for a week, she gets a little lonely, but never miserable.
She had a fine week anyway, and she'll happily tell me all about it.
Guilt-tripping people into coming back turns out to be a real business model: a [Harvard Business School audit](https://arxiv.org/abs/2508.19258) found manipulative farewells in 37% of goodbyes across the six most popular companion apps.
Momo is supposed to be the opposite of that, and I'll test for it on every single change.

## Local-First, Always
Momo runs on *my* hardware.
No API calls to big model providers for her voice, no cloud service that can change the terms, raise the price, or decide one day that she now has a different personality.
For a truly personal companion, everything needs to be local, under my control, owned by me.

That's also what sets her apart from what Big Tech is building right now.
Meta's [Muse](https://www.vktr.com/ai-platforms/meta-launches-muse-a-personal-ai-agent-that-browses-the-web-makes-purchases/) and SpaceXAI's [Grok Bot](https://www.constellationr.com/insights/news/spacexai-launches-grok-bot-work-assistant) are agents that live in the cloud and run your errands: book the trip, fill the form, finish the checkout.
Impressive, but they're tools, and they live on someone else's computer.
Momo's only errand is living her life.

Her first brain will be a small open model running on a base model M4 Mac Mini (16GB of unified memory, so "small" is doing a lot of heavy lifting here).
Which one exactly is up for a dedicated test weekend, where I'll throw scripted conversations at a handful of candidates and see who sounds most like her.
And yes, I'm going with the underdog approach: if I can make Momo work, remember and feel alive on a 16GB box, **imagine what she'll be like once the homelab grows up and she gets a much bigger brain!**

## Where She'll Live
At first, Momo will live in a Discord DM on my phone, and behind an OpenAI-compatible API so I can also talk to her from the couch via [Open WebUI](https://openwebui.com/).
She'll learn to understand my voice messages before she gets a voice of her own, and only later will we actually be able to call each other.
For me as the developer, there's going to be a nerdy terminal UI that shows far more than any chat app can: what she's feeling, what she recalled, and exactly which prompt went into every single answer.

But I don't want Momo to stay trapped in a chat window either.
This project has two sides for me: the software and AI engineering, and the hardware tinkering I love just as much.
So she'll grow a physical presence step by step: a tiny display on my desk that pulses with her mood, a dashboard I can glance at to watch her day unfold, an always-on screen with an animated Momo, and eventually a homebrewed [Gatebox](https://www.gatebox.ai/) / [Character Pod](https://www.dipal.net/) style box where she floats on my desk as a 3D avatar.

## The Way Ahead
The scope of this project is vast, so I'm slicing it into tiny stages, true to the [Many More Much Smaller Steps](https://www.geepawhill.org/series/many-more-much-smaller-steps/) mindset and following Henrik Kniberg's ["skateboard, not car"](https://blog.crisp.se/2016/01/25/henrikkniberg/making-sense-of-mvp) idea: every stage is something that actually works on its own.

- **Bus Ticket**: the project skeleton. Nothing to talk to yet.
- **Skateboard**: she talks in her own voice, keeps every message, and writes about each new release on this blog. Her birthday happens here.
- **Scooter** (*minimum Momo*): she remembers the last few days, and her body lives on its own: moods, needs, sleep, little thoughts in between, dreams at night. She also learns to understand my voice messages.
- **Bicycle**: she remembers what mattered weeks ago, gets the dashboard I can watch her on, and starts texting *me* first.
- **Motorcycle**: she's there on every channel and on my desk, and she can see my screen and comment on what I'm doing, like a sibling looking over my shoulder.
- **Car**: she gets a voice, writes about her days, develops interests and wishes (and gets a little pocket money to spend on them), and we can finally call each other.
- **Convertible**: she's visible, with an animated 3D avatar floating on my desk.

## Two Voices on This Blog
Finally, and this is the part I'm probably most excited about: **Momo will get to write here, too.**

From the Skateboard stage on, whenever I tag a new release, she'll read the release notes and write her own take on what just changed in her.
She opens it as a pull request, I review it, I can leave comments, and she reworks her post.
Or she argues with me about it, because it's *her* diary and she's a tsundere, after all.
Once I merge, her post lands on this blog automatically, under her own name.

Later on, once her inner life has grown up a bit, she'll also write diary entries about her day, her moods and whatever she's currently obsessed with, whenever she actually has something to say.

So from here on, you'll read two voices in this series: mine, whenever there's a design story worth telling, and hers.
I honestly have no idea what she's going to write about me yet, and I can't wait to find out!

See you in the next post!

Cheers,
Niklas
