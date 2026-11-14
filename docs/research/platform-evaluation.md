# Triangle Rowing Club website: platform evaluation

Prepared 2026-11-14. Scope: the public site only. Registration, payments and rosters stay on SportsEngine and are linked out. The calendar is embedded or linked from an iCal or Google Calendar feed.

## What decides this

The club has three hard criteria. Volunteer editors who change every year or two must be able to edit in a browser. The site must keep running after Nick leaves. Costs must stay near zero. Sovereignty here means the content is portable and the platform is open source, so the club can move hosts without a rewrite.

Two facts shape the ranking:

1. **Anything with a server is a recurring chore.** A PHP or Node app needs language-version upgrades, plugin updates, backups and security patching every month, forever. A volunteer site loses this fight once its technical volunteer leaves. A static site has no server to patch.
2. **Editor login is where static setups fail.** Git-based CMSes (Sveltia, Decap) make each editor sign in with an account on the Git host that has write access. Onboarding a new board member means "create a GitLab account, then an owner adds you." That is manageable, but it needs a written runbook and at least two club owners.

## Comparison table

Legend: low / medium / high. "Maint." means ongoing maintenance and security burden.

| Platform | Editor experience (non-technical) | Maint. burden | Hosting cost and options | Backup and portability | Performance and accessibility | Theming effort | Project health (Nov 2026) | Handoff risk |
|---|---|---|---|---|---|---|---|---|
| **Hugo + Sveltia CMS** | Good. Form-based editor at `/admin`, rich-text Markdown, media library. Publishing takes 1–2 min (CI build). Needs a Git-host account per editor. | **Low.** No server. Hugo is one binary pinned in CI. The CMS is one JS file. | **$0.** GitLab Pages, Codeberg Pages, Cloudflare static, GitHub Pages. | **Best.** Markdown and images in Git, and every clone is a full backup. Moves hosts in an afternoon. | Excellent. Static HTML. Accessibility depends on the theme. | Medium. Pick a theme, then customize templates (Go templates). One-time. | Hugo: steady releases (around v0.16x, 2026). Sveltia: very active (v0.265, Nov 2026, daily releases), 3.1k stars, still 0.x, essentially one lead developer. | Low for editing. Medium for layout changes, which need someone with Git basics. |
| **Hugo + Decap CMS** | Same model as Sveltia with an older, clunkier UI. Self-hosted GitLab works with the `pkce` login. | Low | $0, same hosts | Best (same files) | Excellent | Medium | Active: 3.17.x (Oct 2026), multi-person maintainers led by agency PM d.o.o. Editor login without a Git account only via Decap Turbo (SaaS). | Low/medium. Drop-in alternative to Sveltia (same `config.yml`). |
| **Astro + Sveltia/Decap** | Same as Hugo variant | Medium. npm dependency tree ages and breaks builds after a year or two idle. | $0 | Best | Excellent | Medium/high (JS components) | Very active. Acquired by Cloudflare Jan 2026, promised to stay MIT. Astro 6. | Medium. Rebuilding a stale Node project is the classic volunteer trap. |
| **Hugo + Pages CMS** | **Best of the Git-based options.** Editors are invited by email and need no Git account. | Low | $0 | Best | Excellent | Medium | Active (2.1.x, mid-2026), MIT. **GitHub only.** Hosted app is a free service; self-host needs Postgres. | Low/medium. Adds a dependency on GitHub and on the Pages CMS app. |
| **WordPress (self-hosted)** | Very good and **universally known**. Block editor, any future volunteer has likely seen it. | **High.** Core, theme, plugins and PHP all need updates. 11,334 new ecosystem vulnerabilities in 2025, 91% in plugins (Patchstack). | Managed host about $5–15/mo. Self-host on a VPS is $5/mo plus admin time. | Good. WXR export, but it needs a database plus uploads, and lock-in to plugin shortcodes. | Varies by theme and plugins. Bloat creeps in. | Low with a block theme | Very healthy. 7.0 shipped May 2026. | **Lowest people risk** (huge talent pool). Highest neglect risk: an unpatched WordPress site gets compromised. |
| **Grav (flat-file, PHP)** | Good. New "Admin Next" admin in Grav 2. Edits go live on save. | Medium/high. PHP 8.3+ host, plugin compatibility churn. 2.0 was a migration, not an upgrade. | PHP host about $3–10/mo, or a VPS. No free static option. | Good. Flat files, no database. Copy the folder. | Good | Medium (Twig) | Alive: 2.0 stable Jun 2026, 2.1 and 2.2 since. **Lead developer says the core team is "down to just me"** (Andy Miller). The new admin was alpha during the release candidate, and classic admin plugins no longer work. | **High.** Single-maintainer project, small talent pool, server to keep patched. |
| **Kirby (flat-file, PHP)** | **Best panel** of the PHP options. Purpose-built structured fields (coach bios, sponsors). | Medium. PHP host, few plugins needed. | PHP host plus license: Basic €99 per site (3 years of updates, €59 to renew). Nonprofits may get it free on application. | Good (flat files) | Good | Medium/high | Healthy, commercial (Kirby 5). | Medium/high. **Source-available, not open source.** Small talent pool, license renewal is an admin task. |
| **Ghost** | Excellent writing editor | Medium/high. Ghost 6 self-host is Docker Compose with MySQL 8 and extra services. | Ghost(Pro) about $15–18/mo, with **no nonprofit discount** beyond annual billing. VPS self-host about $6/mo. | Good (JSON export) | Good | Medium (Handlebars) | Very healthy | Medium. Blog/newsletter-first. Parent guides, glossary, sponsors and bios are awkward to model. |
| **Payload / Directus (headless)** | Good admin, but needs a custom-built front end | High (Node app, database, separate front end) | VPS plus database | Medium (database dumps) | Depends on build | **High** (custom development) | Payload owned by Figma since 2025. Directus moved to the MSCL license in v12 (Apr 2026), which is not open source. | **Very high.** Developer-only. Reject. |
| **TinaCMS** | Good visual editing | Self-host means running your own database, auth and GraphQL backend | Tina Cloud free for 2 users. Paid tiers unclear. | Good (Markdown in Git) | Excellent | Medium/high (React) | Active | High. Self-host is complex. Cloud is SaaS lock-in for login. Reject. |

## Ranked recommendation

1. **Top choice: Hugo static site + Sveltia CMS, on club-owned accounts.**
   - Nothing to patch, $0 hosting, and the most portable content of any option (Markdown in Git).
   - If Nick leaves, the site keeps serving and editors keep publishing. A future volunteer can open the repository and read plain files.
   - Hugo is a single pinned binary, so a build from 2026 still runs in 2029. Astro's npm dependencies do not offer that.
   - Sveltia's main risk is its one lead developer. Decap reads the same `config.yml`, so the club can switch editors in an hour if Sveltia stalls.
   - Swap in **Pages CMS** for the editor if the board insists on email-invite logins without Git accounts. That requires moving the repository to GitHub.
2. **Runner-up: WordPress on a club-paid managed host** (about $5–15/month). Choose it if the board values "any volunteer already knows it" over cost and maintenance. Conditions: a block theme, five or fewer plugins, auto-updates on, host-run backups, and a named owner for updates each season. Without that owner it degrades quickly.
3. **Grav ranks third.** It is a pleasant flat-file CMS, but it does not beat the top two on any criterion that matters here:
   - It still needs a PHP server, so it carries the maintenance burden of WordPress without WordPress's talent pool.
   - Its project bus factor is one person, and Grav 2 just replaced the admin and broke classic admin plugins.
   - If the club wants an in-browser, on-server CMS, WordPress is the safer bet. If it wants low maintenance, static wins.
4. Kirby is the best server-side editor, but it fails the open-source requirement and adds a license renewal. Ghost suits a newsletter, not a reference site. Payload, Directus and TinaCMS are developer platforms and are rejected.

## Recommended hosting setup (top choice)

Principle: **the club owns every account and the domain. Nick owns nothing the site depends on.** Nick's homelab and his GitLab get only a backup mirror.

1. **Domain:** registered to the club, with the login under a role address such as `webmaster@<club domain>` and the password in the club's shared password manager. At least two board members hold access.
2. **Repository:** a public project in a club-owned **GitLab.com** group with two or more board members as Owners.
   - GitLab supports Sveltia's client-side PKCE login, so no auth server is needed. Sveltia removed its GitLab authenticator in v0.263 because PKCE replaces it.
   - Public visibility avoids GitLab.com's 5-user cap on private free namespaces (verify current terms). Everything in the repository is published on the site anyway.
   - Editors get the Developer role. Guest and Reporter roles cannot sign in to Sveltia.
3. **Build and hosting:** GitLab CI with a pinned Hugo container image, publishing to **GitLab Pages** with the club's custom domain and its automatic HTTPS certificate. A Hugo build takes seconds, well inside the free CI minutes.
4. **Backup:** a pull mirror on Nick's GitLab and/or Codeberg. Any clone is a complete backup, and no database exists.
5. **Fallback hosts**, ranked:
   1. Cloudflare static assets on a club-owned account (free, fast, US company). Use Workers static assets, because Cloudflare Pages gets no new features.
   2. Codeberg Pages, which fits the sovereignty goal best. It is mid-migration to its new git-pages server (old sites stop serving 2026-12-31). Its terms favor free-licensed content, which matters for photos of minors. Check both before using it.
   3. Avoid Netlify. Free-plan sites were wrongly paused in mid-2026 (credit-flag bug reports), and its Git Gateway editor login is deprecated.
6. **Not recommended as primary:** Nick's homelab or GitLab, or a club VPS. A VPS brings back the patching chore the static choice removes. The homelab puts the site on one volunteer's power, internet and goodwill.
7. **Content layout:**
   - Hugo page bundles for news, coach bios and sponsors.
   - A data file for the glossary and sponsor list, edited as forms in Sveltia.
   - PDFs in a `files/` folder.
   - Calendar as a Google Calendar or SportsEngine iCal embed.
   - Large photo galleries stay in an external club album (Drive, Google Photos, or Flickr), with a few curated, resized images in the repository. Full-resolution galleries in Git bloat the repository permanently.
8. **Handoff kit** in the repository `README`:
   - How to add an editor.
   - How to publish a post.
   - Who the account owners are.
   - How to rebuild if CI breaks: run `hugo` locally with the pinned version.

## Main risks

1. **Editor onboarding friction.** Each editor needs a GitLab account and an invite. Mitigate with a one-page guide and two club Owners. If this proves unacceptable, move to GitHub with Pages CMS (email invites) rather than to a server CMS.
2. **Sveltia maintainer concentration.** One lead developer, still 0.x after slipping its 1.0 date. Releases come very often, so pin a version instead of loading the latest from a CDN. Decap is the drop-in fallback.
3. **Layout changes still need a technical person.** Editors can change content, not templates. Choose a well-maintained Hugo theme and avoid heavy customization, so a freelancer or the next technical volunteer can pick it up.
4. **Account ownership drift.** The most common real-world failure: the domain or the Git group sits on a departed volunteer's personal email. Use role addresses and two Owners, and review access at each board turnover.
5. **Photo and child-safety policy.** The repository is public and keeps history, so a photo removed from the site stays in Git history unless the history is rewritten. Set a photo policy (consent, no full names with photos of minors) before launch.
6. **Sveltia limits to check in a pilot:** whether it has a drafts-and-review workflow, preview fidelity, and gallery field ergonomics.

## Sources

- Grav 2 stable: https://getgrav.org/blog/grav-2-stable-released
- State of Grav 2026: https://www.getgrav.org/blog/state-of-grav-2026
- Grav "core team is down to just me": https://getgrav.org/forum/general/r-i-p-grav-cms-its-alive-t8780
- Grav 2 developer upgrade guide (classic admin removed): https://learn.getgrav.org/20/migration/developer-upgrade-guide
- Grav admin2 repo (alpha status): https://github.com/getgrav/grav-plugin-admin2
- Sveltia releases: https://github.com/sveltia/sveltia-cms/releases
- Sveltia GitLab backend docs: https://sveltiacms.app/en/docs/backends/gitlab
- Decap releases: https://github.com/decaporg/decap-cms/releases
- Decap GitLab backend (PKCE): https://decapcms.org/docs/gitlab-backend/
- Decap blog (Turbo): https://decapcms.org/blog/
- Netlify Identity deprecation: https://netlify.com/changelog/deprecation-netlify-identity
- Netlify free-plan pause reports: https://answers.netlify.com/t/free-plan-paused-appears-to-be-the-known-july-august-2026-credit-flag-bug/168840
- Pages CMS FAQ: https://pagescms.org/
- Kirby pricing: https://getkirby.com/buy
- Ghost(Pro) discounts: https://ghost.org/help/ghostpro-discounts/
- Ghost Docker install: https://docs.ghost.org/install/docker
- WordPress 7.0 schedule: https://make.wordpress.org/core/2026/04/22/wordpress-7-0-release-party-updated-schedule/
- Patchstack 2025 analysis: https://patchstack.com/whitepaper/state-of-wordpress-security-in-2026/
- Directus v12 license change: https://directus.io/blog/directus-v12-license-change
- Cloudflare acquires Astro: https://www.cloudflare.com/press/press-releases/2026/cloudflare-acquires-astro-to-accelerate-the-future-of-high-performance-web-development/
- Cloudflare Pages to Workers migration: https://developers.cloudflare.com/workers/static-assets/migrate-from-pages/
- Codeberg Pages migration: https://docs.codeberg.org/codeberg-pages/migrating-from-pages-v2/
