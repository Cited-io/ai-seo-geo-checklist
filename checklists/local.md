# Local checklist for AI search (Google Business Profile, Bing Places, Apple Business, listings)

**For "near me" questions, AI engines lean on business listings, so a complete, verified, rule-following listing on Google, Bing and Apple comes first.** Google says Business Profiles can help your business be visible "in both AI responses and other Google Search results". After the listings, give each location its own page, with matching details and LocalBusiness markup.

IDs match the [master checklist](https://github.com/Cited-io/ai-seo-geo-checklist/blob/main/CHECKLIST.md).

## Items

### L1. Your Google Business Profile is claimed and verified
- **Why:** Google says Merchant Center and Business Profiles "can help your products and services to be visible in both AI responses and other Google Search results". Its AI-features page also lists keeping Business Profile information up to date as a best practice. [Google: Optimizing for generative AI features](https://developers.google.com/search/docs/fundamentals/ai-optimization-guide), [Google: AI features](https://developers.google.com/search/docs/appearance/ai-features)
- **Do:** claim or create the profile and complete verification. [Google: add or claim your Business Profile](https://support.google.com/business/answer/2911778)

### L2. The profile follows Google's rules
- **Rules:** [Google: guidelines for representing your business](https://support.google.com/business/answer/3038177)
  - **Name:** "Your name should reflect your business's real-world name." Adding keywords, taglines or locations to the name isn't permitted.
  - **One profile:** "There should only be one profile per business." Don't create more than one page for each location.
  - **Address:** use a precise address or service area. P.O. boxes at remote locations aren't acceptable.
  - **Categories:** "use as few categories as possible", as specific as possible but representative of your main business.

### L3. Hours, categories, attributes and photos are complete, and reviews get replies
- **Why:** Google ranks local results by relevance, distance and prominence. "More reviews and positive ratings can help your business's local ranking." [Google: local ranking](https://support.google.com/business/answer/7091)
- **Do:**
  - keep regular and special hours current;
  - add products or services and attributes;
  - post real photos;
  - reply to reviews.
- Follow the review rules in O3 of the [off-site checklist](https://github.com/Cited-io/ai-seo-geo-checklist/blob/main/checklists/off-site.md).

### L4. Bing Places and Apple Business are claimed *(practice)*
- **Why:** Microsoft's and Apple's maps and assistants read their own business data, not Google's.
- **Do:** claim and complete your listings in [Bing Places for Business](https://www.bing.com/forbusiness/) and [Apple Business Connect](https://business.apple.com/), with the same details as Google.

### L5. Each location has its own page with LocalBusiness structured data
- **Why:** a page per location gives engines one place to read that location's address, hours, phone and services. Google supports `LocalBusiness` markup for these details. [Google: LocalBusiness](https://developers.google.com/search/docs/appearance/structured-data/local-business)
- **Check:**
  - each location page has `LocalBusiness`, or a more specific type, in JSON-LD;
  - it includes `name`, `address`, `telephone`, `openingHoursSpecification` and `url`;
  - every value matches the visible page and the Business Profile.
- **Example:**

```json
{
  "@context": "https://schema.org",
  "@type": "Dentist",
  "name": "Example Dental Bedford Ave",
  "url": "https://example.com/locations/bedford-ave",
  "telephone": "+1-718-555-0100",
  "address": {
    "@type": "PostalAddress",
    "streetAddress": "100 Bedford Ave",
    "addressLocality": "Brooklyn",
    "addressRegion": "NY",
    "postalCode": "11211",
    "addressCountry": "US"
  },
  "openingHoursSpecification": [{
    "@type": "OpeningHoursSpecification",
    "dayOfWeek": ["Monday", "Tuesday", "Wednesday", "Thursday", "Friday"],
    "opens": "09:00",
    "closes": "18:00"
  }]
}
```

### L6. Name, address and phone match on your site and every listing *(practice)*
- **Why:** when sources disagree, engines may show the wrong phone or an old address, or treat two listings as two businesses.
- **Do:** list every directory that mentions you: the map platforms, industry directories and local chambers. Fix mismatches and merge duplicates.

### L7. Local prompts are tested from the place your customers are *(practice)*
- **Why:** local answers change with the searcher's location, so a check from your office says little about a customer across town.
- **Do:** set the location and language for local prompts when you track them (M7 in [measurement](https://github.com/Cited-io/ai-seo-geo-checklist/blob/main/checklists/measurement.md)).

## Sources

- [Google: Optimizing for generative AI features](https://developers.google.com/search/docs/fundamentals/ai-optimization-guide)
- [Google: AI features and your website](https://developers.google.com/search/docs/appearance/ai-features)
- [Google Business Profile: guidelines](https://support.google.com/business/answer/3038177)
- [Google Business Profile: local ranking](https://support.google.com/business/answer/7091)
- [Google Business Profile: add or claim](https://support.google.com/business/answer/2911778)
- [Google: LocalBusiness structured data](https://developers.google.com/search/docs/appearance/structured-data/local-business)

Checked 2026-10-15.

---

Maintained by [Cited](https://cited.io): AI SEO and GEO agency with its own AI visibility platform. Its done-for-you service starts from $1,497 per location per month: [pricing](https://cited.io/pricing).
