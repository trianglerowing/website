# Website editor guide

For Triangle Rowing Club volunteers. No technical background needed. Editor address: https://dev.trianglerowing.org/admin (after launch: https://trianglerowing.org/admin).

**Saving publishes.** Every save in the editor goes straight to the live site, which rebuilds within a few minutes. There is no draft step, so read your change before you save. To undo a mistake, edit the entry again and save the corrected version.

**What the site does not do.** Registration, payments, rosters and member logins stay on SportsEngine. You only change the links to SportsEngine and whether they show as open or closed. Never change anything in SportsEngine through the website.

## 1. Get access

1. Send your GitHub username to a club GitHub organization owner. If you have no GitHub account, create a free one at https://github.com/signup first.
2. The owner opens the organization People page (https://github.com/orgs/trianglerowing/people), chooses Invite member, enters your username, and gives you access to the `website` repository with write permission.
3. Accept the invitation in the email GitHub sends you.
4. Open https://dev.trianglerowing.org/admin and choose the GitHub sign-in.
5. If the sign-in button reports an error or is missing (the GitHub sign-in helper is still being set up), sign in with a personal access token instead:
   1. On GitHub, open Settings, Developer settings, Personal access tokens, Fine-grained tokens, Generate new token.
   2. Name it "TRC website editor" and choose an expiry (90 days or longer).
   3. Under Repository access, choose Only select repositories, then pick `trianglerowing/website`. Set Resource owner to `trianglerowing`.
   4. Under Permissions, Repository permissions, set Contents to Read and write. Leave everything else at No access.
   5. Choose Generate token and copy it once. Paste it into the editor's token sign-in box.
   6. Keep the token private. Never put it in an email or a page. If it leaks, delete it on the same GitHub page.

## 2. Open or close registration

1. In the editor, open **Club settings**, then **Registration, donations and season**.
2. Under **Registration links**, open the program (for example "Register for Learn to Row").
3. Switch **Registration open** on or off.
4. Save. Within a few minutes the register button on every page that uses it follows the switch.

To change where a button goes, edit **SportsEngine form link**. It must be a link on `sportngin.com`; the editor rejects anything else. To add a program, choose Add Program, fill **Short name used in pages**, **Button text**, **SportsEngine form link**, and **Registration open**. A new program needs a page author to place the button in page text (see section 9).

## 3. Update fees and season dates

1. Season name: **Club settings**, **Registration, donations and season**, field **Current season**. Save.
2. Fees and dates are written in the page text. Open **Pages**, then the program page (for example Programs and costs, High school).
3. Click in **Page text**, change the fee or date, and check the same figure on the Programs and costs overview page and the Financial aid page.
4. Save each page you changed.
5. Check that the fee matches what SportsEngine charges. The website only describes the fee; SportsEngine charges it.

Donate button: in the same Club settings screen, **Donate button** holds **Button text** and **Donation link**.

## 4. Post news

1. Open **News**, choose New News post.
2. Fill **Title**, **Date**, **Summary** (one sentence), and **Post**. Add a **Photo** only if the photo policy (section 8) allows it.
3. Save. The post appears on the News page.

To fix or remove a post, open it in **News**, edit and save, or delete it. A deleted post stays in the repository history (section 8).

## 5. Change coaches

1. Open **Coaches**.
2. To add: choose New Coach, fill **Name**, **Role**, **Order (lower numbers first)**, optional **Photo** and **Biography**. Save.
3. To change: open the coach, edit, save.
4. To remove: open the coach and delete it.

## 6. Change board members

Board members are listed in page text, not in a separate list.

1. Open **Pages**, then About, then the page that lists the board (use Contact if there is no board page yet).
2. In **Page text**, edit the names and roles. Do not publish personal phone numbers or home addresses; use the club's role email addresses.
3. Save.
4. At each board change, also complete the access checklist in section 10.

## 7. Add a sponsor

1. Open **Sponsors**, choose New Sponsor.
2. Fill **Name**, choose **Level**, and fill **Website**. Add the **Logo** if the sponsor gave permission.
3. Save. To remove a sponsor, open it and delete it.

## 8. Photos: swap a home-page photo and the photo policy

Swap a photo:

1. Open **Pages**, then the first page (Triangle Rowing Club, the home page).
2. In **Page text**, click the photo you want to replace and delete it.
3. Click where it was, choose the image button, and Upload the new photo (or pick one already uploaded). Add a short description of the photo for people who cannot see it.
4. Save.

Photo policy:

1. No identifiable minors without consent. If a rower under 18 can be recognized, you need written consent from a parent or guardian first. If unsure, leave the photo out. Photos from behind, from far away on the water, or of boats and oars are fine.
2. Full galleries go to the club photo album, not the website. Put only a few selected photos on the site.
3. Anything removed from the site stays in the public repository history. Deleting a photo hides it from the site but does not erase it, so check before you upload. If a photo must be erased completely, ask the site owner (section 11) right away.

## 9. Building blocks for page text

Type these in **Page text** (in Markdown mode) where you want the block to appear:

| Block | What it shows |
|---|---|
| `{{</* register program="sneak-peek-week" */>}}` | Register button for that program (uses the open/closed switch) |
| `{{</* donate */>}}` | Donate button |
| `{{</* calendar feed="high-school" limit="10" */>}}` | Upcoming events |
| `{{</* video id="VIDEO_ID" title="What it shows" */>}}` | YouTube video |
| `{{</* embed src="https://..." title="What it shows" height="600" */>}}` | Another web page inside the page |

The page `/style-guide/` shows every block.

## 10. Board-turnover access checklist

Do this at every board change. The club owns every account; no account belongs to a person.

1. Domain registrar and DNS: the Cloudflare account that holds trianglerowing.org, .com and .net. Add the new officer, remove the leaving one, and confirm the account email is a club role address and two board members can sign in.
2. GitHub organization owners: on https://github.com/orgs/trianglerowing/people, confirm at least two current board members are Owners. Remove people who left; downgrade editors who no longer edit.
3. Hetzner Cloud project members: confirm at least two current board members are members, and the payment card and billing email belong to the club.
4. The club role mailbox: change its password or sign-in recovery, and confirm the current board can receive its mail.
5. Delete any personal access tokens that departing editors created (they can do this on GitHub).

## 11. Who to ask

Ask the club's website owner on the board, or the club role mailbox. Why the site is built this way: `docs/decisions/0001-platform-and-hosting.md`.
