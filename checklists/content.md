# Content checklist for AI answers (answer-first, one question per page, evidence, comparisons, freshness)

**Write each page so its opening two sentences answer one buyer question on their own, then back the answer with evidence.** Engines build answers from passages. A passage that states the answer, names its source and carries a number is the easiest one to quote. Keep the facts current and dated, because engines repeat what they find as fact.

IDs match the [master checklist](https://github.com/Cited-io/ai-seo-geo-checklist/blob/main/CHECKLIST.md).

## What the evidence says

- **Google:** Google says generative AI search is still SEO. There is "no requirement to break your content into tiny pieces for AI to better understand it". The advice is to create unique content with "a unique point of view". [Google: Optimizing for generative AI features](https://developers.google.com/search/docs/fundamentals/ai-optimization-guide)
- **The GEO paper (KDD 2024):** this is the research paper that named generative engine optimization. It tested nine ways to rewrite a source page. The three best were adding quotations, adding statistics and citing sources, with "a relative improvement of 30-40%" on its main visibility measure. Keyword stuffing scored below the unedited baseline. The abstract sums up: GEO "can boost visibility by up to 40% in generative engine responses". [Aggarwal et al., arXiv 2311.09735](https://arxiv.org/abs/2311.09735)

Answer-first structure and one question per page are common practice, not documented rules. They follow from how engines quote passages, and they also make pages easier for people to read.

## Items

### C1. Each page answers its question in the first two sentences *(practice)*
- **Do:** open with the answer itself. Include the subject, so the sentence makes sense when quoted alone.
- **Before:** "In today's fast-moving world, choosing payroll software can be hard."
- **After:** "For a 20-person startup, the best payroll software is usually one that runs payroll, benefits and tax filing in one tool, for about $40 to $80 per employee per month (example figures)."
- **Check:** read only the first two sentences under the H1. Do they answer the H1?

### C2. One question per page, phrased the way buyers ask it *(practice)*
- **Do:** make the H1 and title the question or its answer, in buyer words: "best X for Y", "X vs Y", "how much does X cost", "how to fix Z".
- **Avoid:** one page that tries to rank for ten loosely related questions.
- **Find the questions:** sales calls, support tickets, Search Console queries, "People also ask", and the prompts you track (see [measurement](https://github.com/Cited-io/ai-seo-geo-checklist/blob/main/checklists/measurement.md)).

### C3. Subheadings answer the follow-up questions
- **Why:** Google says AI Overviews and AI Mode may use "query fan-out", issuing multiple related searches to answer one question. Each search can match a different section. [Google: AI features](https://developers.google.com/search/docs/appearance/ai-features)
- **Do:** write H2s as the natural next questions ("How much does it cost?", "Is it good for teams under 10?"), each answered in its first sentence.

### C4. Claims carry evidence: numbers, quotations and named sources
- **Why:** these three did best in the GEO paper (above).
- **Do:**
  - put a number in the claim, with its date: "plans start at $40 a month (October 2026)";
  - quote a named expert or customer, with their role;
  - link the primary source for any statistic.
- **Avoid:** repeating the target phrase to "optimize". Keyword stuffing did worse than nothing in the paper.

### C5. The page adds something new
- **Why:** Google asks, "Does the content provide original information, reporting, research, or analysis?" [Google: helpful content](https://developers.google.com/search/docs/fundamentals/creating-helpful-content)
- **Do:** add your own data, test results, pricing tables, screenshots or customer numbers. A rewrite of the top five results gives an engine no reason to pick you.

### C6. Comparisons are honest and in tables *(practice)*
- **Why:** "X vs Y" and "alternatives to X" are decision-stage questions, and engines answer them from comparison pages. Tables make prices and features easy to extract.
- **Do:**
  - compare on the criteria buyers use;
  - say where a competitor is the better choice;
  - date the table;
  - link each competitor's pricing page.

### C7. Facts buyers ask about are on the page as text
- **Why:** Google asks that "important content is available in textual form". [Google: AI features](https://developers.google.com/search/docs/appearance/ai-features)
- **Do:** publish prices or price ranges, plan limits, integrations, locations, hours and eligibility in HTML text. Don't leave them only in images, PDFs, tabs that need JavaScript, or behind a "contact sales" form.

### C8. Each page shows a real date and is updated for real
- **Why:** Google lists "changing the date of pages to make them seem fresh when the content has not substantially changed" as a warning sign. [Google: helpful content](https://developers.google.com/search/docs/fundamentals/creating-helpful-content)
- **Do:** show "Updated" dates only for substantive changes. Keep the sitemap `lastmod` in step (see T11 in [technical access](https://github.com/Cited-io/ai-seo-geo-checklist/blob/main/checklists/technical-access.md)).

### C9. Key pages are reviewed on a schedule *(practice)*
- **Why:** an engine that read your old price will quote it.
- **Do:** list your pricing, product, comparison and top answer pages. Review them monthly or whenever a fact changes.

### C10. No mass-produced thin pages
- **Why:** Google defines scaled content abuse as "when many pages are generated for the primary purpose of manipulating search rankings". [Google: spam policies](https://developers.google.com/search/docs/essentials/spam-policies)
- **Do:** publish fewer pages, each with something only you can say. Generated drafts are fine if a person adds facts and checks them.

### C11. Images and video support the text
- **Why:** Google lists "supporting your textual content with high-quality images and videos, when applicable" among AI-features best practices. [Google: AI features](https://developers.google.com/search/docs/appearance/ai-features)
- **Do:** use descriptive alt text, captions and on-page transcripts for videos.

## A quick page template

```markdown
# Best payroll software for a 20-person startup (2026)

For a 20-person startup, the best payroll software is usually ... [the answer in 40 to 60 words]

## How we compared them
[criteria, date, who tested]

## Comparison table
| Tool | Price from | Benefits | Tax filing | Best for |

## How much does payroll software cost?
[answer first, then detail]

## Which is best for a team under 10?
[answer first, then detail]

## Sources
[primary links]

Updated 2026-10-15 by [Name], [role]
```

## Sources

- [Google: Optimizing for generative AI features](https://developers.google.com/search/docs/fundamentals/ai-optimization-guide)
- [Google: AI features and your website](https://developers.google.com/search/docs/appearance/ai-features)
- [Google: Creating helpful, reliable, people-first content](https://developers.google.com/search/docs/fundamentals/creating-helpful-content)
- [Google: Spam policies](https://developers.google.com/search/docs/essentials/spam-policies)
- [Aggarwal et al., "GEO: Generative Engine Optimization", KDD 2024](https://arxiv.org/abs/2311.09735)

Checked 2026-10-15.

---

Maintained by [Cited](https://cited.io): AI SEO and GEO agency with its own AI visibility platform. More on what GEO is: [What is generative engine optimization](https://cited.io/guides/what-is-generative-engine-optimization).
