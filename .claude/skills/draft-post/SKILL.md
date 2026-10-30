---
name: draft-post
description: Draft a blog post for niklastypes.xyz in Niklas's voice and open it as a draft PR for his tweaks. Use when asked to write, draft or revise a post (about Momo, Arasaka, or any topic), or when Niklas comments on a draft-post PR.
---

# Draft a post

Niklas publishes, you write. He gives a topic and points at source material; you hand back a post that needs only fine tweaks, as a draft PR. Momo writes her own entries through her own pipeline (`docs/roadmap.md` → Momo's Diary): this skill writes only Niklas's posts.

## 1. Gather the story

Read every source he points at in full: repo notes (`~/Developer/<repo>/notes/` or `docs/`), PRs and issues via `gh`, changelogs, earlier posts. The incubator lives on his private Gitea and is cloned at `~/Developer/incubator`.

Done when you can state, in one line each: the **motivation** (why this matters to him), **what** happened or is planned, **why** those choices, and **what's next**. Each line traces to a source. A gap you can't fill from the sources goes on the open-questions list for the PR, never into the post as invention. Facts about his life and setup are as strong as the source says and no stronger: owning isn't using.

## 2. Load his voice

Read `docs/writing-style.md` and every file in `docs/voice-samples/` in full, every time; the samples are the ground truth, the style guide the distillation. Notice the pop-culture openings, the parentheticals, the warm-up from measured to excited, the WHY over the WHAT. **What Goes Into a Post** in the style guide is the distilled feedback from his reviews: treat it as rules. When a sample already says something the new post needs, reuse his sentences rather than paraphrasing them.

## 3. Write the draft

- Shape: context and motivation → what → why those decisions → what's next. Headers organise; the prose inside flows.
- Voice: first person, contractions, rhetorical questions, self-deprecating asides, the occasional German or Japanese word where it fits, plain commas and parentheses for asides (he writes no em dashes).
- Facts: specific and sourced. Names of people other than Niklas stay out unless he asks.
- Links: first-level sources only. A product links its own page (Grok Bot → `https://x.ai/bot`, not a news article about it), a person their own site, a work its official site, research the paper itself; a third-party article only when it *is* what's cited (a review's take, a reported audit). Fan wikis or Wikipedia only where no official page exists (Navi, Syl, a concept like *tsundere*). Link what a reader might not know, once, at first mention; household names (Discord, a Mac Mini) stay unlinked. Click-check every link before handing over.
- Length: as long as the story needs; his posts run long and thorough.

Place it where the site's existing posts live: under `content/projects/<project>/posts/<slug>.md` today (a project with no section yet gets an `_index.md` landing page too), following the frontmatter of the newest posts there, with `draft: true`, `authors: [niklas]`, and for Momo posts `series: [momo-diary]` plus `series_order` (the next number in the series; Blowfish shows "Part :" without it). Once the Astro migration has landed, follow its content schema in `docs/research.md` instead.

Done when the draft passes the "What Niklas Does NOT Sound Like" and "What Goes Into a Post" lists in `docs/writing-style.md` line by line, and `hugo --buildDrafts` builds cleanly.

## 4. Hand it over

On a branch `post/<slug>`, commit as `docs: draft "<title>"` and open a PR whose description holds:

- the one-line story (motivation, what, why, next);
- the sources used;
- the open questions, each pinned to the paragraph it affects;
- the visuals: each diagram in the draft, and each screenshot or meme placeholder with what to capture or make;
- how to publish: tweak, flip `draft: false`, merge.

Done when the PR is open and its checks are green.

## 5. Revise on review

When he comments on the PR, rework each commented passage in his voice, push to the same branch, and answer every comment with what changed. His wording wins over yours wherever he wrote any. Apply a comment's reason everywhere it holds, not only on the commented line, and say so in the reply.

Done when every comment has a reply, and every lesson that would apply to future posts (not just this one) has been added to "What Goes Into a Post" in `docs/writing-style.md`, in its own PR.
