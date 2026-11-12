---
name: "philosophy-profiler"
description: "Write a sourced, reader-friendly article tracing a word, idea or philosophy from its original root meaning through history to how it is used today."
license: MIT
---

# Philosophy Profiler

Use this when the user wants an article explaining what a word, ideology or philosophy (e.g. "liberal", "conservative", "stoic", "socialism") actually means, starting from its roots.

## Output

A Can't Think page, ready to submit as a pull request. Read `README.md` at the repository root first, then build the page from `templates/article-template.html`.

- Section: **Words & Society** (`/words-and-society`). File: a short kebab-case `.html` file in the `words-and-society/` folder, e.g. `words-and-society/what-does-liberal-mean.html`.
- Hero eyebrow: `Words &amp; Society &middot; [date]`. Byline: `Authors: [contributor's name] (Human) and Claude (AI)`; ask the contributor for their name.
- Also add a card for the new page to `words-and-society/index.html`, copying the markup of an existing `entry-card` (kicker `Etymology &middot; [date]`) there.
- Map the structure below onto the site's components: TL;DR → `.tldr` box; "The short version" eras → `.timeline` / `.tl-item` with the era in `.tl-date`; perspectives → one `.issue` block per group with the group in `.topic`; historians' asides → `.note-box`; comparisons → `.table-wrap` tables; sources → `.sources-list`.
- Use HTML entities for typographic characters (&rsquo; &ldquo; &rdquo; &mdash; &middot;) like existing pages. Open every external link with `target="_blank" rel="noopener"`.

Write the outline (all headings) first, then research and fill one section at a time.

## Research

1. Etymology: search an etymology source (e.g. etymonline.com) and fetch the entry. Get the original language root, literal meaning, and dates each English sense appeared.
2. Origin of the concept: how the earliest users (e.g. ancient Romans or Greeks) understood it, with named thinkers.
3. First political or formal use: when and where it first named a group, party or movement.
4. Major shifts: each era where the meaning changed, and why.
5. Today: how the term is used in different countries and by different groups.
6. Perspectives: what supporters, critics from each side, and historians say.

Run separate searches for each era and each country or side, so coverage is balanced. Fetch pages you take dates or facts from.

## Structure

1. **Title** and byline (as-of date, author).
2. **TL;DR**: ONE short paragraph, plain words, written for a reader with little time or background. Lead with the root meaning, end with the thought-provoking contrast with today's usage.
3. **The short version**: 5-8 bullets, one per era, each starting with a bold era label (e.g. **Ancient Rome:**). Close with one line inviting the reader to keep reading.
4. **Introduction**: why the term confuses people today.
5. **The root**: the original word and what it meant to the people who first used it.
6. **Early everyday / lifestyle meaning**, including any negative senses.
7. **First political use.**
8. **Each major historical shift**, one section each.
9. **Around the world today**: a table (country or region, what the word signals, example).
10. **As a personal outlook today**, with a bulleted list of perspectives (supporters, critics on each side, historians).
11. **Conclusion**: the common thread, plus a timeline table (newest first).
12. **Sources**: linked list of pages actually opened.

## Style

- Simple words, short sentences (under 25 words), short paragraphs (3 sentences max).
- Specific names, dates and places rather than adjectives.
- Paraphrase sources; at most one short quote per source.
- The user may want the piece to make a point (e.g. that a modern insult contradicts the root meaning). Write it in their voice, but keep it credible: acknowledge in a clause what critics actually mean, and present the strongest opposing views fairly in the perspectives section.