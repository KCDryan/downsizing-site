# Brief addendum: boroughs and more neighborhoods

Read after playbook/content.md, playbook/places.md and notes/brief.md. Everything there still
applies: verified facts only, no prices, no drive times, no zones stated for an area, Fair
Housing language, no research-process narration on the page ("we could not confirm..."):
if something cannot be verified, simply do not say it and tell the reader who to ask.

The audience is people who live in New York City now. Write like someone who knows the city:
use the names locals use ("the Bronx", "the 7 train", "the Q", "Metro-North", "the ferry",
"co-op board", "maintenance", "super", "walk-up", "pre-war", "the BQE", "the LIE"), be exact
about streets and subway lines (only as mta.info shows them), and never explain the city as if
to a tourist. Specific beats general: name the actual parks, library branches, hospitals,
older adult centers and shopping streets, each verified on its own official page.

## Site structure (new)
- Neighborhoods hub: /where-to-downsize/
- Borough pages: /where-to-downsize/manhattan/, /brooklyn/, /queens/, /bronx/, /staten-island/
  (labels: Manhattan, Brooklyn, Queens, The Bronx, Staten Island). menu.group 'neighborhoods',
  orders 1 to 5 in that order.
- Featured neighborhood pages (full pages with photos): /where-to-downsize/SLUG/, with
  `menu: { group: 'featured', borough: 'Manhattan', nta: ['MN0401'], order: N, label, blurb }`
  and `parent: [['/where-to-downsize/', 'Neighborhoods'], ['/where-to-downsize/manhattan/', 'Manhattan']]`.
  `borough` is exactly one of: Manhattan, Brooklyn, Queens, Bronx, Staten Island (data value;
  display "The Bronx" in copy and labels). `nta` codes come from src/neighborhoods.json (NYC
  Planning 2020 Neighborhood Tabulation Areas).

Existing featured pages (link to them where natural): upper-west-side, upper-east-side,
battery-park-city, murray-hill-kips-bay (Manhattan); brooklyn-heights, bay-ridge (Brooklyn);
forest-hills, bayside, jackson-heights (Queens); riverdale (Bronx).
New featured pages being written now: chelsea, greenwich-village, harlem, east-midtown-turtle-bay
(Manhattan); park-slope, sheepshead-bay, carroll-gardens-cobble-hill (Brooklyn); astoria,
long-island-city, flushing (Queens); parkchester (Bronx); st-george, great-kills (Staten Island).
New guide: /guides/getting-around-new-york-city-after-65/.

## Borough page format (1,400 to 2,000 words of prose plus the directory)

```js
import { boroughDirectory } from '../../layout.js';

export default (c, all) => ({
  path: '/where-to-downsize/manhattan/',
  crumb: 'Manhattan',
  h1: 'Downsizing in Manhattan',
  parent: ['/where-to-downsize/', 'Neighborhoods'],
  menu: { group: 'neighborhoods', order: 1, label: 'Manhattan', blurb: 'Under 90 characters.' },
  title: '50 to 60 characters',
  description: '140 to 158 characters',
  faq: [['Question?', `<p>Answer.</p>`]], // 4 to 5, borough-specific
  body: `
<section class="page-hero">
  <div class="wrap">
    <h1>Downsizing in Manhattan</h1>
    <p class="lede">Two or three sentences.</p>
    <dl class="glance">
      <div><dt>County</dt><dd>New York County</dd></div>
      <div><dt>Community districts</dt><dd>12</dd></div>
      <div><dt>Common smaller homes</dt><dd>Co-ops, condos</dd></div>
      <div><dt>Evacuation zone</dt><dd><a href="https://finder.nyc.gov/hurricane" rel="noopener">Check by address</a></dd></div>
    </dl>
  </div>
</section>
<section class="section" style="padding-top:0">
  <div class="wrap prose">
    <h2 id="overview">...</h2>
    ...
    <h2 id="all-neighborhoods">Every Manhattan neighborhood, by community district</h2>
    <p>One or two sentences: the list follows NYC Planning's neighborhood boundaries; neighborhoods with a full guide are linked.</p>
    ${boroughDirectory('Manhattan', all)}
    ...
  </div>
</section>`,
});
```

Borough sections (reword H2s naturally with the borough name):
1. Overview: county name, where it sits, how many community districts (count from
   src/neighborhoods.json), one or two sentences of history from an official source.
2. Housing for downsizers here: the mix of co-ops, condos, row houses, detached houses,
   garden apartments, walk-ups vs elevator buildings, as described by official or reputable
   sources (NYC Planning community profiles, LPC, the borough president). No prices.
3. Where to start: the featured neighborhoods in this borough, one line each, linked.
4. Getting around: subway lines, buses, ferries (NYC Ferry routes / Staten Island Ferry), LIRR
   or Metro-North stations, Staten Island Railway, as the MTA/NYC DOT/NYC Ferry sites show.
   Mention the MTA reduced fare for riders 65 and older only if you read it on mta.info, and
   link /guides/getting-around-new-york-city-after-65/.
5. Hospitals and health care: major hospitals in the borough, each verified on its own site.
6. Older adult services: NYC Aging older adult centers (link the NYC Aging finder or site),
   the borough president's office if it runs relevant programs (verify), libraries (NYPL for
   Manhattan, the Bronx and Staten Island; Brooklyn Public Library; Queens Public Library).
7. Flooding and storms: coastal areas of the borough in general terms only if an official
   source says so (NYC EM, NYC Planning, FloodHelpNY eligible areas from notes/ny-law-facts.md);
   link finder.nyc.gov/hurricane and FEMA MSC; never assign a zone.
8. Taxes: same NYC programs everywhere (SCHE, STAR, co-op/condo abatement, NYC transfer tax),
   from notes/ny-tax-facts.md, linking /costs-and-money/.
9. The full directory (the ${boroughDirectory(...)} block above).
10. One soft line to /get-matched/ near the end.

## Featured neighborhood pages
Exactly the neighborhood format in playbook/places.md (900 to 1,400 words), with the new
menu/parent fields above. Name buildings only when a reliable source confirms both existence
and ownership type. Use the NTA code(s) given in your task.

## Checks before you finish
`node --check` each file, `node build.mjs`, `node tests/content.check.mjs`; fix problems in
YOUR files only (missing og share cards and photos are expected and not yours). Report
files, word counts, anything cut, main sources, in under 200 words.
