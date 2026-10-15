# AI SEO checklist: GEO and AEO checklist for AI search, with an agent skill

**This is a practical AI SEO, GEO (generative engine optimization) and AEO (answer engine optimization) checklist for getting a website found, read and cited by ChatGPT, Google AI Overviews, Google AI Mode, Perplexity, Gemini, Microsoft Copilot and Claude.** It has 57 checks in six areas: technical access, entity and identity, content, off-site, local and measurement. Each check has a one-line reason and, where one exists, a primary source.

The same checklist ships as an agent skill (`ai-seo-geo-audit`) for Claude Code, Codex and other agents. The skill audits any website against it and reports pass, warn or fail with evidence.

> **Keywords:** AI SEO checklist, GEO checklist, generative engine optimization checklist, AEO checklist, answer engine optimization, AI search optimization, LLM SEO, ChatGPT SEO, AI Overviews, llms.txt, Claude skill for SEO, agent skill.

## Contents

**The checklist**
- [CHECKLIST.md: the master checklist on one page](https://github.com/Cited-io/ai-seo-geo-checklist/blob/main/CHECKLIST.md)
- [Technical access: AI crawlers, robots.txt, snippets, rendering, sitemaps, IndexNow, llms.txt](https://github.com/Cited-io/ai-seo-geo-checklist/blob/main/checklists/technical-access.md)
- [Entity and identity: Organization schema, sameAs, consistent profiles](https://github.com/Cited-io/ai-seo-geo-checklist/blob/main/checklists/entity-and-identity.md)
- [Content: answer-first pages, one question per page, evidence, comparisons, freshness](https://github.com/Cited-io/ai-seo-geo-checklist/blob/main/checklists/content.md)
- [Off-site: reviews, roundups, Reddit, YouTube, digital PR](https://github.com/Cited-io/ai-seo-geo-checklist/blob/main/checklists/off-site.md)
- [Local: Google Business Profile, Bing Places, Apple Business, listings](https://github.com/Cited-io/ai-seo-geo-checklist/blob/main/checklists/local.md)
- [Measurement: tracked prompts, repeated runs, control prompts](https://github.com/Cited-io/ai-seo-geo-checklist/blob/main/checklists/measurement.md)

**The agent skill**
- [skills/ai-seo-geo-audit/SKILL.md: the audit skill](https://github.com/Cited-io/ai-seo-geo-checklist/blob/main/skills/ai-seo-geo-audit/SKILL.md)
- [Install it in Claude Code, Codex and other agents](https://github.com/Cited-io/ai-seo-geo-checklist/blob/main/skills/ai-seo-geo-audit/README.md)
- [Check criteria the skill applies](https://github.com/Cited-io/ai-seo-geo-checklist/blob/main/skills/ai-seo-geo-audit/references/checks.md)
- [scripts/check_robots.py: robots.txt check for 13 AI and search crawlers](https://github.com/Cited-io/ai-seo-geo-checklist/blob/main/skills/ai-seo-geo-audit/scripts/check_robots.py)
- [scripts/inspect_page.py: raw-HTML page inspector (meta robots, canonical, headings, JSON-LD)](https://github.com/Cited-io/ai-seo-geo-checklist/blob/main/skills/ai-seo-geo-audit/scripts/inspect_page.py)

**Project**
- [CONTRIBUTING.md](https://github.com/Cited-io/ai-seo-geo-checklist/blob/main/CONTRIBUTING.md)
- [LICENSE (MIT)](https://github.com/Cited-io/ai-seo-geo-checklist/blob/main/LICENSE)

## How to use it

### By hand

1. Open [CHECKLIST.md](https://github.com/Cited-io/ai-seo-geo-checklist/blob/main/CHECKLIST.md) and work top to bottom. Start with access, because an engine can't cite a page it can't read.
2. For any item you're unsure about, open its section file. Each one gives the reason, how to check it, the fix and the source.
3. Copy the checklist into an issue or a doc, and tick items off as you ship them. The IDs (T2, E1, C4 …) stay stable, so you can refer to them in tickets.

### With an agent

Install the skill, then ask for an audit. In Claude Code:

```text
/plugin marketplace add Cited-io/ai-seo-geo-checklist
/plugin install ai-seo-geo@cited-io
/ai-seo-geo:ai-seo-geo-audit https://example.com
```

Or, for any agent that supports skills:

```bash
npx skills add Cited-io/ai-seo-geo-checklist
```

The skill fetches robots.txt, the sitemap, llms.txt and a handful of key pages. It reads their raw HTML and JSON-LD, and returns:

- a short summary;
- the top five fixes;
- a findings table (ID, status, evidence, fix, source);
- crawler access per AI agent;
- a list of what it couldn't check from outside, such as CDN rules, Search Console, listings and prompt tracking.

Other agents, and the details, are in the [install guide](https://github.com/Cited-io/ai-seo-geo-checklist/blob/main/skills/ai-seo-geo-audit/README.md).

## What makes this checklist different

- **It sticks to sources.** Every documented rule links to the engine's own docs (OpenAI, Anthropic, Perplexity, Google Search Central, Bing, Apple), or to the [KDD 2024 GEO paper](https://arxiv.org/abs/2311.09735). Common practice is labelled *(practice)*, so you can tell the two apart.
- **It is honest about llms.txt.** It's an optional proposal. Google says such files "will neither harm nor help" in Search ([source](https://developers.google.com/search/docs/fundamentals/ai-optimization-guide)). The skill reports it as information and never fails a site for skipping it.
- **It separates search from training.** You can block `GPTBot`, `ClaudeBot` or `Google-Extended` and still allow the crawlers that put you in AI answers, such as `OAI-SearchBot`, `Claude-SearchBot` and `PerplexityBot`.
- **It treats measurement as part of the work.** You need tracked prompts, repeated runs and control prompts to know whether a change helped.
- **It uses real data.** The off-site section draws on Cited's open [AI search citations dataset](https://github.com/Cited-io/ai-search-citations-dataset). In its 138 answers to 23 questions about AI search and GEO, ChatGPT listed 17.2 domains as sources per answer and Google AI Mode listed 2.6.

## FAQ

**Is GEO different from SEO?**
GEO keeps SEO's foundations: crawlable, indexable, useful pages. It adds a second question: once an engine reads the page, does its answer name you? Google treats optimizing for its AI features as SEO. Other engines have their own crawlers and sources. More: [GEO vs SEO](https://cited.io/guides/geo-vs-seo).

**What's the difference between AI SEO, GEO and AEO?**
In practice, nothing. They're different names for getting your brand named and cited in AI-written answers. See the [AI search glossary](https://cited.io/guides/ai-search-glossary).

**Do I need llms.txt?**
No. It's cheap to add and fine to skip. See T14.

**Does the skill send my data anywhere?**
No. It makes ordinary HTTPS requests to the site you name, and nothing else.

## Contributing

Issues and pull requests are welcome. Every new or changed item needs a source. See [CONTRIBUTING.md](https://github.com/Cited-io/ai-seo-geo-checklist/blob/main/CONTRIBUTING.md).

## License

[MIT](https://github.com/Cited-io/ai-seo-geo-checklist/blob/main/LICENSE). Use it, fork it, and put it in your own client audits.

---

Maintained by [Cited](https://cited.io): AI SEO and GEO agency with its own AI visibility platform. The long-form guide behind this checklist: [AI SEO and GEO, step by step](https://cited.io/guides/ai-seo).
