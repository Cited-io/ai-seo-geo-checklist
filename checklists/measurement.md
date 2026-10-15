# Measurement checklist for AI visibility (tracked prompts, repeated runs, control prompts)

**Measure AI visibility by asking a fixed set of buyer prompts on each engine, more than once, and reading the trend across many answers.** One screenshot proves nothing, because answers change between runs and differ by engine and location. Track mentions and citations separately. Record the sources each answer lists. Keep some prompts as untouched controls, so you can tell your own work apart from noise.

IDs match the [master checklist](https://github.com/Cited-io/ai-seo-geo-checklist/blob/main/CHECKLIST.md).

## Items

### M1. You track a fixed set of prompts written from buyer questions *(practice)*
- **Why:** every number you report comes from these prompts, so the prompts decide what the number means.
- **Do:** write prompts the way buyers ask, not your brand name. Group them:
  - **Category:** "best CRM for a 10-person agency". This is where shortlists form.
  - **Comparison:** "HubSpot vs Pipedrive", "alternatives to Salesforce". This is where buyers decide.
  - **Problem:** "how do I stop leads going cold". This is where buyers first meet a solution.
  - **Local:** "emergency plumber near Bedford Ave", asked from that place.
- **Keep it fixed:** change the set rarely, and note the date when you do. A trend over a changing set measures the set, not you.

### M2. Each prompt runs on each engine your buyers use
- **Why:** engines read different sources. In the 2026-10 release of our open [AI search citations dataset](https://github.com/Cited-io/ai-search-citations-dataset) (23 questions about AI search and GEO), ChatGPT listed 17.2 domains as sources per answer and Google AI Mode listed 2.6. A result on one engine says little about another.
- **Engines to consider:** ChatGPT, Google AI Overviews, Google AI Mode, Gemini, Perplexity, Microsoft Copilot and Claude.

### M3. Each prompt runs more than once *(practice)*
- **Why:** the same prompt can name different brands on two runs a minute apart.
- **Do:** run on a schedule, such as weekly, and report shares over many answers. Look at trends over weeks, not single days.

### M4. Mentions and citations are tracked separately *(practice)*
- **Mention:** the answer names your brand. It tells you whether you are recommended.
- **Citation:** the answer lists your site as a source. It tells you whether your own pages are doing the work.
- **Why separate:** you can be mentioned without being cited, when an engine learned about you from a review site. You can also be cited without being mentioned, when your page supports a general fact.

### M5. You record which sources each answer lists *(practice)*
- **Why:** this list shows where engines get their answers, and it becomes your off-site target list (O1 in the [off-site checklist](https://github.com/Cited-io/ai-seo-geo-checklist/blob/main/checklists/off-site.md)).
- **Do:** store the domain and the full URL for every source, per prompt, engine and run.

### M6. Some prompts are controls you never work on *(practice)*
- **Why:** engines change their models and sources all the time. Controls show that background movement.
- **Do:** pick prompts like the ones you work on, and leave them untouched. If the worked prompts rise and the controls don't, your work is the likely cause. If both rise, it was probably the engine.

### M7. Every change is logged with its date *(practice)*
- **Do:** keep a changelog of what you shipped, and when: a new page, a rewritten intro, a new review profile, a listing fix. Line it up with the trend.
- **Also:** run local prompts from the city your customers are in, and in their language. Answers change with both.

### M8. You read the first-party reports
- **Google Search Console:** it has a Generative AI performance report. It shows how people discover your content through generative AI features in Google Search and Discover. AI Overviews and AI Mode traffic is also counted in the overall Performance report, under the "Web" search type. [Google: Optimizing for generative AI features](https://developers.google.com/search/docs/fundamentals/ai-optimization-guide), [Google: AI features](https://developers.google.com/search/docs/appearance/ai-features)
- **Bing Webmaster Tools:** AI Performance (public preview since February 2026) shows how often your pages are cited in Microsoft Copilot, Bing's AI summaries and some partner integrations. It also shows sample grounding queries. [Bing](https://blogs.bing.com/webmaster/February-2026/Introducing-AI-Performance-in-Bing-Webmaster-Tools-Public-Preview)

### M9. AI referrals are visible in your analytics *(practice)*
- **Do:** create a segment or channel for visits referred by AI products, such as chatgpt.com, perplexity.ai, copilot.microsoft.com, gemini.google.com and claude.ai.
- **Caveat:** app traffic may arrive with no referrer, so treat these numbers as a floor, not a total.

## The numbers worth reporting

Each number below is a share or an average across many answers to your tracked prompts. How you compute them depends on your tool; what they mean is:

| Number | What it tells you |
|---|---|
| **Visibility** | How often answers name your brand at all |
| **Position** | Where you appear when you're named: first, or fourth in a list |
| **Share of voice** | How much of the conversation you hold against the competitors you track |
| **Sentiment** | Whether answers describe you favorably, neutrally or negatively |
| **Citations** | How often answers list your own site as a source |

Report each one per engine and per prompt group, and against two or three competitors. A visibility of 30% means little alone. Next to competitors at 10% and 60%, it tells you where you stand.

## Sources

- [Google: Optimizing for generative AI features](https://developers.google.com/search/docs/fundamentals/ai-optimization-guide)
- [Google: AI features and your website](https://developers.google.com/search/docs/appearance/ai-features)
- [Bing: Introducing AI Performance in Bing Webmaster Tools](https://blogs.bing.com/webmaster/February-2026/Introducing-AI-Performance-in-Bing-Webmaster-Tools-Public-Preview)
- [Cited: AI search citations dataset, 2026-10 release (CC BY 4.0)](https://github.com/Cited-io/ai-search-citations-dataset)

Checked 2026-10-15.

---

Maintained by [Cited](https://cited.io): AI SEO and GEO agency with its own AI visibility platform. Longer guide: [How to measure AI visibility](https://cited.io/guides/how-to-measure-ai-visibility).
