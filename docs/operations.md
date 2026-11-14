# Operating the website server

The site is plain files. GitHub builds them on every change to `main` (and nightly, to refresh calendar events) and uploads them to a small Hetzner Cloud server, where Caddy serves them over HTTPS. The website part of the server holds nothing that is not in this repository: if the server is lost, the website comes back with the steps below.

The server may also run other club services (for example a password vault). Those hold data that exists nowhere else, so the server has Hetzner Backups turned on, and each such service needs its own off-server backup, documented with that service. Their web server settings live in their own root-owned files in `/etc/caddy/sites/`, which the website's deploy key cannot change.

Why it is built this way: [decisions/0001-platform-and-hosting.md](decisions/0001-platform-and-hosting.md).

## Where things live

| Thing | Where | Who can change it |
|---|---|---|
| Site source, server setup, web server config | GitHub `trianglerowing/website` | Organization Owners; editors through `/admin` |
| Server | Hetzner Cloud project `trc-website` (club account) | Hetzner project members |
| Domain and DNS (trianglerowing.org, .com, .net) | Cloudflare (club account) | Cloudflare account members |
| Deploy key (private half) | GitHub secret `DEPLOY_SSH_KEY` | Organization Owners (write-only; nobody can read it back) |
| Server host keys | GitHub secret `DEPLOY_KNOWN_HOSTS` | Organization Owners |
| Server address | GitHub variable `DEPLOY_HOST` | Organization Owners |

On the server:

| Path | Contents |
|---|---|
| `/srv/trc/site/` | The built site (uploaded by GitHub) |
| `/srv/trc/redirects.caddy` | Old-address redirects, built from `data/redirects.yaml` (uploaded by GitHub; the deploy job refuses a file holding anything but redirects) |
| `/etc/caddy/Caddyfile` | Imports every file in `/etc/caddy/sites/` (root-owned, from `deploy/cloud-init.yaml`) |
| `/etc/caddy/sites/trc-website.caddy` | The website's web server settings (root-owned, from `deploy/cloud-init.yaml`) |

The `deploy` user can write `/srv/trc` and reload the web server, nothing else. Security updates install automatically every day.

## Build a server from scratch

Do this the first time, or to replace a broken server. Nothing on SportsEngine changes.

1. **Deploy key.** Skip if the `DEPLOY_SSH_KEY` secret exists and its public half is already in `deploy/cloud-init.yaml`. Otherwise create a new ed25519 key pair, store the private half as the `DEPLOY_SSH_KEY` repository secret, and put the public half in `deploy/cloud-init.yaml` (by pull request).
2. **Create the server.** Hetzner Cloud console → project `trc-website` → **Add Server**:
   - Location: Ashburn, VA (closest to Raleigh).
   - Image: Debian 13.
   - Type: a shared-CPU type with 4 GB of memory (room for other club services; the website alone needs far less). Arm64 or x86 both work.
   - **Backups:** on.
   - SSH key: the administrator's own public key (emergency access as root only).
   - **Cloud config:** paste the whole of `deploy/cloud-init.yaml` from `main`.
   - Name: `trc-website`. Create.
3. **Point the address at it.** Cloudflare → `trianglerowing.org` → DNS → add an `A` record: name `dev`, the server's IPv4 address, proxy status **DNS only** (grey cloud). Add an `AAAA` record with the IPv6 address the same way. Change no other record.
4. **Tell GitHub about the server.** Repository Settings → Secrets and variables → Actions:
   - Variable `DEPLOY_HOST`: `dev.trianglerowing.org`.
   - Secret `DEPLOY_KNOWN_HOSTS`: the output of `ssh-keyscan -t ed25519 dev.trianglerowing.org`, run a few minutes after the server starts.
5. **Deploy.** Actions → Build site → Run workflow on `main`. When both jobs are green, https://dev.trianglerowing.org shows the site with a valid certificate.

## Replace the deploy key

When a volunteer with Owner access leaves, or if the key may have leaked: create a new key pair, update the `DEPLOY_SSH_KEY` secret, and replace the line in `/home/deploy/.ssh/authorized_keys` on the server (as root). Update the public key in `deploy/cloud-init.yaml` too, so a rebuilt server matches.

## Change web server settings or redirects

**Redirects:** edit `data/redirects.yaml` in a pull request. After it merges, the deploy job uploads the new list and reloads the web server. If the result is invalid, the reload fails, the job turns red, and the server keeps running the previous settings.

**Web server settings for the website** (headers, the site address): these are root-owned on purpose, so the deploy key cannot change them. Edit `/etc/caddy/sites/trc-website.caddy` on the server as root, check it with `caddy validate --config /etc/caddy/Caddyfile`, then `systemctl reload caddy`. Make the same change to `deploy/cloud-init.yaml` by pull request so a rebuilt server matches.

## Launch cutover

A separate, planned step, not routine operation. It moves `trianglerowing.org` and `www` from SportsEngine to this server. Schedule it away from registration deadlines, with the rollback written down first (restore the previous `www` and apex DNS records). See the cutover note in the website's web server settings in `deploy/cloud-init.yaml`, and the SportsEngine rules in the decision record.
