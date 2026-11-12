---
name: "exec-order-summary"
description: "Analyze a US executive order's wording for how vague terms could affect a specific group, then build a shareable doc with a plain-language TLDR."
license: MIT
---

# Executive Order Summary

Use when the user names an executive order (by title or number) and wants to know how its wording could affect a group of people, such as people with disabilities, mental health conditions, immigrants, or workers. If the user doesn't name a group, ask which group to focus on, or default to the groups most directly named in the order.

## Steps

### 1. Get the official text
- Search for the order by title and number. Fetch the full text from the Federal Register (govinfo.gov or federalregister.gov) or whitehouse.gov. Never work from summaries alone.
- Record the EO number, signing date, and Federal Register publication date.

### 2. Check definitions first
- Look for a definitions section. If there is none, say so prominently, because undefined terms are left to whoever implements the order.
- List every key term that is undefined or loosely defined. For each one, note where it appears and why the vagueness matters for the focus group.
- Watch for inconsistent terms across sections (e.g. "mental illness" in one section, "serious mental illness" in another), "or" clauses that create alternative paths, open-ended phrases ("other available means", "appropriate", "maximally flexible"), and missing time limits.

### 3. Section-by-section wording analysis
For each provision that could affect the focus group:
- Quote the exact operative phrase (federal text is public domain).
- Explain in plain words how it could be read or applied against the group.
- Tie it to the relevant legal protections (Constitution, Supreme Court precedent, ADA/Section 504, Fair Housing Act, privacy law, etc.).
- Include real-world evidence that this kind of harm happens, with a source.

### 4. Research reactions
Run separate searches for:
- US legal and advocacy analysis (ABA, civil rights and disability organizations, law firm client alerts, medical and professional associations).
- Interpretations and critics from outside the US: UN treaty bodies (e.g. the CRPD Committee), UN Special Rapporteurs, WHO/OHCHR guidance, foreign advocacy groups, and comparable laws in other countries that went the same or the opposite way. Note the US's treaty status (signed vs ratified). If few foreign governments commented directly, say so.
- Implementation since signing: agency guidance, grant notices, court challenges, state laws, related bills in Congress.

### 5. Present both sides fairly
- Include the strongest arguments from supporters (including the White House fact sheet) in a short section.
- Follow with critics' main reply in a sentence or two.
- Do not add a personal verdict on whether the order is good or bad.

### 6. Write the article
A Can't Think page, ready to submit as a pull request. Read `CONTRIBUTING.md` at the repository root first, then build the page from `templates/article-template.html`.

- Section: **Current US Legislation That's Disturbing** (`/disturbing-legislation`). File: a short kebab-case `.html` file at the site root, e.g. `eo-14321-disabilities-mental-health.html`.
- Hero eyebrow: `Current US Legislation &middot; [date]`. Byline: `Authors: [contributor's name] (Human) and Claude (AI)`; ask the contributor for their name.
- Also add a card for the new page to `disturbing-legislation.html`, copying the markup of an existing `entry-card` there.
- Map the structure below onto the site's components: TL;DR → `.tldr` box; use the ember TL;DR colors noted in the template, with the bullets as a `ul` inside `.tldr`; supporters' arguments → one `.issue` per argument; "What the order is" and "Limits" lists → `ul.prose`; the not-legal-advice line → `p.disclaimer`; comparisons → `.table-wrap` tables; sources → `.sources-list`.
- Use HTML entities for typographic characters (&rsquo; &ldquo; &rdquo; &mdash; &middot;) like existing pages. Open every external link with `target="_blank" rel="noopener"`.

Write the outline (all headings) first, then research and fill one section at a time. Use these sections:
1. **TLDR**: one-sentence lead plus 5 to 8 plain-language bullets for readers who won't read the whole thing. Short sentences, no legal jargon.
2. **What the order is**: number, dates, what it directs, and its stated goal.
3. **The core problem: definitions**: a table of undefined terms (term, where it appears, why it matters).
4. **Section-by-section analysis**: one subheading per issue.
5. **Views from outside the US**: a table (source, position, how it relates to the order), plus a note on whether the international picture is one-sided.
6. **Limits and what has happened since**.
7. **The other side**.
8. **Where to get help**: relevant advocacy or legal-aid organizations for the focus group, plus a line that this is not legal advice.
9. **Sources**: links to pages actually opened.

## Style
- Plain language; sentences under 25 words.
- Paraphrase outside sources; quote only the order itself freely.
- Cite sources for every factual claim about reactions or implementation.
- Search for current status every time, since agency actions and litigation change.