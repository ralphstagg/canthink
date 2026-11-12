---
name: "public-profiler"
description: "Build a neutral, sourced one-page public-record fact sheet on a politician or candidate: career, votes, statements, arrests, ethics issues, attendance."
license: MIT
---

# Public profiler: candidate fact sheet

Use when the user asks for a fact sheet, one-pager, profile or public record on a politician, candidate or public official.

## Principles

- Neutral and evenhanded. Describe the record; do not give a verdict on the person.
- Research before writing. Search the web for current information even if the person seems familiar: offices, races, polls and controversies change.
- Search separately for each part (background, votes, statements, arrests, ethics) and for both supportive and critical coverage.
- Attribute every claim to its source. Flag partisan outlets (right or left) and campaign statements.
- For every criticism, include the person's or campaign's response.
- Say plainly when something was not found (e.g. "No arrest or criminal charge appears in public reporting"). Include debunked rumors only with the fact-check.
- Separate political disputes over past statements from actual ethics findings, and state whether any formal complaint or legal proceeding exists.
- Only public conduct of the public figure. Do not dig into private family members beyond what reporting ties to the public record.

## Output

A Can't Think page, ready to submit as a pull request. Read `CONTRIBUTING.md` at the repository root first, then build the page from `templates/article-template.html`.

- Section: **Texas Candidate Fact Sheets (or the section the maintainer names for other races)** (`/texas-candidates-2026`). File: a short kebab-case `.html` file at the site root, e.g. `paxton-fact-sheet.html` (`[lastname]-fact-sheet.html`).
- Hero eyebrow: `Public Record Fact Sheet &middot; Updated [date]`. Byline: `Authors: [contributor's name] (Human) and Claude (AI)`; ask the contributor for their name.
- Also add a card for the new page to `texas-candidates-2026.html`, copying the markup of an existing `candidate-card` there.
- Map the structure below onto the site's components: TL;DR → `.tldr` box; "At a glance" table → `.glance-grid` of `.glance-item` (`.label` / `.value`); party → a `.pill` (`pill r` for Republican); "In their own words" → one `.issue` per topic; ethics items → `.issue` with a `.response-box` for their response; arrests and event sequences → `.timeline`; attendance gaps → `.open-q`; comparisons → `.table-wrap` tables; sources → `.sources-list`.
- Use HTML entities for typographic characters (&rsquo; &ldquo; &rdquo; &mdash; &middot;) like existing pages. Open every external link with `target="_blank" rel="noopener"`.

The `<h1>` is just the person's name; the `<title>` is `[Name] &mdash; Public Record Fact Sheet`. The as-of date goes in the eyebrow and the byline under the hero. Write the outline (all headings) first, then fill one section at a time.

Style: specific numbers and dates, short sentences, tables wherever items are compared, links to sources inline and in a Sources list.

## Sections, in order

1. **At a glance**: one or two lead sentences (who they are, the current race, the headline finding such as whether any arrests were found and the main ethics question). Then a short table: Born, Education, Office and districts with years, Race (primary or latest result), Latest poll.
2. **Prior career record** (teaching, business, military, law, etc.): where and when, what is documented, whether any complaints or misconduct were found. Two or three bullets with sources.
3. **Legislative record**: signature bills authored or passed. Then a table of the votes critics cite, by area (e.g. guns, border, crime), with bill numbers and years. Note who compiled the list and its leaning. Link to the official legislature vote database.
4. **In their own words**: their latest major town hall, debate or interview, with date, place and format. If the user gives a video link with no transcript, use news coverage of that event and say so. Table: Topic | What they said (immigration, abortion, debt, foreign policy, faith, energy and economy, political reform, anything topical). Note where voters challenged them.
5. **Arrests**: whether any arrests or charges were found; debunked rumors with the fact-check.
6. **Ethics questions and controversies**: open with whether any formal complaint or proceeding exists, then a table: Issue | What was reported | Their response. Follow with one line on political attacks over past statements, labeled as political disputes.
7. **Attendance record** (short, near the bottom): the critics' missed-vote claim, then the verified count and miss rate from official roll-call data, compared with the chamber average and their rank. Two or three bullets on context (e.g. quorum breaks, clustered absences) and any open questions or missing data.
8. **Sources**: one line noting which sources are partisan, then a linked list of pages actually opened.

## Verifying missed votes (state legislators)

- Data: LegiScan bulk datasets per session (legiscan.com/<STATE>/datasets, free login; CSV zips contain rollcalls.csv, votes.csv, people.csv). The user must download them; the site's security check can save an .html page instead of the .zip, so check that each file is a real zip of a few MB.
- Count a vote as missed when vote_desc is Absent or NV (present, not voting); report absent-only too. Use only that chamber's roll calls. Exclude the presiding Speaker, who traditionally does not vote.
- Validate the method against an independent scorecard where one exists (e.g. the Club for Growth Foundation state missed-votes scorecard) before trusting other years.
- Rank only members who served the whole period; give per-session rows and an overall row, plus the chamber average and median.
- Name any sessions not yet analyzed and what they would need to show for the critics' figure to hold.

## Federal officials

For members of Congress, use GovTrack or C-SPAN missed-vote data and Congress.gov roll calls instead of state datasets.