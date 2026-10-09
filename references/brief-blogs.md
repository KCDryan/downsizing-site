# Brief: 10 keyword-targeted guides (October 2026)

Read first: playbook/content.md (binding: accuracy, copy rules, guide format), notes/brief.md,
notes/brief-boroughs.md (NYC voice), notes/ny-tax-facts.md, notes/ny-law-facts.md.
Dates: published and updated '2026-10-01', "Updated October 2026".

## SEO requirements for each guide
- Target the PRIMARY keyword given in your task. Before writing, run WebSearch on it and note
  the "People also ask" style questions and the angles of the top results; cover those
  questions better and more specifically for New York.
- Primary keyword (or a natural close variant) in: the title (50 to 60 chars, keyword near
  the front), the H1, the first 100 words, at least one H2, and the meta description
  (140 to 158 chars, written as a reason to click). Slug is given; keep it.
- Secondary keywords in H2s and naturally in the body. No stuffing: read aloud, it must sound
  like a person.
- 1,800 to 2,500 words. 6 to 9 H2s. Short paragraphs (under 110 words). Use a table where
  comparing options, a `checklist` list for steps, a `note` box for the not-advice line.
- 5 or 6 FAQs, each a real question people search, answered in 40 to 90 words, answer first.
- At least 5 internal links: relevant existing guides, /net-proceeds-calculator/,
  /costs-and-money/, /where-to-downsize/ or a borough page, /55-plus-communities/ when
  relevant, /resources/, and /get-matched/ once near the end.
- article.summary under 180 chars. crumb short (under 35 chars).

## Accuracy
Same rules as always: every fact from a page you read, official sources first, tax/law figures
from the fact sheets or official pages you fetched, no invented numbers, no prices or market
stats, no research-process narration on the page. If unverifiable, do not say it; tell the
reader who to ask. Flag anything legal for a New York attorney.

## Existing guides you can link (paths)
/guides/new-york-senior-property-tax-exemptions/, /guides/estimating-net-proceeds/,
/guides/buy-first-or-sell-first/, /guides/buying-a-co-op-or-condo-in-new-york-city/,
/guides/new-york-seller-disclosures/, /guides/flood-and-storm-insurance-when-downsizing/,
/guides/preparing-an-older-new-york-home-to-sell/, /guides/aging-in-place-vs-downsizing/,
/guides/helping-a-parent-downsize-in-new-york/, /guides/estate-sale-consignment-or-donation/,
/guides/moving-day-in-new-york-city/, /guides/co-op-condo-townhouse-or-house/,
/guides/getting-around-new-york-city-after-65/
New guides being written at the same time (you may link them):
/guides/how-to-sell-a-co-op-in-nyc/, /guides/flip-tax-nyc/,
/guides/nyc-transfer-tax-and-mansion-tax/, /guides/selling-a-parents-house-in-new-york/,
/guides/capital-gains-tax-selling-a-home-in-new-york/,
/guides/reverse-mortgage-or-downsize-new-york/, /guides/downsizing-tips-for-seniors-nyc/,
/guides/senior-housing-options-nyc/, /guides/sell-or-rent-out-your-nyc-home/,
/guides/moving-from-nyc-to-florida/

## Checks and report
`node --check`, `node build.mjs`, `node tests/content.check.mjs` (fix YOUR files only; missing
share cards and links to the sibling guides above that are not written yet are expected).
Report in under 200 words: files, word counts, primary keyword placement, claims cut, main sources.
