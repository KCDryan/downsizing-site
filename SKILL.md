---
name: downsizing-site
description: Launch a complete "<City> Downsizing" lead-generation website for a new city, end to end - scaffold from the newest city repo, research the state's law, write neighborhoods, 55+ communities and guides with verified facts, source and check photos, SEO, deploy to Cloudflare Pages, connect the domain, lead email and indexing, then add keyword-targeted blog guides. Use when the owner says "launch a downsizing site for [city]", "new downsizing site", "do [city] downsizing", "recreate the New York site for another city", or invokes /downsizing-site.
---

# Downsizing site for a new city

The full procedure that built newyorkdownsizing.com (October 2026), in the order it worked.
Follow it start to finish. Stop and ask the owner only where a step says **ASK**.

## 0. Inputs (ask once, in one message, for anything missing)

```
CITY, STATE, STATE_ABBR, CORE_COUNTY
BROKERAGE                      (e.g. eXp Realty)
LEAD_EMAIL                     a real external inbox (e.g. <city>downsizing@gmail.com). Never invent one.
TEAM_LICENSED_IN_THIS_STATE    yes or no
DOMAIN STATUS                  bought and on Cloudflare yet?
COLORS                         optional (New York used city-flag blue and orange)
```

- If nobody on the team is licensed in the state: **stop**. That is a licensing problem.
- If LEAD_EMAIL is unknown, scaffold with `hello@<domain>` as a placeholder and put it on the
  owner checklist. The mail Worker's destination must be an external inbox the owner can
  verify; an address on the site's own domain cannot be an Email Routing destination.
- REGION_FOR_55PLUS is yours to research (step 3). It must stay inside the licensed state.

## 1. Template and working rules

- Template: the newest city repo. As of this writing `~/newyorkdownsizing` (it carries every
  fix below); `~/tampadownsizing` is the original. Read `playbook/README.md`, `content.md`,
  `places.md` and `photos.md` in the template first. They are binding; this skill adds what
  they do not say.
- Delegate research and writing to background agents on **Sonnet**, simple lookups to
  **Haiku**. Review everything on the main model before it ships. One writer per file.
- Never invent a fact. Unverifiable means cut, and tell the reader who to ask.
- Call `change_directory` to the new repo after scaffolding. Keep research in `notes/`
  (gitignored).

## 2. Pre-flight and scaffold

1. `whois <city>downsizing.com`, and a Haiku agent searches for any business trading under
   the exact brand name. Report and carry on unless an exact-name business exists (**ASK**).
2. From the template: `node scripts/new-city.mjs --city .. --state .. --abbr .. --county ..
   --region .. --brokerage .. --email ..`, then `node build.mjs` and
   `node tests/content.check.mjs`. The leftover-word failures are the to-do list.
3. Things the scaffold does not clean when the template is New York. Fix by hand:
   - `src/neighborhoods.json`, `boroughDirectory()` in `src/layout.js`, the borough logic in
     `src/pages/where-to-downsize.js` and `src/pages/index.js` are NYC-specific. Replace the
     data with this city's official neighborhood/district list if one exists (planning
     department open data), or remove the directory and list featured neighborhoods only.
   - `src/assets/calc.js`, `tests/calc.check.mjs`, `net-proceeds-calculator.js`: New York
     transfer taxes. Rebuild for this state's seller transfer taxes, or its portability rule.
   - Lead form placeholder ("e.g. Upper West Side") and `tests/lead.check.mjs` sample values.
   - `template-leftovers.json`: confirm it lists the template city's words. Remove a word
     later only if a real page needs it (New York dropped "Florida" for a moving guide).
   - Colors: tokens at the top of `src/assets/site.css`, plus `favicon.svg`, `layout.js`
     (logo, theme-color), `scripts/og-images.mjs`, `functions/api/lead.js`. Regenerate
     `logo.png` and `apple-touch-icon.png` from the SVG with `sips`. Check contrast (4.5:1).
   - Never call the site "independent" or the match "vetted" (grep for both).

## 3. Research first: fact sheets are the single source of truth

Run these Sonnet agents in parallel before any page is written. Each writes one file in
`notes/` with every fact, the year it applies to and the source URL actually read, and marks
anything unconfirmed UNVERIFIED.

- `notes/<st>-tax-facts.md`: seller transfer taxes (exact rates, thresholds, rounding, who
  pays: these feed the calculator), buyer-side taxes, senior and homestead property tax
  relief, income tax on a sale (IRC 121 plus the state), estate tax, nonresident seller
  rules, closing-cost customs, pending bills or ballot measures.
- `notes/<st>-law-facts.md`: seller disclosure law, agency disclosure forms, condo/co-op/HOA
  law, HOPA 55+ rule, insurer of last resort, flood and evacuation lookups (exact working
  URLs), historic storm context from official reports, attorney customs, aging services.
- `notes/<st>-resources.md`: move managers, estate sale firms, donation, disposal, aging,
  legal referral. Every entry confirmed on its own site.
- 55+ region: which in-state area has at least 10 verifiable age-restricted ownership
  communities. Pick the smallest region that does.
- Photos: see step 6. Can start as soon as slugs are known.

Then decide and record what the state's law changes: calculator, tax pages, housing law,
hazard guides, disclosure.

## 4. Site structure that worked

- **Neighborhoods hub** with area pages (boroughs in NYC; counties or districts elsewhere),
  each listing every official neighborhood, and **featured neighborhood pages** (New York:
  23) that get a full page and photo. `menu.group` is `'neighborhoods'` for area pages and
  `'featured'` for neighborhood pages, with `borough`, `nta` and a two-level `parent` trail.
- **55+ communities**: 6 to 8 real ones, confirmed 55+ on their own or a government page.
- **Guides**: the core 12 from the playbook, a local "getting around after 65" guide, then a
  round of 10 keyword-targeted guides (step 8).
- **Main-model pages**: home, both hubs, costs-and-money, resources, calculator page,
  step-by-step guide, guides hub.

Writer briefs that worked are bundled in `references/` next to this file: `brief.md` (core
rules and verified links), `brief-boroughs.md` (local voice, area and featured page formats),
`brief-blogs.md` (SEO rules for keyword guides). Copy them into the new repo's `notes/`,
rewrite the city-specific parts, and give every writer `playbook/content.md` plus the right
brief and fact sheets. About 3 guides, 4 to 5 neighborhoods or 4 communities per agent.

## 5. Review rules learned the hard way (apply to every agent's output)

- **No research narration on the page.** Grep for `could not|secondary source|unverif|we
  were unable|when we checked|search result|snippet`. Send the writer back to rewrite as
  "ask X".
- **No Wikipedia citations.** Re-source to an official page or cut.
- **Agents get blocked** by some official sites (403, CAPTCHA, JS shells). Verify their
  snippet-sourced claims yourself in the Browser pane: library addresses, park facts,
  hospital names, opening years. Never try to get past a CAPTCHA; cut the claim instead.
  In New York this caught a wrong library address, a wrong tower name and several
  unsupported superlatives and dates.
- Grep for superlatives (`largest|oldest|first|best|only`) and for "Most downsizers here"
  style generalizations. Keep only what a cited source says.
- Check every worked tax example against the calculator module with a one-line node script.
- Remove dated specifics that will rot (event dates, "as of this month the page says").
- Cut any link you cannot load yourself.
- Normalize guide `crumb` capitalization (Title Case).

## 6. Photos

- Agent stages candidates in `notes/photo-candidates/` with a `candidates.json`; nothing goes
  in `src/` until the main model has **looked at every one**. Ask for originals at least
  2400px wide, daylight, leafy or blue sky, not dominated by cars, signs, scaffolding or
  cranes, no close-up strangers, subject near the vertical middle.
- Gated 55+ communities will have none. That is expected.
- `scripts/prep-images.mjs` (New York version) writes banner, 16:10 card, uncropped "full"
  and portrait "tall" crops at high JPEG quality. Do not go back to quality 'low' or a
  single 1600px size: that is what made the photos look fuzzy.
- Set `photoSlug` on the home page and the step-by-step guide.

## 7. Layout and formatting checks (all were real bugs)

- Every long page needs the contents rail: `p.article || p.rail || p.menu` in `layout.js`,
  and `rail: true` on costs-and-money. Without it desktop shows a 760px column and ~400px of
  blank space.
- `.pcard__img` needs `height: auto`; `.rail li a::before` (not `.rail a::before`) or the
  rail button shows "00".
- Guides hub is a card grid, not one full-width band per category.
- Run the gap and structure lints from the New York session: no heading jumps (h1 to h3),
  no paragraphs over 130 words, tables wrapped in `.table-scroll`, no horizontal overflow at
  1280 and 375 (check in the Browser pane with an iframe loop over the sitemap).
- Headless Chrome full-page screenshots (`--headless=new --screenshot`) are the reliable way
  to see a whole page; it cannot go below ~500px wide, so use the Browser pane for mobile.

## 8. SEO pass and keyword guides

- The content check enforces titles (50 to 60), descriptions (110 to 158), uniqueness,
  canonicals, share cards and JSON-LD. Run `node scripts/og-images.mjs` after adding pages.
- Extra audit: every `<img>` has alt and dimensions, every indexable page is in the sitemap,
  no heading jumps, no thin pages besides legal and form pages.
- Keyword research without paid tools: Google autocomplete
  (`https://suggestqueries.google.com/complete/search?client=firefox&q=...`) over ~30 seed
  terms (selling, taxes, senior housing, co-op or condo terms, "moving from <city> to").
  Pick 10 topics the site does not cover, one primary keyword each, and brief writers per
  `references/brief-blogs.md`. If the Ahrefs connector is authorized, use it for volumes.

## 9. Checks, then deploy (pre-authorized by the owner's launch prompt)

```
node build.mjs && node tests/content.check.mjs && node tests/lead.check.mjs \
  && node tests/middleware.check.mjs && node tests/calc.check.mjs
```

1. Commit. `gh repo create <user>/<city>downsizing --private --source . --remote origin --push`.
2. `npx wrangler pages project create <city>downsizing --production-branch main`.
3. Confirm `.githooks/pre-push` is executable (`ls -l`; the scaffold now preserves it). The
   hook builds, tests and deploys on every push to main. "lead delivery failed" lines in its
   output are the lead test's deliberate failure cases.
4. `cd mailer && npx wrangler deploy`.
5. Confirm `https://<city>downsizing.pages.dev` returns 200 with `X-Robots-Tag: noindex`.

Phase 1 handoff: preview URL, what the state's law changed, claims cut, photos rejected,
lawyer items, and the owner checklist (buy the domain and add it to Cloudflare; add apex and
`www` as custom domains on the Pages project; confirm licensing; lead inbox if still unknown).

## 10. Phase 2: when the domain is attached

1. Verify: apex 200 with no `X-Robots-Tag`, `www` 301 to apex, canonical on apex, sitemap
   loads (`dig @1.1.1.1`, `curl -sI`).
2. `dig MX <domain> @1.1.1.1` must be empty. Then
   `npx wrangler email routing enable <domain>` and
   `npx wrangler email routing addresses create <lead inbox>`. Cloudflare emails the inbox a
   verification link: **ASK** the owner to click it.
3. Shared key: `openssl rand -hex 32`, then `wrangler secret put MAILER_KEY` in `mailer/`,
   and `wrangler pages secret put MAILER_KEY` and `MAILER_URL` on the Pages project.
   Redeploy.
4. Once `wrangler email routing addresses list` shows the address verified, POST one clearly
   labelled test lead to `https://<domain>/api/lead` and ask the owner to confirm it arrived.
5. `node scripts/indexnow.mjs`. Tell the owner to submit the sitemap in Search Console and
   request indexing on the home page and two strong guides (IndexNow does not reach Google).

## 11. Final report

One short message: live URL, what was built (counts), what was verified, every claim cut or
softened and why, photos missing, anything for a lawyer licensed in the state (consent
wording, brokerage advertising rules, terms page), and what only the owner can do.
