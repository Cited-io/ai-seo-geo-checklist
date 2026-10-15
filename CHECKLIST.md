# AI SEO and GEO checklist (master list)

**This is the full AI SEO, GEO and AEO checklist on one page.** Work through it top to bottom: access first, because an engine that can't read a page can't cite it. Each item has an ID, a one-line reason, and a source where a primary one exists. Items with no public source are marked *(practice)*: they are common practice, not documented rules.

Each section has a longer file under [`checklists/`](#sections) with examples and how to check each item.

Google's own guidance is that generative AI search is still SEO. It needs no special files, markup or tactics ([Google: Optimizing for generative AI features](https://developers.google.com/search/docs/fundamentals/ai-optimization-guide)). This checklist follows that line. It adds what other engines document, and what helps an engine quote and recommend a page once it has read it.

## Sections

1. [Technical access](#1-technical-access): [detail](https://github.com/Cited-io/ai-seo-geo-checklist/blob/main/checklists/technical-access.md)
2. [Entity and identity](#2-entity-and-identity): [detail](https://github.com/Cited-io/ai-seo-geo-checklist/blob/main/checklists/entity-and-identity.md)
3. [Content](#3-content): [detail](https://github.com/Cited-io/ai-seo-geo-checklist/blob/main/checklists/content.md)
4. [Off-site](#4-off-site): [detail](https://github.com/Cited-io/ai-seo-geo-checklist/blob/main/checklists/off-site.md)
5. [Local](#5-local): [detail](https://github.com/Cited-io/ai-seo-geo-checklist/blob/main/checklists/local.md)
6. [Measurement](#6-measurement): [detail](https://github.com/Cited-io/ai-seo-geo-checklist/blob/main/checklists/measurement.md)

---

## 1. Technical access

- [ ] **T1. `/robots.txt` loads and parses.** A broken or missing file leaves crawler access to defaults you didn't choose. [Google: robots.txt](https://developers.google.com/search/docs/crawling-indexing/robots/intro)
- [ ] **T2. AI search crawlers are allowed.** `OAI-SearchBot` decides whether you appear in ChatGPT search answers; `Claude-SearchBot`, `PerplexityBot`, `Googlebot`, `Bingbot` and `Applebot` feed their engines' search. [OpenAI](https://developers.openai.com/api/docs/bots), [Anthropic](https://support.claude.com/en/articles/8896518-does-anthropic-crawl-data-from-the-web-and-how-can-site-owners-block-the-crawler), [Perplexity](https://docs.perplexity.ai/guides/bots), [Apple](https://support.apple.com/en-us/119829)
- [ ] **T3. User-triggered fetchers are allowed.** `ChatGPT-User`, `Claude-User` and `Perplexity-User` visit a page when someone asks about it; Anthropic says blocking `Claude-User` stops it retrieving your content for user queries. [Anthropic](https://support.claude.com/en/articles/8896518-does-anthropic-crawl-data-from-the-web-and-how-can-site-owners-block-the-crawler)
- [ ] **T4. Training crawlers are a separate, deliberate choice.** `GPTBot`, `ClaudeBot`, `Google-Extended` and `Applebot-Extended` control training use; OpenAI, Google and Apple each say these rules are independent of search. [OpenAI](https://developers.openai.com/api/docs/bots), [Google](https://developers.google.com/crawling/docs/crawlers-fetchers/google-common-crawlers), [Apple](https://support.apple.com/en-us/119829)
- [ ] **T5. Your CDN, firewall and bot protection let those crawlers through.** robots.txt can say yes while a bot-management rule says no; Google lists "ensuring that crawling is allowed in robots.txt, and by any CDN or hosting infrastructure". [Google: AI features](https://developers.google.com/search/docs/appearance/ai-features)
- [ ] **T6. Key pages are indexable.** A page must be indexed and eligible for a snippet to be a supporting link in AI Overviews or AI Mode. [Google: AI features](https://developers.google.com/search/docs/appearance/ai-features)
- [ ] **T7. Snippet controls are intentional.** `nosnippet` and `max-snippet` (meta tag or `X-Robots-Tag` header) also limit use in AI Overviews and AI Mode; Bing's `NOARCHIVE` keeps a page out of its AI answers. [Google: robots meta tag](https://developers.google.com/search/docs/crawling-indexing/robots-meta-tag), [Bing](https://blogs.bing.com/webmaster/september-2023/Announcing-new-options-for-webmasters-to-control-usage-of-their-content-in-Bing-Chat)
- [ ] **T8. Main content is in the HTML the server sends.** Google says "not all bots can run JavaScript" and server-side or pre-rendering is "still a great idea". [Google: JavaScript SEO basics](https://developers.google.com/search/docs/crawling-indexing/javascript/javascript-seo-basics)
- [ ] **T9. Canonical tags point at the page you want cited.** Engines pick one URL per duplicate set; a wrong canonical sends credit elsewhere. [Google: canonical URLs](https://developers.google.com/search/docs/crawling-indexing/consolidate-duplicate-urls)
- [ ] **T10. Important pages are reachable through internal links.** Google lists "making your content easily findable through internal links" as an AI-features best practice. [Google: AI features](https://developers.google.com/search/docs/appearance/ai-features)
- [ ] **T11. An XML sitemap exists, is listed in robots.txt, and has honest `lastmod` dates.** Google uses `lastmod` only when it is "consistently and verifiably" accurate. [Google: build a sitemap](https://developers.google.com/search/docs/crawling-indexing/sitemaps/build-sitemap)
- [ ] **T12. The site is verified in Google Search Console and Bing Webmaster Tools, with the sitemap submitted.** Both show indexing problems, and both now report on AI features. [Search Console](https://search.google.com/search-console/about), [Bing Webmaster Tools](https://www.bing.com/webmasters/about)
- [ ] **T13. IndexNow pings on publish and update.** It notifies Bing and the other participating engines at once; Google is not a participant. [IndexNow](https://www.indexnow.org/documentation), [participants](https://www.indexnow.org/searchengines.json)
- [ ] **T14. `llms.txt` is treated as optional.** It is a proposal, not a standard; Google says such files "will neither harm nor help" visibility in Search. [llmstxt.org](https://llmstxt.org/), [Google](https://developers.google.com/search/docs/fundamentals/ai-optimization-guide)

## 2. Entity and identity

- [ ] **E1. The home page has Organization structured data in JSON-LD.** It helps Google understand who you are; Google recommends the home page and JSON-LD. [Google: Organization](https://developers.google.com/search/docs/appearance/structured-data/organization)
- [ ] **E2. `sameAs` lists every official profile.** LinkedIn, Crunchbase, YouTube, GitHub, X, Wikipedia or Wikidata where they exist, so engines can join your profiles into one entity. [Google: Organization](https://developers.google.com/search/docs/appearance/structured-data/organization), [schema.org/sameAs](https://schema.org/sameAs)
- [ ] **E3. Structured data matches what the page shows.** Google says not to add structured data about information that isn't visible to the user. [Google: structured data](https://developers.google.com/search/docs/appearance/structured-data/intro-structured-data)
- [ ] **E4. Name, one-line description, logo, address and phone match everywhere.** Engines reconcile your brand from many sites; mismatches split or confuse it. *(practice)*
- [ ] **E5. An About page says who you are, what you sell, for whom and where.** Engines need one page that answers "what is [brand]" in plain words. *(practice)*
- [ ] **E6. Authors have bylines that link to a bio.** Google asks whether it is "self-evident to your visitors who authored your content". [Google: helpful content](https://developers.google.com/search/docs/fundamentals/creating-helpful-content)
- [ ] **E7. A shared or generic name is disambiguated.** If another company uses your name, use one consistent form (such as name plus domain) on every profile. *(practice)*
- [ ] **E8. Wikipedia and Wikidata are earned, not self-written.** Wikipedia requires notability and discourages editing about yourself. [Notability](https://en.wikipedia.org/wiki/Wikipedia:Notability), [Conflict of interest](https://en.wikipedia.org/wiki/Wikipedia:Conflict_of_interest)

## 3. Content

- [ ] **C1. Each page answers its question in the first two sentences.** Engines build answers from passages, and an opening that stands alone is the easiest one to lift. *(practice)* More: [Cited: AI SEO guide](https://cited.io/guides/ai-seo)
- [ ] **C2. One question per page, phrased the way buyers ask it.** "Best payroll software for a 20-person startup" beats "Payroll solutions". *(practice)*
- [ ] **C3. Subheadings answer the follow-up questions.** AI Overviews and AI Mode may use "query fan-out", issuing multiple related searches, and each can land on a different section. [Google: AI features](https://developers.google.com/search/docs/appearance/ai-features)
- [ ] **C4. Claims carry evidence: numbers, quotations and named sources.** In the GEO paper, adding quotations, statistics and citations did best; keyword stuffing did worse than doing nothing. [Aggarwal et al., KDD 2024](https://arxiv.org/abs/2311.09735)
- [ ] **C5. The page adds something new.** Google asks whether content provides "original information, reporting, research, or analysis". [Google: helpful content](https://developers.google.com/search/docs/fundamentals/creating-helpful-content)
- [ ] **C6. Comparisons are honest and in tables.** "X vs Y" and "alternatives to X" pages answer buying questions; tables make prices and features easy to extract. *(practice)*
- [ ] **C7. Facts buyers ask about are on the page as text.** Prices, plans, features, locations and limits; Google asks that "important content is available in textual form". [Google: AI features](https://developers.google.com/search/docs/appearance/ai-features)
- [ ] **C8. Each page shows a real date and is updated for real.** Google warns against changing dates when the content "has not substantially changed". [Google: helpful content](https://developers.google.com/search/docs/fundamentals/creating-helpful-content)
- [ ] **C9. Key pages are reviewed on a schedule.** Stale prices or features get repeated by engines as fact. *(practice)*
- [ ] **C10. No mass-produced thin pages.** Many pages made "for the primary purpose of manipulating search rankings" is scaled content abuse. [Google: spam policies](https://developers.google.com/search/docs/essentials/spam-policies)
- [ ] **C11. Images and video support the text, not replace it.** Google lists high-quality images and video as a best practice alongside text. [Google: AI features](https://developers.google.com/search/docs/appearance/ai-features)

## 4. Off-site

- [ ] **O1. You know which sites engines list as sources for your prompts.** For 23 questions about AI search and GEO (138 AI answers) in our open [AI search citations dataset](https://github.com/Cited-io/ai-search-citations-dataset) (2026-10), engines listed 566 distinct domains as sources. [Measurement](https://github.com/Cited-io/ai-seo-geo-checklist/blob/main/checklists/measurement.md)
- [ ] **O2. You plan per engine.** ChatGPT listed 17.2 domains as sources per answer in our dataset; Google AI Mode listed 2.6. [Dataset](https://github.com/Cited-io/ai-search-citations-dataset)
- [ ] **O3. You collect genuine reviews on the sites your buyers read.** Never pay for a particular sentiment or ask only happy customers. [FTC rule](https://www.ftc.gov/news-events/news/press-releases/2024/08/federal-trade-commission-announces-final-rule-banning-fake-reviews-testimonials), [Google review policy](https://support.google.com/contributionpolicy/answer/7400114)
- [ ] **O4. You are on the "best X" roundups engines cite.** Engines often answer from lists you don't own; earn a place with evidence, not just a fee. *(practice)*
- [ ] **O5. You take part in Reddit honestly.** For questions about AI search and GEO, reddit.com was listed as a source in 21 of 138 answers in our dataset, and in 39.1% of Google AI Overviews answers; Reddit's rules require authentic posts and ban content manipulation. [Reddit Rules](https://redditinc.com/policies/reddit-rules)
- [ ] **O6. You publish YouTube videos that answer buyer questions.** youtube.com was listed in 13 of 138 answers on the same questions, and in 43.5% of Google AI Overviews answers; use question-style titles, chapters and accurate captions. [Chapters](https://support.google.com/youtube/answer/9884579), [Captions](https://support.google.com/youtube/answer/2734796)
- [ ] **O7. Digital PR is built on something worth citing.** Google says chasing inauthentic "mentions" "isn't as helpful as it might seem"; original data earns real ones. [Google](https://developers.google.com/search/docs/fundamentals/ai-optimization-guide)
- [ ] **O8. No link schemes.** Links made to manipulate rankings are link spam. [Google: spam policies](https://developers.google.com/search/docs/essentials/spam-policies)

## 5. Local

- [ ] **L1. Your Google Business Profile is claimed and verified.** Google says Business Profiles help you appear "in both AI responses and other Google Search results". [Claim a profile](https://support.google.com/business/answer/2911778), [Google](https://developers.google.com/search/docs/fundamentals/ai-optimization-guide)
- [ ] **L2. The profile follows Google's rules.** Real-world name with no keywords added, one profile per location, a precise address or service area, few and specific categories. [Google: guidelines](https://support.google.com/business/answer/3038177)
- [ ] **L3. Hours, categories, attributes and photos are complete, and reviews get replies.** Google ranks local results by relevance, distance and prominence. [Google: local ranking](https://support.google.com/business/answer/7091)
- [ ] **L4. Bing Places and Apple Business Connect are claimed.** Microsoft's and Apple's maps and assistants read their own business data, not Google's. *(practice)* [Bing for business](https://www.bing.com/forbusiness/), [Apple Business](https://business.apple.com/)
- [ ] **L5. Each location has its own page with LocalBusiness structured data.** One page per place, with its address, hours and phone. [Google: LocalBusiness](https://developers.google.com/search/docs/appearance/structured-data/local-business)
- [ ] **L6. Name, address and phone match on your site and every listing.** *(practice)*
- [ ] **L7. Local prompts are tested from the place your customers are.** Answers change by location. *(practice)*

## 6. Measurement

- [ ] **M1. You track a fixed set of prompts written from buyer questions.** Category, comparison, problem and local prompts, not your brand name. *(practice)*
- [ ] **M2. Each prompt runs on each engine your buyers use.** Engines read different sources (see O2). [Dataset](https://github.com/Cited-io/ai-search-citations-dataset)
- [ ] **M3. Each prompt runs more than once.** Answers vary between runs, so read trends across many answers, never one screenshot. *(practice)*
- [ ] **M4. Mentions and citations are tracked separately.** A mention names your brand; a citation links your site. You can have either without the other. *(practice)*
- [ ] **M5. You record which sources each answer lists.** That list is your off-site target list (O1). *(practice)*
- [ ] **M6. Some prompts are controls you never work on.** If worked prompts improve and controls don't, your work caused it. *(practice)*
- [ ] **M7. Every change is logged with its date.** So you can line up what you shipped with what moved. *(practice)*
- [ ] **M8. You read the first-party reports.** Google Search Console has a Generative AI performance report; Bing Webmaster Tools has AI Performance (public preview). [Google](https://developers.google.com/search/docs/fundamentals/ai-optimization-guide), [Bing](https://blogs.bing.com/webmaster/February-2026/Introducing-AI-Performance-in-Bing-Webmaster-Tools-Public-Preview)
- [ ] **M9. AI referrals are visible in your analytics.** Segment visits referred by chatgpt.com, perplexity.ai, copilot.microsoft.com, gemini.google.com and claude.ai. *(practice)*

---

## Run it with an agent

The [ai-seo-geo-audit skill](https://github.com/Cited-io/ai-seo-geo-checklist/blob/main/skills/ai-seo-geo-audit/SKILL.md) checks the items a crawler can see from outside (most of T and E, part of C and L) and reports a pass, warn or fail for each ID. Install steps: [skill README](https://github.com/Cited-io/ai-seo-geo-checklist/blob/main/skills/ai-seo-geo-audit/README.md).

## Sources

All sources were checked on 2026-10-15. "Our dataset" is Cited's open [AI search citations dataset](https://github.com/Cited-io/ai-search-citations-dataset), 2026-10 release: 138 answers (23 prompts about AI search, GEO and AI visibility tools, on 6 engines: ChatGPT, Claude, Copilot, Gemini, Google AI Overviews and Google AI Mode, asked from the US on 2026-10-14), CC BY 4.0.

---

Maintained by [Cited](https://cited.io): AI SEO and GEO agency with its own AI visibility platform. Read the long-form guide: [AI SEO and GEO, step by step](https://cited.io/guides/ai-seo).
