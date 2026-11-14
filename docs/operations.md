# Operating the website server

The site is plain files. GitHub builds them on every change to `main` (and nightly, to refresh calendar events) and uploads them to one small Hetzner Cloud server, where Caddy serves them over HTTPS. The server holds nothing that is not in this repository, so it needs no backup: if it is lost, build a new one with the steps below.

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
| `/srv/trc/Caddyfile` | Web server config, a copy of `deploy/Caddyfile` (uploaded by GitHub) |
| `/srv/trc/redirects.caddy` | Old-address redirects, built from `data/redirects.yaml` (uploaded by GitHub) |
| `/etc/caddy/Caddyfile` | One line importing `/srv/trc/Caddyfile` (from `deploy/cloud-init.yaml`) |

The `deploy` user can write `/srv/trc` and reload the web server, nothing else. Security updates install automatically every day.

## Build a server from scratch

Do this the first time, or to replace a broken server. Nothing on SportsEngine changes.

1. **Deploy key.** Skip if the `DEPLOY_SSH_KEY` secret exists and its public half is already in `deploy/cloud-init.yaml`. Otherwise create a new ed25519 key pair, store the private half as the `DEPLOY_SSH_KEY` repository secret, and put the public half in `deploy/cloud-init.yaml` (by pull request).
2. **Create the server.** Hetzner Cloud console → project `trc-website` → **Add Server**:
   - Location: Ashburn, VA (closest to Raleigh).
   - Image: Debian 13.
   - Type: the smallest shared-CPU type offered.
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

Edit `deploy/Caddyfile` or `data/redirects.yaml` in a pull request. After it merges, the deploy job uploads the files and reloads the web server. If the new config is invalid, the reload fails, the job turns red, and the server keeps running the previous config.

## Launch cutover

A separate, planned step, not routine operation. It moves `trianglerowing.org` and `www` from SportsEngine to this server. Schedule it away from registration deadlines, with the rollback written down first (restore the previous `www` and apex DNS records). See the end of `deploy/Caddyfile` and the SportsEngine rules in the decision record.
