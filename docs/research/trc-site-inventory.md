# Triangle Rowing Club (TRC) public site inventory

Crawled 2026-11-14 via WebFetch plus curl of public HTML/CSS/nav JSON. Read-only; no logins, no form submissions.

- Public URL: https://www.trianglerowing.org (SportsEngine "Sitebuilder", site id 61928; platform host alias https://triangle-rowing-club.sportngin.com)
- Meta description (every page): "A competitive rowing team for middle and high school students in Wake County, North Carolina."
- Organization: 501(c)(3), founded 2008, 120+ athletes, 30+ schools. Mailing address PO Box 5102, Cary, NC 27512-5102.
- Boathouse/practice: Lake Wheeler Park, 6404 Lake Wheeler Road, Raleigh, NC 27603 (verified on multiple pages). Indoor winter facility: Carolina Pines Park, 2305 Lake Wheeler Rd, Raleigh, NC 27603. Long-distance regatta departure: Bass Pro Shops lot, 801 Bass Pro Ln, Cary, NC 27513.

## 1. Navigation (from embedded nav JSON; live menu is JS-rendered)

Top level: Who We Are (/home) | Join | For Members | Support Us | Merch Store (external link)

```
Who We Are (/home)
  Programs (/programs)
    High School (/high-school)
    Middle School (/middle-school)
    Sneak Peek Week (/sneak-peek-week)
    Off-Season Training (/off-season-training)
    Learn To Row (/learn-to-row)
  Coaches (/coaches)
  Facilities (/facilities)
  Achievements (/achievements)
  Training Schedule (/training-schedule)
Join (/join)
For Members (/faq)
  Registration (/trc-registrations)  [2 children]
  Practice (/practices)  [1 child]
  Regattas (/regattas)  [1 child]
  Volunteering (/volunteering)  [1 child]
  Tuition Reduction (/tuition-reduction-program)
  Uniforms/Spirit Wear (/uniforms-and-spiritwear)
  New? (/new)
  Rowing 101 (/rowing-101)  [3 children: Boats, Racing, Rowing Terms]
  Safety (/safety)
  Calendar (/page/show/7282304-calendar)  [SportsEngine calendar node]
Support Us (/support-us)
  Erg-A-Thon (/erg-a-thon)
  Donations (/donations)
  Become a Sustainer (/sustainer)  [1 child: Sustainer FAQ]
  Corporate Matching (/corporate-matching)
Merch Store -> http://teamlocker.squadlocker.com/#/lockers/triangle-rowing-club-1913870 (new tab; http, not https)
```
Footer/quick links on home: Programs, Join, Uniforms and Spiritwear, Athlete and Family Manual (Google Doc), For Members, Support Us; Contact Us (SportsEngine compose-email element /page_element/compose_email/2760521); Privacy Policy (/privacy_policy.pdf); "Powered by SportsEngine" links.

No news/blog section exists (/news returns 404; home has no post feed). No site search beyond SportsEngine "Page Search".

## 2. Page count

Sitemap.xml lists 42 pages (all under /page/show/<id>-<slug>). Plus 1 external-link nav node (Merch Store). Of the 42, I fetched about 27 directly; the rest were confirmed to exist (HTTP 200) but not read in detail (marked "not read").

Sitemap list: home, facilities, calendar, programs, high-school, learn-to-row, sneak-peek-week, coaches, support-us, sustainer, corporate-matching, donations, sustainer-faq, achievements, middle-school, off-season-training, volunteering, new-to-trc, rowing-101, boats, racing, rowing-terms, for-members (faq), practice, regattas, registration, practice-faq, regatta-faq, volunteer-faq, registration-faq, uniforms-spirit-wear, safety-and-safesport, se-login-and-profile-access, registration-editing, details, edit-profile-information, se-communications, add-guardian, erg-a-thon, tuition-reduction-program, join-our-team, our-training-schedule.

Note: sitemap slugs differ from live nav URLs (e.g. /coaches vs our-coaches, /sustainer vs become-a-sustainer, /new vs new-to-trc). Redirect map needed. /edit-profile-information returns 404 at the short slug; sitemap form untested.

## 3. Page inventory

| # | URL | Title | Purpose | Summary | Type |
|---|-----|-------|---------|---------|------|
| 1 | / (/home) | Who We Are | Landing | Mission, Winter Training register CTA, interest form CTA, YouTube video (embed id RNblDvboIq0), team photo (High Point 2026), quick links, tiered sponsor logos, contact, community partners (City of Raleigh Parks, Lake Wheeler Park), supported programs (Raleigh Rowing Center, NC State rowing club), social icons | static text, embedded video, sponsor list |
| 2 | /programs | Programs | Overview | Year-round co-ed squads (MS, Novice, Varsity; "six squads"), no adult program (refers adults to Raleigh Rowing Center), links to HS/MS/SPW/Learn-to-Row. Says "Winter Open House has concluded" | static text |
| 3 | /high-school | High School | Program detail | Grades 9-12; practices Mon-Sat; fall mid-Aug to early Nov, spring mid-Feb to mid-May; dues $1,695 "most recent season"; off-season $165-$275; regattas incl. Head of the Charles/Hooch; physical required; PDFs linked | static text, document links |
| 4 | /middle-school | Middle School | Program detail | Grades 6-8; girls Tue/Thu/Sat, boys Wed/Fri/Sat; dues $525; off-season $180-$250; two NC regattas | static text, document links |
| 5 | /sneak-peek-week | Sneak Peek Week | Trial week | $10 fee; fall dates Aug 25-29 (HS with experience/LTR) and Sep 1-5 (others); schedule, what to bring; registration on SportsEngine | static text, form link |
| 6 | /learn-to-row | Learn To Row (Summer 2026) | Summer camp | Sessions 0-3 (Jun 22 - Aug 7, 2026), Mon-Fri 9:30-12:30, $285/week, swim requirements, refund policy, daily structure; registration closed; Google map link | static text, form link |
| 7 | /off-season-training | Off-Season Training | Summer/winter training | Summer $175 MS / $230 HS per session; winter M/W/F and T/Th options; fees for winter missing; "to be provided" placeholders | static text |
| 8 | /coaches | Our Coaches | Staff bios | 3 head coaches (Will White, Kees Koopman, Josiah Geist), 6 assistants; no contact emails | static text, photos |
| 9 | /facilities | Our Facilities | Venue rules | Lake Wheeler Park, 15 mph limit, parking/pickup rules, parking map image (2026), weather link | static text, image |
| 10 | /achievements | Our Achievements | Results | Totals (46 nationals boats, 4 US Junior team, ~60 colleges), news-style dated entries Jun 2022 - Oct 2025, ~10 photos | static text, photos (news-like) |
| 11 | /training-schedule | Our Training Schedule | Weekly schedule | Spring/fall, winter indoor, summer; Lake Wheeler and Carolina Pines locations, Google Maps links. No calendar widget | static text |
| 12 | /join | Join Our Team | Funnel | 3 steps: interest form, learn to row, register; eligibility; coach@ email | static text, form link |
| 13 | /faq | For Members | Hub | "FAQ Central" intro only; no Q&A body on this page | static text (hub) |
| 14 | /trc-registrations | Registration | How to register | Checklist of info needed, PDFs (medical clearance, Return to Play dated 10_2020), links to registration FAQ/edit | static text, PDFs |
| 15 | /practices | Practice | Weekly schedule + policies | Pickup 30 min before sunset, attendance, weather, illness | static text |
| 16 | /regattas | Regattas | Race schedule | Fall 2026 (Sep 26 - Nov 14) and Spring '27 lists with RegattaCentral links; USRowing membership, excused absence, Bass Pro departure lot | static table |
| 17 | /volunteering | Volunteering | Volunteer policy | 40 tokens per HS rower (2026 spring), opt-out fee $800, enforcement; Google Docs and SignUpGenius | static text, external docs |
| 18 | /tuition-reduction-program | Tuition Reduction | Financial aid | 10-75% awards, deadlines Aug 17 / Sep 6 (no year), Google Form application | static text, form |
| 19 | /uniforms-and-spiritwear | Uniforms/Spirit Wear | Gear | HS and MS uniform lists, jackets (fall order, min 6), Square store and Squadlocker | static text, store links |
| 20 | /new | New? | New-parent guide | Checklist, what to bring, fueling, safety, waiver PDF | static text, PDF (not read directly beyond summary) |
| 21 | /rowing-101 | Rowing 101 | Explainer hub | Links to Boats, Racing, Rowing Terms | static text |
| 22-24 | /boats, /racing, /rowing-terms | Boats / Racing / Rowing Terms | Explainers | HTTP 200, NOT READ | static text |
| 25 | /safety | Safety | Safety/SafeSport | AED/first aid, SafeSport, background checks via NCSI, registration form link | static text |
| 26 | /support-us | Support Us | Fundraising hub | Links to Erg-A-Thon, Donations, Sustainer, Corporate Matching; sponsor tiers | static text, sponsor list |
| 27 | /erg-a-thon | Erg-A-Thon | Fundraiser | 2026 goal $50,000 for a Vespoli 8+; Givebutter campaign link | static text, donation link |
| 28 | /donations | Donations | Give | Givebutter link; card/Google Pay/Apple Pay/PayPal/Venmo | static text, donation link |
| 29 | /sustainer | Become a Sustainer | Monthly giving | Recurring giving via Givebutter, fund choice | static text, donation link |
| 30 | /sustainer-faq | Sustainer FAQ | FAQ | $25/rower/month, $30,000 goal, equipment costs | static text |
| 31 | /corporate-matching | Corporate Matching | Employer match | Names Cisco, Red Hat, Oracle, Progress Energy, SAS | static text |
| 32 | /page/show/7282304-calendar | Calendar | Schedule | SportsEngine calendar (month/list/day views, RSS, iCal, Google/Apple for 4 calendars: General, High School, MS Boys, MS Girls). Grid showed no events | calendar (SportsEngine) |
| 33-36 | /registration-faq, /practice-faq, /regatta-faq, /volunteer-faq | FAQs | Topic FAQs | HTTP 200, NOT READ | static text |
| 37 | /registration-editing | Registration Edit Details | How to edit/upload docs | HTTP 200, NOT READ (instructions for SportsEngine account) | static text, screenshots |
| 38 | /details, /add-guardian | SE help pages | HTTP 200, NOT READ | static text, screenshots |
| 39 | /se-login | SE Login and Profile Access | Instructions | 4-step screenshot guide to sign in to SportsEngine / My SportsEngine | static text, screenshots |
| 40 | /se-communications | Communications | Instructions | How to set communication preferences in SportsEngine | static text, screenshots |
| 41 | /page/show/8883554-join-our-team, /page/show/9075305-our-training-schedule | duplicates of Join / Training Schedule in sitemap | - | same pages |
| 42 | /privacy_policy.pdf | Privacy policy | PDF | not read | document |

Pages 38-41: sitemap shows edit-profile-information as a separate page (404 at short slug).

## 4. SportsEngine-dependent features (likely stay on SportsEngine; link from new site)

Registration forms (all on https://triangle-rowing-club.sportngin.com/register/form/<id>):
1. Winter Training registration: /register/form/770415448 (home page CTA)
2. Interest form: /register/form/827812930 (home and Join)
3. Sneak Peek Week registration: /register/form/965436227
4. Learn-to-Row camp registration: /register/form/148012664
5. Volunteer / background check registration form on Safety page: /register/form/270278506
(Main season team registration link not directly captured; /trc-registrations and /join point to registration; confirm the current season form ID with the club.)

Other SportsEngine features:
6. Member login / profile: SE sign-in (https://triangle-rowing-club.sportsengine-prelive.com/se-login is the link used on the Communications page; a "prelive" staging host, likely a bug). Members edit registration, upload documents (physicals, waivers), manage guardians, set communication preferences.
7. Payments: season dues, camp fees, Sneak Peek fee paid via SportsEngine registration (credit card); discount codes for scholarship recipients issued by the club, entered at registration.
8. Calendar: SportsEngine calendar page with RSS and iCal/Google/Apple feeds for 4 calendars (General, High School, MS Boys, MS Girls). Feed URLs not captured; need export from the calendar page.
9. Email/communications: "Contact Us" compose-email element (/page_element/compose_email/2760521); team email/newsletter via SE (TRC Newsletter referenced) and communication preferences.
10. Rosters: none public. No public roster, scores, or team pages found.
11. Analytics: Google Tag Manager (GTM-KGG8ZWR, GTM-TMK6MGB) and GA4 (G-Z7T9M0T3YT) in page source.

Not on SportsEngine (external services to keep linking):
- Donations: Givebutter, https://givebutter.com/triangle-rowing-club (general/sustainer), https://givebutter.com/c/erg-a-thon2026 (Erg-A-Thon). A Zeffy page also exists for TRC per web search (https://www.zeffy.com/organization/triangle-rowing-club) but is not linked from the site; also search shows https://givebutter.com/TR2 (tuition reduction).
- Tuition Reduction application: Google Form https://docs.google.com/forms/d/e/1FAIpQLScDuYG1ujOkeKAMotelMWkY8t8br00qPWqc4Tp9b3xL4Y5sOg/viewform?usp=dialog
- Athlete and Family Manual: Google Doc https://docs.google.com/document/d/1l1XDuctHbmLf5_-8-PdGtmUhkeuOsoHXfHpPxNb3kd8/edit
- SafeSport instructions Google Doc: https://docs.google.com/document/d/1Zk7hgysRBNTvUa7ZTcHaaLGtoUwBfoRqLceQsn5sfVU/edit?usp=sharing
- Volunteer job descriptions and sign-up (Google Docs), SignUpGenius per regatta
- Uniform store: https://trianglerowing.square.site/ ; Spirit wear: https://teamlocker.squadlocker.com/#/lockers/triangle-rowing-club-1913870
- Regatta entries: RegattaCentral and elizabethcityrowing.club (see /regattas)
- Weather: https://forecast7.com/en/35d66n78d68/27603/?unit=us
- Maps: Google Maps (Learn-to-Row map, boat storage https://maps.app.goo.gl/k4qfkEE1hy1d5rVp6, indoor https://maps.app.goo.gl/ovUAvQ5KnBFAEhGY9)
- PDFs hosted on SportsEngine CDN: Medical_Practitioner_Clearance_Form.pdf (https://cdn3.sportngin.com/attachments/document/09be-2752102/Medical_Practitioner_Clearance_Form.pdf), NCHSAA Return to Play form (10_2020), registration waivers PDF, privacy_policy.pdf. These must be re-hosted or they break if the SE account is closed.
- Images: all site images live on the sportngin CDN; must be downloaded and re-hosted.

## 5. Branding

- Logo: TRC shield, https://cdn3.sportngin.com/attachments/logo_graphic/8648-177275976/TRC_shield_medium.png (favicons/touch icons same path with _favicon_size_16/32/96 and _touch_icon_size_120..192). Site header image: https://app-assets2.sportngin.com/site_files/61928/siteHeader.jpg
- Colors (from theme/default CSS, by frequency): orange #E87722 (primary accent, 53 uses; also middle-school T-shirt color), navy #1B365D / #1A365D (primary dark), gold/yellow #DDA301 and #FCCD22 (accent), green #489456 / #2F6B3A, slate #42687C, neutrals #FFF #000 #333 #666 #CCC #DDD. Navy and orange are the club's visible identity; gold appears to be SportsEngine default. Verify against logo file.
- Fonts: "Titillium Web" (headings/primary), "Lato", "Open Sans", "LeagueGothicRegular" (fallback Arial Narrow), FontAwesome icons.
- Photos: FAD_xxxx.jpg series (club photographer), High Point 2026 team photo, 2024 Fall South trophy image.
- Sponsor logos on sportngin CDN (listed on home page).

## 6. Programs, contacts, social

Programs:
- Middle school (grades 6-8), co-ed; fall/spring competitive; dues $525
- High school (grades 9-12), Novice and Varsity men/women; dues $1,695
- Learn-to-Row summer camps (rising 6th-12th), $285/week, Lake Wheeler
- Sneak Peek Week (fall trial), $10
- Off-season: summer ($175 MS, $230 HS/session) and winter indoor ($165-$275 HS, $180-$250 MS per High School/Middle School pages)
- No masters/adult program (adults referred to Raleigh Rowing Center, https://raleighrowing.org/). Rowing Club at NC State https://rowingclubncsu.com/ also listed.
- Competitions: NC regattas (High Point, Elizabeth City), Head of the Charles/Hooch/South, Dogwood, SE Regionals, Youth Nationals

Contacts (all mailto): info@trianglerowing.org (general), coach@trianglerowing.org (coaching/prior experience), kkoopman@trianglerowing.org (Coach Kees, learn-to-row), fundraiser@trianglerowing.org, uniforms@trianglerowing.org, secretary@trianglerowing.org (background checks), safety@trianglerowing.org (SafeSport). Mailing address PO Box 5102, Cary, NC 27512-5102. No phone number found.

Social: Facebook https://www.facebook.com/Triangle.Rowing.Club/ ; Instagram https://www.instagram.com/trianglerowing/ ; X/Twitter https://twitter.com/TriangleRowing ; plus a placeholder link with href "http://#" on the home page (broken). YouTube video embedded on home (not a channel link).

Sponsors: Silver Oar (Crawford Hospitality, Hillsborough CDJR), Bronze Oar (Fox Rothschild), Erg-a-thon Platinum (Fathom, Sage Ecological Services, EzedMed), Gold (Triangle Lawns, Triangle Pest). Sponsor links all external.

## 7. Problems found

1. Stale/dated: Learn-to-Row page is "Summer 2026" and closed, still live in Nov 2026. Sneak Peek Week page shows Aug/Sep 2026 dates (past). Tuition Reduction deadlines (Aug 17 / Sep 6) have no year; says "returning applications now closed." Erg-A-Thon page references 2025/2026 goal. Home page promotes Winter Training with undated CTA. Programs page says "Winter Open House has concluded."
2. Outdated documents: Middle School page links NCHSAA 2023-2024 physical form (HS page links 2025-2026); Return to Play form dated 10/2020; Off-Season page email subject references 2023.
3. Inconsistent info: Volunteering page says 40 tokens in one place and 20 in another; fee amounts called "most recent season" (no current year); off-season dues ranges differ between Off-Season page and HS/MS pages; Join says "next opportunity is fall Sneak Peek Week" (now past); Learn-to-Row says "registrations closed" but Session 3 "spots available".
4. Broken/odd links: home placeholder link `http://#`; Communications page login link points to a `sportsengine-prelive.com` staging host; Merch Store and Raleigh parks links use http and old raleighnc.gov paths (likely dead); several internal links use http://trianglerowing.org without www; sitemap slugs do not match live nav URLs; /edit-profile-information 404; /news 404. Medical form URL has long tracking query string (_gl).
5. "For Members" (/faq) page is an empty hub; FAQ answers live on 4 sub-pages. Registration page lists no fees; Join page lists no costs ("season dues" only); fees scattered across 5 pages. No single clear pricing summary for parents.
6. Parent-facing gaps: no phone number; mailing address is a Cary PO box while the site says Raleigh; no board/officer list; no direct season dates/calendar events (calendar grid showed none); coach emails missing on Coaches page; no mention of what "tokens" are until Volunteering page; SafeSport/safety is buried under For Members.
7. Navigation: a 10-item "For Members" menu with nested children; Calendar is the last item. Mobile nav depends on SportsEngine JS.
8. Accessibility/quality: images with missing alt text (Corporate Matching photo), headings skip levels (H3/H4 then H1 for sponsors and "Page Search"), H1 used for search box; uppercase/lowercase inconsistent sponsor headings.
9. Platform lock-in: all images, PDFs, forms, login help pages (screenshots of the SE UI) are on the sportngin CDN or describe SE UI; a SE redesign breaks the help pages.
10. Third-party data: GTM and GA4 trackers in page source (Data Sovereignty note: new site should decide on analytics explicitly).
11. Content not fetched: Boats, Racing, Rowing Terms, 4 topic FAQs, registration-editing, details, add-guardian, trc-registrations children. Page source of the home page was captured in scratchpad (home.html, default.css, theme.css).
