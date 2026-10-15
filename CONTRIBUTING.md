# Contributing to the AI SEO and GEO checklist

**Issues and pull requests are welcome. Every new or changed check needs a source.**

## What a good change looks like

- **A new check:**
  - add a `- [ ]` line to [CHECKLIST.md](https://github.com/Cited-io/ai-seo-geo-checklist/blob/main/CHECKLIST.md) with the next free ID in its section;
  - give it a one-line reason;
  - add the detail (why, how to check, fix, source) to the matching file in `checklists/`;
  - if an agent can check it from outside the site, add its criteria to [references/checks.md](https://github.com/Cited-io/ai-seo-geo-checklist/blob/main/skills/ai-seo-geo-audit/references/checks.md).
- **A correction:** link the current primary source. Engines change crawler names and controls often, so a dated link to the engine's own docs beats a blog post.
- **A script fix:** keep the scripts to the Python standard library, and describe how you tested the change.

## Sources

- **Prefer primary sources:** the engine's own documentation (OpenAI, Anthropic, Perplexity, Google Search Central, Bing, Apple), standards (RFC 9309, schema.org), and peer-reviewed research.
- **Label practice:** a check that is common practice but not documented anywhere is welcome. Label it *(practice)*.
- **No unsourced statistics.** No vendor claims presented as fact.
- **No promotional links.** Tool or agency links are out of scope.

## Style

- **Plain words.** One idea per sentence. Lead with the answer.
- **IDs are stable.** Never renumber existing IDs. Retire one by marking it removed.

## Reporting a problem

Open an issue with:

- the check ID;
- what is wrong or out of date;
- the source that shows it.
