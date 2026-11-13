# Doppel: Visual Identity

Raw research, checked 2026-11-13. Source quality key as in `company.md`.

## Brand guidelines and press kit

- No public brand guidelines, press kit, media kit or logo download found.
- These URLs return 404: https://www.doppel.com/press , /company/press , /media-kit , /brand , /press-kit
- The newsroom (https://www.doppel.com/company/press-releases) has press releases and a "For media requests" contact, but no asset downloads. [P]

## Observed in the site code (not a stated brand guide)

Everything below was read from the homepage HTML and its stylesheets (https://www.doppel.com/ and its `/_next/static/css/` files) on 2026-11-13. These are the website's styling values, not official brand rules. [P, from code]

**Logo**
- Inline SVG with class `main-logo`, linked as "Doppel homepage". Wide horizontal shape (viewBox 1501 x 331), single fill `#0E1114` (near black). Whether it is a wordmark or a symbol plus wordmark was not checked visually.

**Colors (named CSS variables)**

| Variable | Hex |
|---|---|
| `--color-black`, `--color-bg` | `#1B141B` (also the browser `theme-color`) |
| `--color-yellow` | `#E7FF92` |
| `--color-purple` | `#DECAF9` |
| `--color-blue` | `#1C84FC` |
| `--color-orange` | `#FF9D52` |
| `--color-white` | `#F5F5F5` |
| Greys 100 to 600 | `#2D272D`, `#494349`, `#767276`, `#A4A1A4`, `#D1D0D1`, `#EDECED` |

- Most-used hex values in the CSS: `#1B141B` (22 uses), `#E7FF92` (18), `#F9FFE4` (16, a pale yellow used in gradients).

**Fonts**
- Suisse Intl (`suisseIntl`, CSS variable `--font-suisse`), the most-used family.
- TT Livret (`ttLivret`, CSS variable `--font-livret`).
- A system monospace stack for code-style text.
- Which font is used for headings and which for body text was not checked.

**Imagery (from the homepage text)**
- Product and threat-graph imagery ("Doppel Threat Graph"), a customer logo strip and a grid of award badges (G2, Fortune Cyber 60, SINET and others). Source: https://www.doppel.com/ [P]

## Not determined

Logo usage rules, clear space, the official palette and type scale. The site's dark background variable suggests a dark theme, but the theme was not checked visually.
