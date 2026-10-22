# Solenhive Website — Claude Code Instructions

## Project overview
Single-page marketing site for Solenhive: paid media strategy plus the software that checks every tag is doing its job, sold to agencies and multi-location brands, white-label ready. Operated by Marc Carlton LLC. Static HTML/CSS/JS on Vercel.

## Tech stack
- Pure HTML, CSS, JavaScript — no frameworks, no build tools
- Pages: `index.html`, `privacy-policy.html`, `terms-of-service.html`
- Assets: `images/solenhive-logo-dark.svg` (header logo), `favicon-32.png`, `favicon-192.png`, `apple-touch-icon.png`, `images/marc-carlton.{webp,jpg}` (founder photo, 720×900, 4:5)
- Fonts: Google Fonts — Barlow Condensed, Work Sans, DM Mono
- Deployed via Vercel (auto-deploys on push to `master`)

## File structure
```
solenhive-website/
├── index.html
├── privacy-policy.html
├── terms-of-service.html
├── favicon-32.png
├── favicon-192.png
├── apple-touch-icon.png
├── images/
│   ├── solenhive-logo-dark.svg
│   ├── marc-carlton.webp
│   └── marc-carlton.jpg
├── solenhive-logo.svg      ← old file with live Gill Sans text; not used on the site; never modify
├── solenhive-brand-guide.md
└── CLAUDE.md               ← this file
```

---

## Positioning and copy rules — never violate these

- **Never name products on the public site.** Describe capabilities only (tag & pixel compliance, client reporting, retainers & billing, paid media analytics). Products get white-labeled by partners, so names stay off the site, the legal pages, and meta tags.
- Headline: "We run the media. We build the tools." (always two lines). Audience: agencies and multi-location brands.
- Mark a module "Live" only if it runs in production today; otherwise "In build". Never list planning-stage ideas.
- **No employer references** anywhere in this repo (no current employer, no automaker brand names). The founder bio stays as written unless Marc changes it.
- No client names, logos, screenshots, or results without the client's written sign-off.
- Scan data must stay anonymized: no site URLs, pixel IDs, site-platform vendor names, or industry-specific terms ("dealer", "OEM", "SRP").
- Scan numbers must match across the hero waterfall, the punchline, the findings, and the coverage table. "Sending data" means the tag sent events, not just a network request.
- Severity uses color plus a text label (Error / Warning), never color alone.
- No invented stats, prices, timings, or testimonials. If a fact is missing, leave the element out — never ship a `[PLACEHOLDER]`.
- Plain English, sentence case, active voice. Buttons say what happens ("Email the details", not "Submit"). Never use: "leverage", "synergy", "disrupt", "innovative", "cutting-edge".

---

## Design system

### The one loud element
The hero's **tag waterfall** — a browser-style timeline of every tag on one real scanned site, with a playhead that sweeps once on load. It is the page's only animation and its only dense, data-heavy element. Everything else stays quiet. Do not add a second showpiece, card grids, or scroll-triggered effects.

### Template tells to keep out
- No all-caps eyebrow labels above headings; no letter-spaced uppercase anywhere
- No identical bordered card grids; no big-number stat tiles
- No "A · B · C" meta strings; no arrows appended to links
- Monospace (DM Mono) only inside the waterfall, nowhere else
- Numbered markers only for real sequences (the four audit steps)

### Colors
```
--navy:     #0d1b2e   ← page background
--navy-mid: #132238   ← waterfall panel, form fields
--line:     #1e3a5f   ← rules and borders; logo circle
--gold:     #e8c44a   ← CTAs, firing tags, "Live" status, audit step numbers
--white:    #ffffff   ← primary text
--muted:    #8fa3bb   ← secondary text (passes 4.5:1 on both navies)
--alert:    #ff8a7a   ← Error severity only
```
`#5a6a7e` fails contrast for small text — do not use it for text.

### Typography
- Headings: **Barlow Condensed** 300 (400 for h3), sentence case, tight leading
- Body: **Work Sans** 300, 18px base (19px at ≥1800px), line length ≤ 62ch
- Scale: perfect fourth — 15 / 18 / 24 / 32 / 57 / 128 (fluid via clamp)
- Waterfall data only: **DM Mono** 13px
- Never use weight 600 or 700

### Layout
- 12-column grid, left-aligned, max width 1320px (1440px at ≥1800px), gutter `clamp(20px, 4.5vw, 64px)`
- Section padding `clamp(88px, 11vw, 168px)`, separated by a single 1px rule
- Breakpoints: 1080px (two-column sections stack), 900px (hamburger menu), 720px (waterfall rows stack name over bar; forms go single column), 380px (smaller logo and step numbers)

### Logo
- Header logo is `images/solenhive-logo-dark.svg`: a vector traced from Marc's 3000px master PNG. Letterforms and honeycomb geometry are the master's; colors swapped for dark backgrounds only (letters white, circle `#1e3a5f`, cells `#e8c44a`). Shown 34px tall, same `<img>` on all three pages.
- Header uses wordmark + mark without the tagline (unreadable at header size; the brand standard allows this for app headers).
- Favicons are cropped from the same master mark.
- Never retype the wordmark in a font, redraw the mark, use a downscaled raster, or recolor with CSS filters. To regenerate, re-trace the master.

---

## Home page sections (in order)
1. **Header** — sticky; logo left; Findings · Platform · Audit · About; "Book an audit"; hamburger below 900px (Escape closes it)
2. **Hero** — two-line headline, intro, two buttons, the tag waterfall, then the punchline "Six Meta pixels. Two send a PageView. None send a lead."
3. **Findings** (`#findings`) — four findings from the waterfall's scan, plus the ad platform coverage table
4. **Platform** (`#platform`) — four modules as a list with Live / In build status, then the white-label statement
5. **Audit** (`#audit`) — four numbered steps, plus fractional media leadership and measurement setup
6. **About** (`#about`) — founder photo and bio
7. **Contact** (`#contact`) — form that composes an email to hello@solenhive.com (no backend yet), with inline validation messages
8. **Footer** — legal line, Privacy, Terms, email

Any element with `data-interest="…"` pre-selects that option in the contact form when clicked.

### Footer legal line (all pages, identical)
`&copy; <year> Marc Carlton LLC. Solenhive is operated by Marc Carlton LLC.` — update the year each January.

### Legal pages
- Operator is defined as "Marc Carlton LLC, doing business as Solenhive". Bump the page's effective date whenever its content (not just styling) changes.

---

## Quality floor (check before every push)
- No horizontal scroll at 320, 360, 390, 414, 768, 834, 1024, 1080, 1180, 1280, 1440, 1680, 1920, 2560 wide, and 844×390 phone landscape
- No clipped headings, buttons, or table cells; header stays one row
- Visible keyboard focus (gold outline); touch targets ≥ 44px; text contrast ≥ 4.5:1
- `prefers-reduced-motion`: waterfall renders static, no playhead
- Review screenshots at phone, tablet, laptop, and large-monitor widths — not just the automated checks

---

## Tracking
- Amazon Ad Tag in `index.html` `<head>`: PageView on load, `Contact` event on any mailto click and form submit.
- No GA4 yet. When adding it, add consent handling and update the Privacy Policy's tracking section in the same change.

---

## Deployment
- Big visual changes go to a preview branch first; merge to `master` after Marc approves
- `master` is the Vercel production branch; every push auto-deploys
- No build step — static files deploy as-is
- Custom domain: `solenhive.com`

---

## Do not
- Do not add npm, package.json, or build tooling
- Do not add CSS or JS frameworks
- Do not name products, clients, or employers (see Positioning)
- Do not use light backgrounds
- Do not ship placeholder text or placeholder images

---

*CLAUDE.md — Solenhive Website v3.0 · Last updated: October 2026*
