---
name: "mental-illness-profiler"
description: "Write a warm, clinically accurate, sourced family guide explaining a loved one's mental health and related conditions, how they interact, and how to support them."
license: MIT
---

# Mental Illness Profiler: family support guide

Use when the user wants a shareable guide or article that helps family, partners or friends understand someone's mental health, neurodevelopmental, trauma-related or chronic medical conditions, what episodes look like, and how to support them. The user may start from an article, a term (e.g. "dorsal vagal shutdown", "autistic burnout") or a list of conditions.

## Before writing: ask

Ask these in one message if the user hasn't already answered them. Make sensible defaults for anything skipped and say what you chose.

1. Is the guide general and shareable like an article, or about one named person? Does that person know about it or want to help write it?
2. How should the person be named? Default: "your loved one".
3. Who is the audience and what is their age? Default: adults 20+.
4. Which conditions are involved, and which are confirmed vs. possible?
5. What do episodes look like, and what triggers or eases them?
6. Should it include contacts, or be informational only?
7. What tone: warm and personal, or a clinical handout? Default: warm, clinically accurate.

## Principles

- **Experiences vs. explanations.** Treat the person's reported experiences (numbness, fog, freezing, disconnection, trouble speaking or starting tasks) as real. Keep them separate from the explanations for why they happen.
- **Respectful framing of emerging concepts.** Many terms (polyvagal "shutdown", autistic burnout, emotional dysregulation in ADHD) describe real experiences that are still being defined.
    - Present them as frameworks clinicians and communities use, without a debunking tone or naming critics.
    - Do not state a contested mechanism as settled fact. Add one neutral line such as "researchers are still working out the exact biology".
- **Prefer the best-established science where it exists.** Examples:
    - window of tolerance (Siegel)
    - tonic immobility research on trauma
    - stress effects on the prefrontal cortex (Arnsten)
    - formal diagnostic criteria (DSM-5)
    - condition-specific research on fatigue, pain and executive function
- **Show how conditions interact.** Explain how each condition adds load and how stress, pain, fatigue and lack of support lower the threshold for episodes.
- **Family support is evidence-based.** Include the research that social support protects against trauma symptoms, and that blame and disbelief worsen them.
- **No diagnosis.** Hold "possible" diagnoses lightly and say they are still being assessed.
- **Commercial health claims.** Do not include consumer DNA-test claims, supplement protocols or hormone advice from commercial pages. If the user's source contains them, leave them out. If the user insists, include them only with risks and clinician oversight.
- **Safety section.** Always include a "when to get help" table, including condition-specific red flags. Examples:
    - seizure signs after brain injury
    - eye inflammation or spinal fracture risk with ankylosing spondylitis
    - suicide risk; in the U.S., mention 911 and 988 even when no contacts are requested

## Output

A Can't Think page, ready to submit as a pull request. Read `README.md` at the repository root first, then build the page from `templates/article-template.html`.

- Section: **Learn to Love** (`/learn-to-love`). File: a short kebab-case `.html` file in the `learn-to-love/` folder, e.g. `learn-to-love/when-your-loved-one-shuts-down.html`.
- Hero eyebrow: `Learn to Love &middot; [date]`. Byline: `Authors: [contributor's name] (Human) and Claude (AI)`; ask the contributor for their name.
- Also add a card for the new page to `learn-to-love/index.html`, copying the markup of an existing `entry-card` there.
- Map the structure below onto the site's components: TL;DR → `.tldr` box; "The short version" → `ul.prose` with bold labels; "When to get help" → `.table-wrap.urgent`; the closing not-medical-advice line → `p.disclaimer`; comparisons → `.table-wrap` tables; sources → `.sources-list`.
- Use HTML entities for typographic characters (&rsquo; &ldquo; &rdquo; &mdash; &middot;) like existing pages. Open every external link with `target="_blank" rel="noopener"`.

Title it "When Your Loved One [Experience]" (e.g. "When Your Loved One Shuts Down"), with the date in the eyebrow and the byline under the hero. Write the outline (all headings) first, then research and fill one section at a time.

## Research

Search separately for each condition and concept. Prefer peer-reviewed reviews, meta-analyses, PMC/PubMed, diagnostic criteria, and university, hospital or charity resources. Gather:

1. Each condition's link to the experience, such as dissociation, shutdown, fatigue or executive function.
2. Trauma responses, such as freeze or tonic immobility, and how triggers work.
3. How stress affects thinking and executive function.
4. Practical support evidence: grounding, validation, social support and its effect on outcomes.
5. Condition-specific medical red flags.

Use specific numbers (study size, percentages, risk ratios) and link each claim inline.

## Structure

1. **Title** and byline (as-of date, author).
2. **TL;DR**: ONE warm, plain paragraph. Say what the experience is and that it is not a choice. Name the conditions that add up. End with what helps most.
3. **The short version**: 6-8 bullets, each starting with a bold label (e.g. **Shutdown is protection:**). Close with one line inviting the reader to keep reading.
4. **Why this guide exists**: who it's for, what the experience looks like from outside vs. inside, and that it's informational, not a diagnosis.
5. **What it can look like**: a table with columns "What you might see | What it may feel like inside | What usually helps".
6. **Why it happens**: one subsection per concept or condition. Typical order:
    - the framework (e.g. window of tolerance)
    - trauma and freeze
    - the popular term the user asked about
    - stress and the thinking brain
    - each condition
    - family support
7. **During an episode**: a "Try this | Instead of this" table, then grounding options. Note sensory differences for autistic people.
8. **Afterward, and every day**: right-after steps; "Believe them"; a "Need | What helps" table by condition; questions for a plan made together at a calm time; a short note on professional support.
9. **Taking care of yourself too**: short bullets for the supporter.
10. **When to get medical or urgent help**: a table with columns "Get emergency help now | Contact their doctor or care team soon", plus one closing line.
11. **Sources**: linked list of pages actually used, then an italic line saying it is general information, not medical advice.

## Style

- Warm, personal and non-judgmental. Address the reader as "you" and the person as "your loved one" (or as the user chooses).
- Simple words, short sentences (under 25 words), short paragraphs (3 sentences max).
- Clinically accurate: specific studies, numbers and criteria rather than adjectives.
- Paraphrase sources. Use at most one short quote per source.
- Tables wherever items are compared or paired.