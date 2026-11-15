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
| Headings | Aller Bold and Bold Italic, Standard Edition (Dalton Maag) | Dalton Maag Free Licence Agreement with EULA 1.2 (`static/fonts/Aller-Font-License.txt`) | Marketing shared drive, `fonts/Aller` folder (Font Squirrel release); files served unchanged |

The guide's body-font line is a placeholder ("XYZ font"). Urbanist is the default pending a club decision.

Headings are Aller Bold, the club's official font, set in capitals (Pace work package 2505, Aller headings: https://pace.demar.co/work_packages/2505). It is set once as `--font-heading` in `assets/css/main.css`. It replaced League Gothic, which the first home page redesign used.

## Text on color

Brand orange (#E87722) on white is 2.96:1 and navy on orange is 4.09:1, both below the 4.5:1 WCAG AA minimum for normal text. So:

- Orange text on white uses #B35500.
- Orange buttons carry navy text in bold Aller at 1.35rem or larger (WCAG large bold text, 3:1 minimum).
- Orange figures on navy are display size only.
- White text on a photo sits on a navy overlay at least 70% opaque.

All fonts are self-hosted under `static/fonts/` and declared in `assets/css/fonts.css`. The site loads nothing from Google Fonts or Adobe Fonts.

### Aller on the website

Decision (Nick DeMarco for the club): Nick reviewed the Aller licence (`static/fonts/Aller-Font-License.txt`, the Dalton Maag Free Licence Agreement with EULA version 1.2, from the Drive fonts folder) and approved Aller for the website's headings. How the site keeps within it:

- Only Standard Edition files are used (Free Licence clause 3). Aller Display, the logo font, is not covered and is not in the repository; the logo artwork is outlined shapes and needs no font.
- The files are served exactly as supplied, as TrueType, with no conversion to WOFF2, because the EULA forbids derivative works (clauses 9 and 20).
- The licence travels with the files (Free Licence clause 5).
- The free licence covers 25 Users, and 1,000 website visitors per day count as one User (Free Licence clauses 1-2, EULA clause 16): about 25,000 visitors a day, far above this site's traffic. If traffic ever approaches that, the club needs a commercial licence.

Fallback if the decision is ever reversed: change `--font-heading` in `assets/css/main.css` to an open-licence face and delete the `Aller_*` files.

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

Fonts in `static/fonts/`: `Aller_Rg.ttf`, `Aller_It.ttf`, `Aller_Bd.ttf`, `Aller_BdIt.ttf`, `Aller_Lt.ttf`, `Aller_LtIt.ttf`, `Aller-Font-License.txt`, `Urbanist-Regular.woff2`, `Urbanist-Italic.woff2`, `Urbanist-SemiBold.woff2`, `Urbanist-Bold.woff2`, `Urbanist-OFL.txt`.

Home page photos are in `assets/images/home/` (from the old SportsEngine site, board-approved; see `docs/photo-review.md`). Hugo resizes them at build time into WebP and JPEG at several widths; text, figures and alt text are in `data/home.yaml`.

Stylesheet: `assets/css/fonts.css` (font-face rules only).
