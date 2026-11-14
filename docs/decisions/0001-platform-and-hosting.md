# 0001 — Website platform and hosting

Status: accepted (2026-11-14, Nick DeMarco for Triangle Rowing Club)
Pace: Website project (Pace project 44, under Triangle Rowing Club, project 43) — https://pace.demar.co/projects/trc-website

## Decision

1. **Site generator: Hugo.** The site is built ahead of time into static HTML. No database or PHP runs on the live site.
2. **Editor: Sveltia CMS.** Volunteers edit pages in the browser at `/admin`. Saving commits to Git and triggers a rebuild. Decap CMS reads the same config and is the fallback if Sveltia stalls.
3. **Git host: GitHub**, in an organization owned by the club. The repository is public; the site content is public anyway.
4. **Web server: Hetzner**, on a small cloud server in an account owned by the club (role email address, club payment card, at least two board members with access). Caddy serves the built files with automatic HTTPS. The server also hosts small scheduled jobs (calendar feed refresh) and, if wanted, a contact-form handler.
5. **Staging first:** the new site is served at `dev.trianglerowing.org` while it is built and reviewed, with search-engine indexing blocked (`X-Robots-Tag: noindex` and a disallow-all `robots.txt`). `trianglerowing.org` and `www` stay on SportsEngine until a separate launch cutover.
6. **Domain and DNS:** the club holds trianglerowing.org (primary), .com and .net, all in Cloudflare and all verified on the club's GitHub organization `trianglerowing`. Observed 2026-11-14: .com redirects (301) to https://trianglerowing.org/; .net has no redirect and returns 404. For .org, registrar and DNS are both Cloudflare (registered 2009-06-26, expires 2027-06-26). TRC email runs on Google Workspace through MX records in Cloudflare; no website change touches MX records.
7. **Stays on SportsEngine:** registration, payments, rosters, member logins. The site links out to the SportsEngine registration forms.

## Why

- Volunteers turn over every year or two. The site must keep working, and be editable by non-technical people, after the technical volunteer leaves.
- A static site has nothing on the web side to patch. Hugo is one program pinned to one version, so the build does not rot when untouched.
- Content is Markdown plus images in Git. Every clone is a full backup, and moving to another host or platform is a copy, not a migration.
- GitHub over Codeberg: the club does not weigh the Microsoft distinction, and GitHub gives the best Sveltia support, Pages CMS as an email-invite editor option, wider volunteer familiarity, and mature build tooling.
- Hetzner over free static hosting: club-controlled, low cost (about €4–5/month), and a place for scheduled jobs and small dynamic pieces.
- Every account (domain, GitHub organization, Hetzner) is owned by the club, not a person, so a volunteer leaving is a credential handover rather than a loss of control.

## Rejected

- **Grav:** PHP server to maintain; core team down to one developer; Grav 2 upgrade is a migration.
- **WordPress:** easiest handoff by familiarity, but the most upkeep and security exposure (plugins).
- **Ghost, Kirby, Payload, Directus, TinaCMS:** wrong fit (newsletter focus), license cost or non-open-source license, or need a developer to build the front end.
- **Codeberg / self-hosted Forgejo:** viable; not chosen for editor convenience. Self-hosting Forgejo would add a Git server holding editor logins for the club to patch.
- **Nick's homelab or git.demar.co:** the club's site would depend on one volunteer's personal infrastructure.

## SportsEngine must keep working throughout

Registration, payments, rosters and member logins run on SportsEngine for the whole project and after it. No step may interrupt them.

- **Read-only toward SportsEngine.** Migration, calendar feeds and inventory only read SportsEngine. Nothing is deleted, unpublished or edited in the SportsEngine admin until after launch, and then only by a separate, explicitly approved step.
- **DNS changes are additive until launch.** The only pre-launch DNS change is adding `dev.trianglerowing.org`. The `trianglerowing.org` and `www` records, MX records, and every TXT record (mail authentication, domain verification) stay unchanged.
- **Link to SportsEngine on its own hostname.** Registration, login and payment links use `triangle-rowing-club.sportngin.com/...`, never a `trianglerowing.org` path, so they keep working when `www` moves. Registration is linked, not embedded in an iframe.
- **Launch cutover is its own planned step**, with a rollback (restore the previous `www` and apex records), done outside registration deadlines, and checked against SportsEngine's custom-domain setting before any record changes.

## Constraints that follow

- **Photos of minors:** the public repository keeps history after a file is removed. Full galleries live in an external club photo album; the repository holds only selected, consented images. A photo policy is set before launch.
- **Editors** need a GitHub account and an invite to the organization. A one-page editor guide is part of launch.
- **Access review** at each board turnover: domain registrar, GitHub organization owners, Hetzner account.

## Research behind this decision

`docs/research/platform-evaluation.md`, `docs/research/trc-site-inventory.md`, `docs/research/peer-club-survey.md`.
