# Site map for the new trianglerowing.org

Work package: Write site map and old-URL redirect map (https://pace.demar.co/work_packages/2489).
Sources: `docs/research/trc-site-inventory.md`, `docs/research/peer-club-survey.md`, the live sitemap.xml and the live pages, all read on 2026-11-14.

Rules used: every page is a folder `content/pages/<path>/_index.md` served at `/<path>/`; navigation is at most two levels; registration, payments, rosters and member login stay on SportsEngine (`triangle-rowing-club.sportngin.com`) and pages link out to them rather than copy them.

## Navigation tree

```
Header: [Join] button, then:
Home                               /
Start here (new to rowing)         /new-to-rowing/
  Parent FAQ                       /new-to-rowing/parent-faq/
  Regatta guide                    /new-to-rowing/regatta-guide/
  How rowing works                 /new-to-rowing/how-rowing-works/
  Glossary                         /new-to-rowing/glossary/
  Gear and uniforms                /new-to-rowing/gear/
Programs and costs                 /programs/
  High school                      /programs/high-school/
  Middle school                    /programs/middle-school/
  Learn to row (summer)            /programs/learn-to-row/
  Sneak Peek Week                  /programs/sneak-peek-week/
  Off-season training              /programs/off-season-training/
  Financial aid                    /programs/financial-aid/
Families                           /families/
  Practice and schedule            /families/practice/
  Calendar                         /families/calendar/
  Regatta schedule                 /families/regatta-schedule/
  Volunteering                     /families/volunteering/
  Safety and SafeSport             /families/safety/
  Registration help                /families/registration-help/
About                              /about/
  Coaches                          /about/coaches/
  Facilities                       /about/facilities/
  Achievements                     /about/achievements/
  Contact                          /about/contact/
  Privacy policy                   /about/privacy/
Support us                         /support/
  Donate                           /support/donate/
  Monthly giving                   /support/monthly-giving/
  Erg-A-Thon                       /support/erg-a-thon/
  Sponsors and corporate matching  /support/sponsors/
News                               /news/
Merch store                        external link (Squadlocker), not a page
Join                               /join/   (header button, also listed under Programs)
```

Top-level items: 7 pages plus the Join button and one external link. The Join page is reached from the header button and from every program page.

## Page list

Status values: new, migrated (source URL given), dropped (reason given; dropped pages are redirected, see below). Audience: parents of prospective or new rowers, current families, athletes, donors and sponsors, or all visitors.

| Path | Audience | Purpose | Status | Source or reason |
|---|---|---|---|---|
| `/` | all visitors | Say what TRC is, show the next step (join or interest form) and the season banner. | migrated | `/home` (Who We Are) |
| `/new-to-rowing/` | parents of new rowers | One start page: what rowing is, what a child does each week, a first-season timeline (fall, winter, spring, summer) and who to ask. | new | Builds on `/new` and `/rowing-101` |
| `/new-to-rowing/parent-faq/` | parents of new rowers | Answer the common worries in plain language: no experience, body size, cost, absences, trial period. | migrated | `/registration-faq`, `/practice-faq` (regatta and volunteer questions move to their own pages) |
| `/new-to-rowing/regatta-guide/` | parents | Explain what a regatta is, how a race day runs, what to pack and where to be. | migrated | `/regatta-faq`, with new explanatory content |
| `/new-to-rowing/how-rowing-works/` | parents | Show the boats and how racing works in one short page. | migrated | `/rowing-101`, `/boats`, `/racing` |
| `/new-to-rowing/glossary/` | parents | Define rowing words (sweep, sculling, cox, erg, head race). | migrated | `/rowing-terms`; data in `data/glossary.yaml` |
| `/new-to-rowing/gear/` | parents and athletes | List required clothing, uniforms and spirit wear, with links to the stores. | migrated | `/uniforms-and-spiritwear` |
| `/programs/` | parents | Compare all programs by grade, days, season dates and price on one page, with what dues cover and what costs extra. | migrated | `/programs` |
| `/programs/high-school/` | parents, athletes (grades 9 to 12) | Schedule, season dates, price and registration link for high school rowing. | migrated | `/high-school` |
| `/programs/middle-school/` | parents, athletes (grades 6 to 8) | Schedule, season dates, price and registration link for middle school rowing. | migrated | `/middle-school` |
| `/programs/learn-to-row/` | parents of beginners | Summer camp sessions, price, swim requirement and registration link. | migrated | `/learn-to-row` |
| `/programs/sneak-peek-week/` | parents of beginners | Fall trial week: dates, fee, what to bring, registration link. | migrated | `/sneak-peek-week` |
| `/programs/off-season-training/` | current athletes | Summer and winter training options and prices. | migrated | `/off-season-training` |
| `/programs/financial-aid/` | parents | Show how tuition reduction works, who can apply, deadlines and the true cost of a season. | migrated | `/tuition-reduction-program` |
| `/join/` | parents | The three steps to join: interest form, learn to row or trial, register (links out to SportsEngine). | migrated | `/join` |
| `/families/` | current families | Hub for everything a member family needs during the season. | migrated | `/faq` (For Members; the old page was an empty hub) |
| `/families/practice/` | current families | Practice times by squad and season, pickup, attendance, weather and illness rules. | migrated | `/practices`, `/training-schedule` |
| `/families/calendar/` | current families | Season calendar with feeds for each squad (embedded from the SportsEngine feeds, no new calendar system). | migrated | `/page/show/7282304-calendar` |
| `/families/regatta-schedule/` | current families | List this season's regattas with dates, places and entry links. | migrated | `/regattas` |
| `/families/volunteering/` | current families | Explain the volunteer token system, jobs and sign-up links. | migrated | `/volunteering`, `/volunteer-faq` |
| `/families/safety/` | parents | Safety, first aid, SafeSport training steps and background checks. | migrated | `/safety` |
| `/families/registration-help/` | current families | Say what to have ready to register and link to SportsEngine sign-in and its help for profiles, guardians and documents. | migrated | `/trc-registrations` |
| `/about/` | all visitors | Mission, history, size and a pointer to the other About pages. | new | Mission text taken from `/home` |
| `/about/coaches/` | parents | Introduce head and assistant coaches, with credentials and contact emails. | migrated | `/coaches` |
| `/about/facilities/` | current families | Boathouse and lake location, parking and pickup rules, indoor winter site. | migrated | `/facilities` |
| `/about/achievements/` | all visitors | Results, nationals boats and college placements. | migrated | `/achievements` |
| `/about/contact/` | all visitors | Email addresses by topic, mailing address and a contact form. | new | Replaces the SportsEngine compose-email element `/page_element/compose_email/2760521` |
| `/about/privacy/` | all visitors | State how the club handles personal data. | migrated | `/privacy_policy.pdf` |
| `/support/` | donors and sponsors | Hub for ways to give, with what a gift buys. | migrated | `/support-us` |
| `/support/donate/` | donors | One-time gift (links to Givebutter). | migrated | `/donations` |
| `/support/monthly-giving/` | donors | Monthly giving and its questions in one page. | migrated | `/sustainer`, `/sustainer-faq` |
| `/support/erg-a-thon/` | donors, families | Annual fundraiser: goal, date, link to the campaign. | migrated | `/erg-a-thon` |
| `/support/sponsors/` | businesses | Sponsor tiers as readable text, current sponsors and employer matching. | migrated | `/corporate-matching`, sponsor lists on `/support-us` |
| `/news/` | all visitors | Dated club news and results; the old site had none. | new | No source; section already exists in `content/news/` |

Dropped pages (all redirected to the closest page above):

| Old page | Reason | Redirected to |
|---|---|---|
| `/join-our-team` (page/show/8883554) | Duplicate of `/join`. | `/join/` |
| `/our-training-schedule` (page/show/9075305) | Duplicate of `/training-schedule`. | `/families/practice/` |
| `/se-login-and-profile-access`, `/registration-editing`, `/details`, `/edit-profile-information`, `/add-guardian`, `/se-communications` | Screenshot guides to the SportsEngine screens. They go stale when SportsEngine changes and the login link on one points at a staging host. Replaced by links to SportsEngine's own help on the registration help page. | `/families/registration-help/` |
| `/faq` hub body | Empty page; its job is done by `/families/`. | `/families/` |

Not planned, by design: registration forms, payment, rosters, member login, profile editing and email preferences stay on SportsEngine. The site links to the registration forms and shows no price-paying flow.

## Old URL coverage

`data/redirects.yaml` maps every URL below to a page above. It holds, for each of the 42 pages in the live sitemap.xml: the `/page/show/<id>-<slug>` path from the sitemap; the short path used by the live navigation; and the short slug form of the sitemap name where it differs. The short slug forms (for example `/our-coaches`) were not each confirmed live; they are included so any old bookmark resolves. Also mapped: `/home`, `/privacy_policy.pdf` and the compose-email element path. Home page links to external services (Givebutter, Google Docs, SportsEngine registration forms, stores) are not site paths and are not redirected.
