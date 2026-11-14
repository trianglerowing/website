# TRC brand

Source: the "TRC brand guide" Google Doc in the Marketing shared drive (Branding folder). Pace work package 2488 (import brand assets and settle web fonts): https://pace.demar.co/work_packages/2488

## Name

Triangle Rowing Club. "TRC" is acceptable where space or brevity requires it.

## Colors

| Color | Pantone | Web (hex) | CMYK |
|---|---|---|---|
| Orange | 158 C | #E87722 | 0% 48% 85% 4% |
| Navy blue | 534 C | #1B365D | 71% 42% 0% 64% |
| White | none | #FFFFFF | 0% 0% 0% 0% |

The brand guide lists white's web color as #000000. That is an error (black); white is #FFFFFF. Pantone colors cannot be previewed on a monitor; use the hex values on screen.

## Fonts

| Use | Font | License | Source |
|---|---|---|---|
| Body text | Urbanist (Regular, Italic, SemiBold, Bold) | SIL Open Font License 1.1 (`static/fonts/Urbanist-OFL.txt`) | https://github.com/coreyhu/Urbanist (official WOFF2 in `fonts/webfonts`) |
| Headings | League Gothic 1.601 (Regular) | SIL Open Font License 1.1 (`static/fonts/LeagueGothic-OFL.md`) | https://github.com/theleagueof/league-gothic (official release, `static/WOFF2`) |

The guide's body-font line is a placeholder ("XYZ font"). Urbanist is the default pending a club decision.

Headings are League Gothic, a condensed athletic face the old trianglerowing.org site already used, set in capitals at large sizes (Pace work package 2502, home page redesign: https://pace.demar.co/work_packages/2502). It has one weight, so headings are never bolded. It is set once as `--font-heading` in `assets/css/main.css`.

## Text on color

Brand orange (#E87722) on white is 2.96:1 and navy on orange is 4.09:1, both below the 4.5:1 WCAG AA minimum for normal text. So:

- Orange text on white uses #B35500.
- Orange buttons carry navy text in League Gothic at 2rem or larger (WCAG large text, 3:1 minimum).
- Orange figures on navy are display size only.
- White text on a photo sits on a navy overlay at least 70% opaque.

All fonts are self-hosted WOFF2 under `static/fonts/` and declared in `assets/css/fonts.css`. The site loads nothing from Google Fonts or Adobe Fonts.

### Aller: web use not permitted

Aller (Dalton Maag) is the official club font, and the logo uses Aller Display. The license supplied with the Drive fonts folder (`Aller Font License.txt`: the Font Squirrel release of the Dalton Maag Free Licence Agreement plus End User Licence Agreement version 1.2) does not allow self-hosted WOFF2 on this site:

- Free Licence clause 3: "Editions other than the Standard Edition of the Aller Font Family are not covered by this Free Licence Agreement, and require a commercial licence." Aller Display is not the Standard Edition.
- EULA clause 16: the licensee "may convert the Font Software to EOT format (or other format which Dalton Maag may from time-to-time make it known that it allows under specific terms) for installation on the Licensee's Website." WOFF2 is not named.
- EULA clause 20: "The Licensee shall not produce Derivative Works of this Font Software except for document embedding and permitted conversions"; clause 9 defines a Derivative Work as data "in any format into which Font Software may be converted".
- Free Licence clause 5: redistribution only as a verbatim copy of the supplied .zip, so font files cannot be committed to a repository.
- Free Licence clauses 1-2: capped at 25 Users, with 1,000 website visitors per day counting as one User.

Decision: no Aller files are in the repository. Adobe Fonts also licenses web use only through an Adobe subscription and loads from Adobe servers, which breaks the no-third-party-requests rule. Aller remains usable for print; the logo artwork is outlined shapes and needs no font.

Aller stays the print and logo font; League Gothic is the web heading font.

## Logos

Usage rules from the guide:

- The shield is the primary logo and the brand. It appears above and more prominently than any other logo on a piece.
- Secondary logos (for example the eight-boat logo) are used for wide, short applications, when the shield's proportions do not fit, when detail is insufficient, when a piece calls for multiple logos, or for a specific need (such as the North Carolina outline with Raleigh highlighted). They use the club colors and font.
- The logo is rarely modified. The one exception is the Erg-a-thon logo, where the rowers are replaced by erg-ers.

## Files

Logo files in `assets/brand/`:

| File | Description |
|---|---|
| `shield.svg` | Primary shield, for white backgrounds (from `TRC shield for white background.svg`) |
| `shield-on-blue.png` | Primary shield for blue backgrounds, 770 px wide (from `TRC shield for blue background.png`) |
| `eight-boat-on-white.svg` | Eight-boat with coxswain, for white backgrounds (converted from the Illustrator-compatible PDF) |
| `eight-boat-on-blue.svg` | Eight-boat with coxswain, for blue backgrounds |

Not imported: the Erg-a-thon, winter holiday, oar blade and North Carolina map logos exist only as Illustrator files in Drive (no web export). Illustrator source files are not committed. Export web versions in Drive if needed.

Fonts in `static/fonts/`: `LeagueGothic-Regular.woff2`, `LeagueGothic-OFL.md`, `Urbanist-Regular.woff2`, `Urbanist-Italic.woff2`, `Urbanist-SemiBold.woff2`, `Urbanist-Bold.woff2`, `Urbanist-OFL.txt`.

Home page photos are in `assets/images/home/` (from the old SportsEngine site, board-approved; see `docs/photo-review.md`). Hugo resizes them at build time into WebP and JPEG at several widths; text, figures and alt text are in `data/home.yaml`.

Stylesheet: `assets/css/fonts.css` (font-face rules only).
