# Entity and identity checklist for AI search (Organization schema, sameAs, consistent profiles)

**An AI engine has to know which company you are before it can recommend you.** It builds that picture from your site and from every profile that describes you. So give it three things. Organization markup on your home page that names your official profiles. The same name, description and contact details everywhere. And one page that says plainly what you do.

IDs match the [master checklist](https://github.com/Cited-io/ai-seo-geo-checklist/blob/main/CHECKLIST.md).

## Items

### E1. The home page has Organization structured data in JSON-LD
- **Why:** Google says Organization markup can "help Google better understand your organization's administrative details". It recommends the home page, or a single page about the organization. It also recommends JSON-LD "if your site's setup allows it". There are no required properties; add the ones that apply. [Google: Organization](https://developers.google.com/search/docs/appearance/structured-data/organization), [Google: intro to structured data](https://developers.google.com/search/docs/appearance/structured-data/intro-structured-data)
- **Check:** view the home page source and find `<script type="application/ld+json">` with `"@type": "Organization"` (or a subtype such as `LocalBusiness`). Paste the page into the [Rich Results Test](https://search.google.com/test/rich-results) or the [Schema Markup Validator](https://validator.schema.org/).
- **Example:**

```json
{
  "@context": "https://schema.org",
  "@type": "Organization",
  "name": "Example Co",
  "url": "https://example.com",
  "logo": "https://example.com/logo.png",
  "description": "Payroll software for startups with 5 to 200 employees.",
  "sameAs": [
    "https://www.linkedin.com/company/example-co",
    "https://www.crunchbase.com/organization/example-co",
    "https://www.youtube.com/@exampleco",
    "https://github.com/example-co"
  ]
}
```

### E2. `sameAs` lists every official profile
- **Why:** `sameAs` is "the URL of a page on another website with additional information about your organization". It tells engines that these profiles are the same entity as your site. [Google: Organization](https://developers.google.com/search/docs/appearance/structured-data/organization), [schema.org/sameAs](https://schema.org/sameAs)
- **Check:** every URL in `sameAs` resolves and is an official profile you control or one that describes you, such as Wikipedia or Wikidata. Profiles you own link back to your domain.
- **Common misses:** a LinkedIn company page, Crunchbase, G2 or Capterra, YouTube, GitHub, an app store listing.

### E3. Structured data matches what the page shows
- **Why:** Google says "don't add structured data about information that is not visible to the user, even if the information is accurate". Markup about content "hidden from the user" can bring a manual action, and the page then loses eligibility for rich results. [Google: intro to structured data](https://developers.google.com/search/docs/appearance/structured-data/intro-structured-data), [Google: structured data policies](https://developers.google.com/search/docs/appearance/structured-data/sd-policies)
- **Check:** the name, logo, address and phone in the markup match the page footer or contact page. Ratings in markup are visible on the page.

### E4. Name, description, logo, address and phone match everywhere *(practice)*
- **Why:** engines describe you by combining many sources. If LinkedIn says "HR platform", your site says "payroll software" and a directory has an old address, answers inherit the mix.
- **Check:** list your top 10 profiles (LinkedIn, Crunchbase, G2, Google Business Profile, app stores, social accounts). Compare the name, the one-line description, the logo, the URL and the contact details.
- **Fix:** write one canonical one-line description and use it everywhere.

### E5. An About page says who you are, what you sell, for whom and where *(practice)*
- **Why:** "What is [brand]?" is one of the first questions buyers ask an engine. A page that answers it in two plain sentences is the easiest source to use.
- **Check:** the About page opens with a definition ("Example Co is payroll software for…"), not a mission statement. It names your founders or team, location and year founded where relevant.

### E6. Authors have bylines that link to a bio
- **Why:** Google asks, "Is it self-evident to your visitors who authored your content?" It also asks, "Do bylines lead to further information about the author or authors involved?" [Google: helpful content](https://developers.google.com/search/docs/fundamentals/creating-helpful-content)
- **Check:** articles show a named author linked to a bio with real credentials. No invented authors.

### E7. A shared or generic name is disambiguated *(practice)*
- **Why:** if another company or product uses your name, engines can merge you or pick the wrong one.
- **Fix:**
  - use one consistent distinguishing form, such as name plus domain ("Example (example.com)"), on profiles and in your own copy;
  - keep `sameAs` complete so engines can tell which profiles are yours;
  - put a clear definition on the About page.

### E8. Wikipedia and Wikidata are earned, not self-written
- **Why:** Wikipedia articles require notability shown by independent sources. Wikipedia strongly discourages writing about your own company. [Notability](https://en.wikipedia.org/wiki/Wikipedia:Notability), [Conflict of interest](https://en.wikipedia.org/wiki/Wikipedia:Conflict_of_interest)
- **Check:** if you qualify, make sure the facts on existing pages are current. Raise corrections on the talk page, with sources, and disclose your affiliation. Wikidata has its own notability policy. [Wikidata: Notability](https://www.wikidata.org/wiki/Wikidata:Notability)

## Sources

- [Google: Organization structured data](https://developers.google.com/search/docs/appearance/structured-data/organization)
- [Google: Introduction to structured data](https://developers.google.com/search/docs/appearance/structured-data/intro-structured-data)
- [Google: Structured data general guidelines](https://developers.google.com/search/docs/appearance/structured-data/sd-policies)
- [Google: Creating helpful, reliable, people-first content](https://developers.google.com/search/docs/fundamentals/creating-helpful-content)
- [schema.org: sameAs](https://schema.org/sameAs)
- [Wikipedia: Notability](https://en.wikipedia.org/wiki/Wikipedia:Notability) and [Conflict of interest](https://en.wikipedia.org/wiki/Wikipedia:Conflict_of_interest)

Checked 2026-10-15.

---

Maintained by [Cited](https://cited.io): AI SEO and GEO agency with its own AI visibility platform. Terms used here are defined in the [AI search glossary](https://cited.io/guides/ai-search-glossary).
