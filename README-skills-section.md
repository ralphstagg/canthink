## Contributing articles with Claude skills

This repo includes four [Claude skills](https://docs.claude.com/en/docs/agents-and-tools/agent-skills/overview) that write articles in the site's house format: the same research steps, section order, tone and page template as the existing pages. They live in `.claude/skills/`, so anyone who clones the repo and runs [Claude Code](https://docs.claude.com/en/docs/claude-code/overview) inside it gets them automatically, and `git pull` keeps them current.

| Skill | Section | What it writes |
| --- | --- | --- |
| `/philosophy-profiler` | Words & Society | Traces a word, idea or philosophy from its original root meaning, through each era where its meaning shifted, to how different countries and groups use it today. Ends with a fair range of perspectives and a timeline. |
| `/mental-illness-profiler` | Learn to Love | A warm, clinically accurate family guide to a loved one's mental health, neurodevelopmental, trauma-related or chronic medical conditions: what episodes look like, why they happen, how conditions interact, what helps, and when to get urgent help. |
| `/exec-order-summary` | Current US Legislation That's Disturbing | Reads a US executive order's official text section by section, flags undefined or vague terms, explains how they could be applied to a specific group, and covers legal context, international views, what has happened since, and supporters' arguments. |
| `/public-profiler` | Candidate Fact Sheets | A neutral, sourced public-record fact sheet on a politician or candidate: background, career, legislative record and votes, their own statements, arrests, ethics questions with their responses, and a verified attendance record. |

### Quick start

```bash
git clone https://github.com/YOUR-USERNAME/YOUR-FORK.git
cd YOUR-FORK
claude
```

Then, inside Claude Code:

```
/philosophy-profiler  What does "socialism" actually mean?
```

Claude asks a few questions, researches, and writes the page as an HTML file in its section's folder, plus a card on the section index. Review it, check every source, and open a pull request. See [README.md](README.md) for the full guide, page template and review checklist.

The skills are MIT licensed and are plain Markdown, so other Agent Skills–compatible tools can use them too.
