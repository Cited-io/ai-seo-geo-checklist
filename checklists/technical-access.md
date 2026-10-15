# Technical access checklist for AI search (AI crawlers, robots.txt, snippets, rendering, sitemaps, IndexNow)

**An AI engine can only cite a page it was allowed to fetch, could read, and was allowed to quote.** So check four things in order. Are the search crawlers allowed in robots.txt and at the CDN? Is the page indexable and snippet-eligible? Is the content in the HTML the server sends? Can engines find new and changed pages quickly?

Each item below has an ID that matches the [master checklist](https://github.com/Cited-io/ai-seo-geo-checklist/blob/main/CHECKLIST.md) and the [audit skill](https://github.com/Cited-io/ai-seo-geo-checklist/blob/main/skills/ai-seo-geo-audit/SKILL.md).

## The crawlers that matter

Most AI companies run separate agents for search, for user-triggered visits and for training. Each one obeys its own robots.txt group, so you can allow search and still opt out of training.

| Company | Search / index | Fetches when a user asks | Training | Source |
|---|---|---|---|---|
| OpenAI | `OAI-SearchBot` | `ChatGPT-User` | `GPTBot` | [OpenAI crawlers](https://developers.openai.com/api/docs/bots) |
| Anthropic | `Claude-SearchBot` | `Claude-User` | `ClaudeBot` | [Anthropic crawlers](https://support.claude.com/en/articles/8896518-does-anthropic-crawl-data-from-the-web-and-how-can-site-owners-block-the-crawler) |
| Perplexity | `PerplexityBot` | `Perplexity-User` | none listed | [Perplexity crawlers](https://docs.perplexity.ai/guides/bots) |
| Google | `Googlebot` (AI Overviews, AI Mode) | n/a | `Google-Extended` (a control token, not a separate crawler) | [Google common crawlers](https://developers.google.com/crawling/docs/crawlers-fetchers/google-common-crawlers) |
| Apple | `Applebot` | n/a | `Applebot-Extended` (a control token) | [Apple](https://support.apple.com/en-us/119829) |
| Microsoft | `Bingbot` (Bing and Copilot) | n/a | controlled with page-level tags (T7) | [Bing](https://blogs.bing.com/webmaster/september-2023/Announcing-new-options-for-webmasters-to-control-usage-of-their-content-in-Bing-Chat) |

What the docs say, in short:

- **OpenAI:** "Sites that are opted out of OAI-SearchBot will not be shown in ChatGPT search answers." GPTBot's rules are separate. For `ChatGPT-User`, "robots.txt rules may not apply" because a person started the visit.
- **Anthropic:** blocking `Claude-User` "prevents our system from retrieving your content in response to a user query". Blocking `Claude-SearchBot` "prevents our system from indexing your content for search optimization". `ClaudeBot` is the training crawler. Anthropic also honors `Crawl-delay`.
- **Perplexity:** `PerplexityBot` "is designed to surface and link websites in search results on Perplexity". `Perplexity-User` "generally ignores robots.txt rules", because a user requested the fetch.
- **Google:** `Google-Extended` "does not impact a site's inclusion in Google Search nor is it used as a ranking signal".
- **Apple:** "Webpages that disallow Applebot-Extended can still be included in search results."

## Items

### T1. `/robots.txt` loads and parses
- **Why:** if the file errors or returns HTML, each crawler falls back to its own default.
- **Check:** `curl -sI https://example.com/robots.txt` returns `200` and `text/plain`. The body has `User-agent` groups, not an HTML page.
- **Fix:** serve a plain-text file at the root of each host (`www` and the bare domain count as separate hosts). [Google: robots.txt](https://developers.google.com/search/docs/crawling-indexing/robots/intro)

### T2. AI search crawlers are allowed
- **Why:** blocking `OAI-SearchBot` keeps you out of ChatGPT search answers. The same holds for each engine's search crawler.
- **Check:** for each search agent in the table, find the group that applies to it (its own group, else `*`). Confirm your key paths are not disallowed. Watch for a blanket `User-agent: *` / `Disallow: /` left over from staging.
- **Fix:** a minimal pattern that allows search and leaves training as a separate choice:

```text
User-agent: OAI-SearchBot
User-agent: Claude-SearchBot
User-agent: PerplexityBot
Allow: /

User-agent: *
Disallow: /admin/

Sitemap: https://example.com/sitemap.xml
```

A crawler follows only the group that names it most specifically and ignores the `*` group. So in the example above, the three named crawlers may also fetch `/admin/`. Repeat any `Disallow` lines they must obey inside their own group. [Google: how Google interprets robots.txt](https://developers.google.com/search/docs/crawling-indexing/robots/robots_txt)

### T3. User-triggered fetchers are allowed
- **Why:** `ChatGPT-User`, `Claude-User` and `Perplexity-User` fetch a page when someone asks about it, or pastes its URL.
- **Check:** they are not disallowed in robots.txt, and your firewall doesn't challenge them (T5).

### T4. Training crawlers are a deliberate choice
- **Why:** `GPTBot`, `ClaudeBot`, `Google-Extended` and `Applebot-Extended` govern training use. OpenAI, Google and Apple each document that these rules are separate from search inclusion.
- **Check:** decide, write the decision down, and make robots.txt match it. Neither choice is wrong. Blocking training while allowing search is a common, documented setup.

### T5. CDN, firewall and bot protection let crawlers through
- **Why:** Google's AI-features page lists "ensuring that crawling is allowed in robots.txt, and by any CDN or hosting infrastructure". Bot-management products can block or challenge AI crawlers even when robots.txt allows them.
- **Check:** review your CDN's bot or AI-crawler settings and your server logs for `403`, `429` or challenge responses to these agents. You can't test this honestly from outside by faking a user agent, because many providers verify crawlers by IP.
- **Fix:** allow the verified crawlers. OpenAI publishes IP ranges (`openai.com/searchbot.json`, `openai.com/chatgpt-user.json`, `openai.com/gptbot.json`). [OpenAI](https://developers.openai.com/api/docs/bots)

### T6. Key pages are indexable
- **Why:** to appear as a supporting link in AI Overviews or AI Mode, a page must be "indexed and eligible to be shown in Google Search with a snippet". [Google: AI features](https://developers.google.com/search/docs/appearance/ai-features)
- **Check:**
  - no `noindex` in the robots meta tag or the `X-Robots-Tag` header;
  - the page returns `200`, not a redirect chain or soft 404;
  - the URL Inspection tool in Search Console shows it indexed.

### T7. Snippet controls are intentional
- **Why:** Google says `nosnippet` "will also prevent the content from being used as a direct input for AI Overviews and AI Mode". `max-snippet` limits how much can be used. [Google: robots meta tag](https://developers.google.com/search/docs/crawling-indexing/robots-meta-tag)
- **Bing:** content tagged `NOARCHIVE` "will not be included in Bing Chat answers". `NOCACHE` limits answers to the URL, title and snippet. Bing documented this in 2023, for what is now Copilot. [Bing](https://blogs.bing.com/webmaster/september-2023/Announcing-new-options-for-webmasters-to-control-usage-of-their-content-in-Bing-Chat)
- **Check:** look for `nosnippet`, `max-snippet:0` or low values, `noarchive` and `nocache` in meta tags and headers. Look for `data-nosnippet` on main content.
- **Fix:** remove them from pages you want quoted. Keep them where you don't.

### T8. Main content is in the HTML the server sends
- **Why:** Google says "not all bots can run JavaScript" and server-side or pre-rendering is "still a great idea". [Google: JavaScript SEO basics](https://developers.google.com/search/docs/crawling-indexing/javascript/javascript-seo-basics)
- **Check:** fetch the raw HTML (`curl -sL https://example.com/page`) and search it for the page's first paragraph and its H1. If they are missing, the page relies on client-side rendering.
- **Fix:** server-side rendering, static generation or pre-rendering for content pages.

### T9. Canonical tags point at the page you want cited
- **Check:** `<link rel="canonical">` is absolute, points at itself on the preferred URL, and doesn't point at the home page from every page. [Google: canonical URLs](https://developers.google.com/search/docs/crawling-indexing/consolidate-duplicate-urls)

### T10. Important pages are reachable through internal links
- **Why:** Google lists "making your content easily findable through internal links". Orphan pages are found late or not at all.
- **Check:** each money page and answer page is linked from navigation, a hub page or related articles.

### T11. An XML sitemap exists, is listed in robots.txt, and has honest `lastmod`
- **Why:** Google uses `<lastmod>` only when it is "consistently and verifiably" accurate, and ignores `<priority>` and `<changefreq>`. [Google: build a sitemap](https://developers.google.com/search/docs/crawling-indexing/sitemaps/build-sitemap)
- **Check:** the `Sitemap:` line in robots.txt resolves to valid XML. Each file holds at most 50,000 URLs or 50 MB uncompressed. The `lastmod` dates change only when the content does.

### T12. Search Console and Bing Webmaster Tools are set up
- **Why:** both show crawl and index errors, and both report on AI features. Search Console has a Generative AI performance report ([Google](https://developers.google.com/search/docs/fundamentals/ai-optimization-guide)). Bing Webmaster Tools has AI Performance, which shows citations in Copilot and Bing's AI summaries ([Bing](https://blogs.bing.com/webmaster/February-2026/Introducing-AI-Performance-in-Bing-Webmaster-Tools-Public-Preview)).
- **Check:** both are verified for the right property, and the sitemap is submitted in each.

### T13. IndexNow pings on publish and update
- **Why:** one ping notifies every participating engine. The current list is Bing, Yandex, Seznam, Naver, Yep, the Internet Archive and Amazonbot. Google is not on it. [IndexNow docs](https://www.indexnow.org/documentation), [participants](https://www.indexnow.org/searchengines.json)
- **Check:** a key file `https://example.com/<key>.txt` exists and contains the key. Your CMS or CDN sends a ping when pages change.

### T14. `llms.txt` is optional
- **What it is:** a 2024 proposal for a Markdown file at `/llms.txt` that lists a site's key pages for language models. Only the H1 is required. [llmstxt.org](https://llmstxt.org/)
- **What we know:** Google says you don't need "new machine readable files, AI text files, markup, or Markdown to appear in Google Search", and that such files "will neither harm nor help" there. [Google](https://developers.google.com/search/docs/fundamentals/ai-optimization-guide) No major engine documents that it reads `llms.txt` for search.
- **Our view:** cheap to add, fine to skip. Never treat it as a substitute for T1 to T13. More: [Cited: llms.txt guide](https://cited.io/guides/llms-txt)

## Sources

- [OpenAI: Overview of OpenAI crawlers](https://developers.openai.com/api/docs/bots)
- [Anthropic: crawler documentation](https://support.claude.com/en/articles/8896518-does-anthropic-crawl-data-from-the-web-and-how-can-site-owners-block-the-crawler)
- [Perplexity: crawlers](https://docs.perplexity.ai/guides/bots)
- [Google: common crawlers and Google-Extended](https://developers.google.com/crawling/docs/crawlers-fetchers/google-common-crawlers)
- [Google: AI features and your website](https://developers.google.com/search/docs/appearance/ai-features)
- [Google: robots meta tag and X-Robots-Tag](https://developers.google.com/search/docs/crawling-indexing/robots-meta-tag)
- [Google: JavaScript SEO basics](https://developers.google.com/search/docs/crawling-indexing/javascript/javascript-seo-basics)
- [Google: build and submit a sitemap](https://developers.google.com/search/docs/crawling-indexing/sitemaps/build-sitemap)
- [Apple: About Applebot](https://support.apple.com/en-us/119829)
- [Bing: content controls for AI answers (2023)](https://blogs.bing.com/webmaster/september-2023/Announcing-new-options-for-webmasters-to-control-usage-of-their-content-in-Bing-Chat)
- [IndexNow documentation](https://www.indexnow.org/documentation)
- [llmstxt.org](https://llmstxt.org/)

Checked 2026-10-15.

---

Maintained by [Cited](https://cited.io): AI SEO and GEO agency with its own AI visibility platform. More on ChatGPT's crawlers: [How to get cited by ChatGPT](https://cited.io/guides/how-to-get-cited-by-chatgpt).
