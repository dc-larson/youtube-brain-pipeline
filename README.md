# YouTube Brain Pipeline

Turn a YouTube channel or playlist into a **"brain"**: a structured, source-tagged knowledge base you can actually query, instead of 90 videos you'll never rewatch.

## What this is

A small, repeatable pipeline built with [Claude Code](https://code.claude.com) that:

1. **Pulls captions** for every video in a channel or playlist with `yt-dlp` (text only, no video downloads).
2. **Cleans** them into plain-text transcripts with an index of titles, dates, and links.
3. **Extracts** claims, rules, and frameworks one video at a time, tagging each with its source video and date.
4. **Synthesizes** everything into a numbered doctrine: recurring ideas ranked by how often they show up, contradictions flagged, and gaps listed.

Every claim traces back to a specific video, so you can always check the source.

## Why I built this

I watch a lot of long-form YouTube to learn: AI, business, negotiation, industries I'm curious about. Most of it evaporates. The best ideas are scattered across dozens of hours, repeated in slightly different words, and mixed in with sponsor reads and course pitches.

I wanted a way to keep the signal and drop the noise. I also wanted a real project to learn Claude Code on: one with downloads, cleanup scripts, sub-agents, git, and judgment calls, not just a toy example. This repo is the reusable part of that work.

## Use cases

Each brain has a **purpose**, and the purpose decides what gets extracted and what you end up with:

| Purpose | Good for | You end up with |
|---|---|---|
| **Skill** | Technical channels (AI tools, coding, workflows) | Techniques and workflows to adopt, compared against how you work now |
| **Experiment** | Side-hustle and "make money with X" channels | One card per business model (cost, time, steps, claimed results) and a ranked list of cheap tests to try |
| **Lens** | Business thinkers, negotiators, operators | Frameworks and diagnostic questions, so you can ask "how would this person look at my problem?" |
| **Primer** | An industry you know nothing about | A short briefing: how it works, key terms, how people get in |

Some examples:

- **Learning a tool fast:** distill a 100-video tutorial playlist into the 30 practices that keep coming up, with the outdated ones flagged.
- **Pressure-testing an idea:** turn a channel's worth of business models into a short list of experiments you could run for under $100 each.
- **Getting a second opinion:** build a lens from a negotiation or sales channel and run your next big conversation through it.
- **Helping a friend:** build a primer on their industry before you talk shop.
- **Comparing experts:** build brains from several creators on the same topic and see where they agree, disagree, and what only one of them covers.

## How it works

```
raw/        captions from yt-dlp (not committed)
clean/      cleaned transcripts (not committed)
extract/    one file of tagged claims per video
doctrine/   synthesized doctrine, conflicts, gaps
CLAUDE.md   project instructions Claude Code reads every session
```

The key rules in `CLAUDE.md`:

- Process **one video at a time** so nothing gets lost in a giant context.
- Tag every claim **durable** (principles that age well) or **perishable** (features, prices, rules that change).
- Mark every income or results figure as an **unverified creator claim**.
- **Skip** sponsor reads, affiliate links, and course pitches.
- **Paraphrase.** Don't copy the creator's words.
- **Checkpoint** on a small sample before scaling to the full set.

## Requirements

- [Claude Code](https://code.claude.com) with a Claude subscription
- Git, Python 3.7+, [yt-dlp](https://github.com/yt-dlp/yt-dlp) and Deno

## A note on respecting creators

This is for **personal learning**. Brains you build are distillations of someone else's work, so keep them private, don't redistribute transcripts, and support the creators whose content you learn from. Watch the videos behind the ideas you actually use.
