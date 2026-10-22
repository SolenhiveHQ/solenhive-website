# Solenhive Website — Claude Code Instructions

## Project overview
Single-page marketing site for Solenhive: paid media strategy plus the software that checks every tag is doing its job, sold to agencies and multi-location brands, white-label ready. Operated by Marc Carlton LLC. Static HTML/CSS/JS on Vercel.

## Tech stack
- Pure HTML, CSS, JavaScript — no frameworks, no build tools
- Pages: `index.html`, `privacy-policy.html`, `terms-of-service.html`
- Assets: `images/solenhive-logo-dark.svg` (header logo), `images/solenhive-mark.svg` (mark only, hero seam), `favicon-32.png`, `favicon-192.png`, `apple-touch-icon.png`, `images/marc-carlton.{webp,jpg}` (founder photo, 720×900, 4:5)
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
│   ├── solenhive-mark.svg
│   ├── marc-carlton.webp
│   └── marc-carlton.jpg
├── solenhive-logo.svg      ← old file with live Gill Sans text; not used on the site; never modify
├── solenhive-brand-guide.md
└── CLAUDE.md               ← this file
```

---

## Positioning and copy rules — never violate these

- **Never name products on the public site.** Describe capabilities only (tag & pixel compliance, client reporting, retainers & billing, paid media analytics, search & AI visibility). Products get white-labeled by partners, so names stay off the site, the legal pages, and meta tags.
- Headline: "We run the media." | "We build the tools." — one per half of the split hero. Media side speaks to multi-location brands; tools side to agencies and resellers.
- The page covers both sides equally: the platform (all five modules), the media practice, and the audit. The scan is proof, not the whole story.
- Mark a module "Live" only if it runs in production today; otherwise "In build". Never list planning-stage ideas.
- **No employer references** anywhere in this repo (no current employer, no automaker brand names). The founder bio stays as written unless Marc changes it.
- No client names, logos, screenshots, or results without the client's written sign-off.
- Scan data must stay anonymized: no site URLs, pixel IDs, site-platform vendor names, or industry-specific terms ("dealer", "OEM", "SRP").
- Paid media analytics tab shows real budget-planner output for the example saved in the planner (inputs, recommended media spend, five-channel split). Never show the source dealer, brand, fee line, per-unit gross, or automotive channel terms (VDP, AIA).
- Billing tab shows two real retainer cycles from the invoicing app: hours only. Never show client names, rates, dollar amounts, invoice numbers, or time-entry descriptions (they name clients' customers).
- Scan numbers must match across the hero waterfall, the punchline, the findings, and the coverage table. "Sending data" means the tag sent events, not just a network request.
- Severity uses color plus a text label (Error / Warning), never color alone.
- No invented stats, prices, timings, or testimonials. If a fact is missing, leave the element out — never ship a `[PLACEHOLDER]`.
- Plain English, sentence case, active voice. Buttons say what happens ("Email the details", not "Submit"). Never use: "leverage", "synergy", "disrupt", "innovative", "cutting-edge".

---

## Design system

### Concept: the page is shaped like the logo
The logo is "solen · mark · hive" — two words joined by the honeycomb. The hero repeats that shape: **We run the media** | the mark on a honeycomb seam | **We build the tools** (layout 9, split screen: two sides of the business, one binary choice for the visitor).

### The hive line (what connects everything)
- A honeycomb edge (zigzag) is the only connective device. It forms the hero seam, then runs down the left gutter through every section (≥1080px), with a hex cell at each section heading that turns gold once the visitor reaches it.
- On phones the seam turns horizontal between the stacked halves, with the mark on it; the gutter thread is hidden.
- The same line joins the steps in the platform flow diagrams.
- Draw it only with the `--hive-v`, `--hive-h`, `--cell`, `--cell-on` tokens in `index.html`. Don't add other connectors, dividers, or decorative hexagons.

### The one loud element
The **tag waterfall** in the platform's first tab — a browser-style timeline of every tag on one real scanned site. Its playhead sweeps once when the waterfall scrolls into view; it is the page's only data-heavy element and only scripted animation. Other platform tabs use simple flow diagrams until real product screens exist (swap in real output when Marc supplies it; never invent numbers).

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
- Source of truth: the invoicing app's official dark SVG (`https://invoicing.solenhive.com/solenhive-logo-dark.svg`): text as vector paths, seven gold cells clipped in a circle filled `#0D1B2E`, so the mark sits clean on navy. Never re-trace, retype, recolor, or use a raster of it.
- `images/solenhive-logo-dark.svg` — header lockup: that file with the rule and tagline removed and the viewBox cropped (`22 19 512 94`), shown 34px tall on all three pages.
- `images/solenhive-lockup-dark.svg` — the untouched full lockup with tagline, for large placements only (the tagline is unreadable under ~500px wide).
- `images/solenhive-mark.svg` — the mark alone (circle, clip, cells) for the hero handle and phone seam. Favicons (`favicon-32.png`, `favicon-192.png`, `apple-touch-icon.png`) are rendered from it. The invoicing app's `app/favicon.ico` and `app/apple-icon.png` come from the same mark.

---

## Home page sections (in order)
1. **Header** — sticky; logo left; Platform · Findings · Media (slides the hero) · About; "Book an audit"; hamburger below 900px (Escape closes it)
2. **Sliding split hero** — left: "For multi-location brands / We run the media." (h1); right: "For agencies and resellers / We build the tools." The mark is a drag handle (`role="slider"`, arrow keys, Home/End, Enter centers) on the hive-line seam. Snap points: 24 / 50 / 76. Dragging or "How we run media" / "See the platform" opens that side: its intro is replaced by detail (media practice areas, or the four modules), and the other side narrows to its headline plus a "Show media" / "Show tools" button. Height `clamp(520px, 66vh, 640px)`. Below 901px there is no slider: halves stack, the seam turns horizontal with the mark on it, and the same buttons expand each side's detail in place. The nav's "Media" link slides to the media side.
3. **Platform** (`#platform`) — five accessible tabs (arrow keys, Home, End): Tag & pixel compliance (waterfall + punchline), Client reporting (flow), Retainers & billing (two real cycles), Paid media analytics (In build; real planner output), Search & AI visibility (In build; discovery, context, consumption flow); then the white-label statement
4. **Findings** (`#findings`) — what broken tracking costs the media budget: four findings from the scan + coverage table (the bridge between the two sides)
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
- Without JavaScript the waterfall shows its final state and the first tab is visible
- Review screenshots at phone, tablet, laptop, and large-monitor widths — not just the automated checks

---

## Tracking
- Amazon Ad Tag in `index.html` `<head>`: PageView on load, `Contact` event on any mailto click and form submit.
- The tag is NOT loaded when the browser sends Global Privacy Control or Do Not Track (a no-op `window.amzn` is set first). No `<noscript>` pixel: it can't check those signals. The Privacy Policy promises this behavior — keep them in sync.
- No GA4 yet. When adding it, apply the same signal check, add consent handling, and update the Privacy Policy in the same change.

### Policy pages must match the site
- Privacy Policy lists every service that touches visitor data (Vercel, Google Fonts, Amazon Ads, Google Workspace), Amazon's required interest-based-ads disclosure and opt-out links, and the GPC/DNT behavior. Adding or removing any third-party script, font, form backend, or analytics tool means updating it in the same commit and bumping its effective date.
- Terms of Service: paid services and platform access run under separate written agreements; the real examples on the Site are illustrations, not promises of results; "In build" modules carry no release guarantee.

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

*CLAUDE.md — Solenhive Website v3.4 · Last updated: October 2026*
