# Writer brief: New York Downsizing (read in full, after playbook/content.md)

Site: newyorkdownsizing.com. `c.city` = New York, `c.state` = New York, `c.stateAbbr` = NY,
`c.county` = New York County, `c.region` = Long Island, `c.brokerage` = eXp Realty,
`c.brand` = New York Downsizing. Published/updated date for every new page: 2026-09-29
("Updated September 2026").

## Hard rules on top of playbook/content.md
- Write ONLY the files assigned to you. Do not edit any other file, do not run git, do not
  run scripts other than `node --check`, `node build.mjs` and `node tests/content.check.mjs`.
- The content check lists problems for every page on the site. Only fix problems in YOUR files.
  Other pages are being rewritten by other people in parallel.
- These words must never appear anywhere in your files (template leftovers): Tampa,
  Hillsborough, Pasco, Florida, Save Our Homes.
- Florida concepts do not exist here: no homestead exemption, no portability, no CDD, no
  documentary stamps, no estoppel, no hurricane shutters talk. New York has none of them.
- Format reference ONLY (never copy facts): the Tampa site's pages at
  /Users/ryanchan/tampadownsizing/src/pages/ show the tone, structure and markup quality
  expected.
- Every fact you state needs a source you read. Law/tax/hazard facts: use the verified fact
  sheets below and cite their URLs; do not re-derive them differently. Anything marked
  UNVERIFIED in a fact sheet must not be asserted.
- Mark anything you cannot verify with `${V('what to check')}` while drafting, then resolve
  it before you finish (verify, or cut and tell the reader what to ask). Report every cut.
- No prices, medians, appreciation, days-on-market, drive times, or crime/safety statements.
- Fair housing: describe homes and amenities, never who should live there.

## Verified fact sheets (the single source for law, tax and hazards)
- notes/ny-law-facts.md: disclosure (PCDA excludes condos and co-ops), co-ops, condos, HOAs,
  HOPA, NYPIUA, C-MAP, NFIP, evacuation zones, Sandy, attorneys, aging services.
- notes/ny-tax-facts.md: transfer taxes, STAR, SCHE, RPTL 467, co-op/condo abatement, capital
  gains, estate tax. Complete. Do not research tax law yourself; if it is not in this file,
  do not state it.
- notes/ny-resources.md: verified move managers, donation, DSNY disposal, aging, legal.

## Links you may use (confirmed)
- NYC hurricane evacuation zone finder: https://finder.nyc.gov/hurricane (explanation:
  https://www.nyc.gov/site/em/ready/hurricane-evacuation.page). Six zones, updated 2021.
- FEMA Flood Map Service Center: https://msc.fema.gov/portal/home (FEMA calls it the
  official source; https://www.fema.gov/flood-maps).
- NYC flood maps context: https://www.nyc.gov/site/floodmaps/index.page
- FloodHelpNY: https://floodhelpny.org/en
- Suffolk storm surge zone map: https://suffolkcountyny.gov/Departments/FRES/Office-of-Emergency-Management/Storm-Surge-Zone-Interactive-Map
- Nassau County: no evacuation lookup could be verified (the county site blocks our fetches).
  For Nassau places, link FEMA MSC and tell the reader to confirm evacuation and storm
  surge information with Nassau County's emergency management office. Do not invent a URL.
- DOS property condition disclosure form (2025 PDF): https://dos.ny.gov/system/files/documents/2025/05/dos-1614-f-property-condition-disclosure-statement_04.2025-eff.-07.2025.pdf

## Internal pages (link to these; all exist at launch)
/downsizing-guide/ (step-by-step plan), /where-to-downsize/, /55-plus-communities/,
/costs-and-money/, /resources/, /net-proceeds-calculator/ (NYS + NYC transfer tax net
proceeds calculator), /get-matched/ (link once, near the end).

Neighborhoods, /where-to-downsize/SLUG/ (menu order):
1 upper-west-side, 2 upper-east-side, 3 battery-park-city, 4 murray-hill-kips-bay,
5 brooklyn-heights, 6 bay-ridge, 7 forest-hills, 8 bayside, 9 riverdale, 10 jackson-heights

55+ communities (Long Island), /55-plus-communities/SLUG/ (menu order):
1 greens-at-half-hollow, 2 country-pointe-plainview, 3 harborview-port-washington,
4 seasons-at-dix-hills, 5 country-pointe-preserve, 6 beechwood-at-the-waterways,
7 polo-club-at-islandia, 8 westhampton-pines

Guides, /guides/SLUG/:
new-york-senior-property-tax-exemptions, estimating-net-proceeds, buy-first-or-sell-first,
buying-a-co-op-or-condo-in-new-york-city, new-york-seller-disclosures,
flood-and-storm-insurance-when-downsizing, preparing-an-older-new-york-home-to-sell,
aging-in-place-vs-downsizing, helping-a-parent-downsize-in-new-york,
estate-sale-consignment-or-donation, moving-day-in-new-york-city,
co-op-condo-townhouse-or-house

## Photos
Neighborhood pages already have photos keyed by slug; nothing to do. 55+ pages have none.

## Glance box for place pages
Replace the playbook's "Evacuation zone" row with the right lookup: NYC finder for the five
boroughs, Suffolk storm surge map for Suffolk, FEMA MSC for Nassau.

## Report back (under 250 words)
Files and word counts, every claim you cut, any `V()` left and why, main sources.
