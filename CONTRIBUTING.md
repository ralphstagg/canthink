# Contributing to Can't Think

Thanks for wanting to add to [Can't Think](https://www.cantthink.net). This site is a collection of plain-language, sourced articles meant to help people slow down and think. Every page follows a house structure so readers know what to expect, and so pages within a section can be compared side by side.

This guide covers what kinds of articles fit, how to write one with the Claude skills in this repo, how pages are built, and what reviewers check before merging.

---

## Contents

1. [What belongs here](#what-belongs-here)
2. [Ground rules](#ground-rules)
3. [The site sections](#the-site-sections)
4. [Writing an article with the Claude skills](#writing-an-article-with-the-claude-skills)
5. [Writing an article by hand](#writing-an-article-by-hand)
6. [How a page is built](#how-a-page-is-built)
7. [Style guide](#style-guide)
8. [Sources and citations](#sources-and-citations)
9. [Submitting a pull request](#submitting-a-pull-request)
10. [Review checklist](#review-checklist)
11. [License](#license)

---

## What belongs here

Good fits:

- **Small, honest starting points** on a hard topic. Understanding before action; clarity before certainty.
- **Fact-based, sourced** writing. Every factual claim can be traced to a page the author actually opened.
- **Plain language** a busy reader can follow, with a short answer up top.
- **Fairness.** Even when a page makes a point, it describes the strongest version of the other side.

Not a fit:

- Opinion pieces with no sources, or sources that only support one side.
- Attacks on private individuals, or digging into private family members of public figures.
- Commercial health claims (supplements, DNA tests, hormone protocols), affiliate links or ads.
- Anything copied from another site. Paraphrase; quote sparingly (see [Sources](#sources-and-citations)).

If you are not sure an idea fits, open an issue describing it before you write.

## Ground rules

- **Neutral where the section is neutral.** Candidate fact sheets and legislation breakdowns describe the record; they do not tell readers how to vote or give a personal verdict.
- **No diagnosis.** Learn to Love guides explain conditions and how to support people. They never diagnose anyone, and they always include when to get help.
- **Disclose AI help.** If you used Claude (or another AI tool), say so in the byline, in the same form the site already uses: `Authors: Your Name (Human) and Claude (AI)`. You remain responsible for every fact on the page.
- **Check it yourself.** AI-assisted research can be wrong. Open the sources, confirm dates and numbers, and make sure every link works.
- **Be kind in review threads.** Disagree with claims and sources, not people.

## The site sections

Each article lives in one section. Each section has an index page that lists its articles as cards.

| Section | Index page | What goes there | Claude skill |
| --- | --- | --- | --- |
| **Learn to Love…** | `/learn-to-love` | Guides to understanding and supporting people living with chronic illness, mental health conditions, shutdown and trauma. | `/mental-illness-profiler` |
| **Texas Candidate Fact Sheets** | `/texas-candidates-2026` | Neutral, sourced public-record pages on candidates. For other states or races, ask in an issue first; a new section page may be needed. | `/public-profiler` |
| **Words & Society** | `/words-and-society` | Where loaded words come from, what they used to mean, and how they are used today. | `/philosophy-profiler` |
| **Current US Legislation That's Disturbing** | `/disturbing-legislation` | Section-by-section breakdowns of laws and executive orders whose vague wording could reach further than their stated target. | `/exec-order-summary` |
| **Humanity and the Problems It Faces…** | `/humanity-and-the-problems-it-faces` | What is actually broken (crime, cruelty, poverty) with honest numbers and an honest look at what might fix it. | No skill yet; follow an existing page's shape. |

## Writing an article with the Claude skills

The repo ships four Claude skills in `.claude/skills/`. Each one knows the research steps, section order, tone and page format for its section, so your article comes out matching the rest of the site.

### Setup

1. Fork this repo and clone your fork.
2. Install [Claude Code](https://docs.claude.com/en/docs/claude-code/overview).
3. Open a terminal in the repo folder and run `claude`.

That is all. Skills in a project's `.claude/skills/` folder load automatically when you work in that project, and `git pull` keeps them up to date. Type `/` in Claude Code to see them listed.

### Run a skill

Invoke the skill by name and say what you want to write about:

```
/philosophy-profiler  What does "socialism" actually mean?
/mental-illness-profiler  A guide for families of someone with complex PTSD and chronic pain
/exec-order-summary  Executive Order 14XXX and how it could affect immigrant workers
/public-profiler  A fact sheet on [candidate name], running for [office]
```

Claude will usually ask a few questions first (your name for the byline, your audience, the angle you want). It then builds an outline, researches each section and writes the page as an HTML file in the repo, plus a card on the section's index page.

### Using another AI tool

The skills are plain Markdown instructions (`SKILL.md`). Tools that support the Agent Skills format can use the folders directly; check your tool's docs for where it looks for skills. For other tools, paste the relevant `SKILL.md` into the conversation, then attach `CONTRIBUTING.md` and `templates/article-template.html`.

### After the skill finishes

You are the editor. Before opening a pull request:

- Read the whole page in a browser (open the `.html` file, or run a local server such as `npx serve .`).
- Open every source link. Remove any claim you cannot confirm.
- Check names, dates, numbers, vote counts and quotes against the sources.
- Cut anything that sounds like a verdict in a section that is meant to be neutral.

## Writing an article by hand

You do not need Claude. Copy `templates/article-template.html`, rename it, and follow the section order for your section's skill (read the matching `SKILL.md` in `.claude/skills/`; the "Structure" or "Sections" list is the outline). Then follow the rest of this guide.

## How a page is built

The site is plain HTML served by Netlify. There is no build step, no framework and no Markdown conversion.

```
/
├── index.html                    home page
├── fact-sheet.css                shared styles for every page
├── learn-to-love.html            section index pages
├── words-and-society.html
├── ...
├── what-does-liberal-mean.html   one file per article
├── templates/
│   └── article-template.html     start new pages from this
└── .claude/skills/               Claude skills for contributors
```

### File names and URLs

- One `.html` file per article, at the site root, in short lowercase kebab-case: `what-does-liberal-mean.html`.
- Netlify serves it without the extension: `/what-does-liberal-mean`. Use extension-less links everywhere (`href='/words-and-society'`).
- Candidate fact sheets use `[lastname]-fact-sheet.html`.

### Page skeleton

Every article has the same frame. Start from `templates/article-template.html`, which has all of it.

1. **`<head>`**: `<title>Article Title &mdash; Can't Think</title>`, a one or two sentence `<meta name="description">`, the Google Fonts link (Fraunces and Karla), `fact-sheet.css`, then a small page `<style>` block for the TL;DR box and other extras.
2. **`.topnav`**: the site mark and a breadcrumb: `Home · Section · Short page name`.
3. **`.hero`**: an `.eyebrow` (section name and date), the `<h1>`, a `.sub` summary sentence, a `.meta-row` of `.pill` tags (topic tags and a reading time), and a `.byline`.
4. **`.section` blocks**, each with a `.wrap` and an `<h2>`, in the order your section's skill sets.
5. **Sources** as the last section, as a `.sources-list`.
6. **`<footer class="wrap">`** linking back to the section page.

### Components

These classes come from `fact-sheet.css` or the template's page style. Reuse them rather than inventing new ones.

| Component | Markup | Use for |
| --- | --- | --- |
| TL;DR box | `div.tldr` > `div.tldr-label` + `p` (or `ul`) | The short answer at the top. Sage colors by default; ember colors for legislation pages (see the comment in the template). |
| Timeline | `div.timeline` > `div.tl-item` > `div.tl-date` + `p` | Eras, dated events, arrests, "the short version" of a history. |
| Prose list | `ul.prose` | Bulleted lists inside body text; start items with a `<strong>` label. |
| Table | `div.table-wrap` > `table` with `thead`/`tbody` | Anything compared or paired. Add `.urgent` for "when to get help" tables. |
| Issue block | `div.issue` > `div.topic` + `p` | One viewpoint, argument, topic or controversy per block. |
| Response box | `div.response-box` > `div.rb-label` + text, inside an `.issue` | A person's or campaign's reply to a criticism. |
| At-a-glance grid | `div.glance-grid` > `div.glance-item` > `div.label` + `div.value` | Quick facts on fact sheets (born, education, offices). |
| Note box | `div.note-box` | A caveat, a historian's aside, or "more entries to come". |
| Open question | `div.open-q` with a leading `<strong>Open question:</strong>` | Something the record does not settle. |
| Pull quote | `p.pull` | Rarely; one short line worth highlighting. |
| Pills | `span.pill` inside `.meta-row` | Tags and reading time. Fact sheets add party: `pill r` for Republican. |
| Disclaimer | `p.disclaimer` | "General information, not medical/legal advice" lines. |

### Add your page to its section

Each section index page lists its articles as cards. Add one for your page by copying an existing card on that page (`entry-card` on most sections, `candidate-card` on the fact sheet section) and updating the link, kicker (category and date), title and one-sentence description. Newest entries go at the end of the grid unless the maintainer asks otherwise.

### Encoding and links

- Use HTML entities for typographic characters, as existing pages do: `&rsquo;` `&ldquo;` `&rdquo;` `&mdash;` `&ndash;` `&middot;` `&rarr;`.
- External links open in a new tab: `target="_blank" rel="noopener"`.
- Keep everything in the page itself and `fact-sheet.css`. Do not add JavaScript, trackers, embeds or new external stylesheets.
- If a change to `fact-sheet.css` seems necessary, propose it in its own pull request.

## Style guide

- **Short answer first.** Every page opens with a TL;DR a reader can stop after.
- **Simple words.** Sentences under 25 words. Paragraphs of three sentences or fewer.
- **Specifics over adjectives.** Names, dates, places, numbers, bill numbers, study sizes.
- **Tables wherever things are compared.**
- **Warm where the section is personal** (Learn to Love), **even-handed where it is civic** (fact sheets, legislation, words).
- **Address the reader as "you"** in guides; refer to the person being supported as "your loved one" unless there is a reason not to.
- **Dates** in the eyebrow and cards as `Oct. 29, 2026`. Fact sheets say `Updated Oct. 25, 2026`.

## Sources and citations

- **Cite pages you actually opened.** Do not cite from search snippets or memory.
- **Link claims inline** where they appear, and list every source again in the Sources section.
- **Prefer original sources**: official records, court filings, the Federal Register, legislature vote databases, peer-reviewed research (PubMed/PMC), diagnostic criteria, major university or hospital pages.
- **Label partisan sources.** On fact sheets and legislation pages, add a line at the top of Sources naming any partisan, campaign or advocacy sources.
- **Paraphrase.** Quote at most one short passage (under 15 words) per outside source. The text of laws and executive orders is public domain and can be quoted where the exact wording matters.
- **No images of real people** copied from other sites.
- **Time-sensitive pages** (candidates, legislation) need a fresh check of current status before submitting, and an "Updated" date.

## Submitting a pull request

1. Create a branch: `git checkout -b add-what-does-socialism-mean`.
2. Add your article file and the card on its section page. Keep each pull request to one article.
3. Open both pages in a browser and check them at phone width.
4. Commit, push to your fork and open a pull request. Fill in the template, including whether you used AI.
5. A maintainer will review it. Expect questions about sources; that is normal and not a rejection.

Corrections to existing pages are welcome too. Open a pull request that changes only what is wrong and links the source showing the correction.

## Review checklist

Maintainers check every pull request for:

- [ ] Fits a section and the site's purpose.
- [ ] Follows the section's structure (see the matching skill's `SKILL.md`).
- [ ] Built from the template: title, description, topnav, hero with eyebrow, pills and byline, sections, Sources, footer.
- [ ] Card added to the section index page; links are extension-less and work.
- [ ] Every factual claim is sourced; sources were opened and support the claim.
- [ ] Partisan sources are labeled; neutral sections contain no verdicts; criticisms include the subject's response.
- [ ] Quotes are short and few; nothing is copied.
- [ ] Learn to Love guides include the "when to get help" table and the not-medical-advice line.
- [ ] AI use is disclosed in the byline.
- [ ] No new scripts, trackers, embeds or external styles.
- [ ] Reads well on a phone.

## License

The Claude skills in `.claude/skills/` are released under the MIT License (see `.claude/skills/LICENSE`).
