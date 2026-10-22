# Solenhive Website — Claude Code Instructions

## Project overview
Single-page marketing site for Solenhive: paid media strategy plus the marketing software behind it, sold to agencies and multi-location brands, white-label ready. Operated by Marc Carlton LLC. Static HTML/CSS/JS on Vercel.

## Tech stack
- Pure HTML, CSS, JavaScript — no frameworks, no build tools
- Pages: `index.html`, `privacy-policy.html`, `terms-of-service.html`
- Assets: `images/solenhive-logo-dark.png` (header logo), `favicon-32.png`, `favicon-192.png`, `apple-touch-icon.png`, `images/marc-carlton.{webp,jpg}` (founder photo, 720×900, 4:5)
- Fonts: Google Fonts (see Typography)
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
│   ├── solenhive-logo-dark.png
│   ├── marc-carlton.webp
│   └── marc-carlton.jpg
├── solenhive-logo.svg      ← old file with live Gill Sans text; not used on the site; never modify
├── solenhive-brand-guide.md
└── CLAUDE.md               ← this file
```

---

## Positioning and copy rules — never violate these

- **Never name products on the public site.** Describe capabilities only (tag & pixel compliance, client reporting, paid media analytics, retainers & billing). Products get white-labeled by partners, so names stay off the site, the legal pages, and meta tags.
- Headline: "We run the media. We build the tools." Audience: agencies and multi-location brands.
- Mark a module `LIVE` only if it runs in production today; otherwise `IN BUILD`. Never list planning-stage ideas.
- **No employer references** anywhere in this repo (no current employer, no automaker brand names). The founder bio stays as written unless Marc changes it.
- No client names, logos, screenshots, or results without the client's written sign-off.
- Scan report data must stay anonymized: no site URLs, no site-platform vendor names, no automaker or industry-specific terms ("dealer", "OEM").
- Severity uses color plus a text label (Error / Warn / OK / None), never color alone.
- No invented stats, prices, or testimonials. If a fact is missing, leave the element out — never ship a `[PLACEHOLDER]`.
- Headlines 6 words max. Plain English, outcomes first. Never use: "leverage", "synergy", "disrupt", "innovative", "cutting-edge".

---

## Brand rules

### Colors
```
--navy:       #0d1b2e   ← primary background
--navy-mid:   #132238   ← alternate section / card background
--navy-light: #1e3a5f   ← borders, logo circle on dark
--gold:       #e8c44a   ← accents, CTAs, LIVE status
--white:      #ffffff   ← primary text
--text-muted: #8fa3bb   ← secondary text (passes 4.5:1 on both navies)
--alert:      #ff8a7a   ← ERROR severity in scan report UI only (7:1 on navy)
```
`#5a6a7e` (old text-dim) fails contrast for small text — do not use it for text.

### Typography (per the brand standard)
- Display / headings / labels / buttons / nav: **Barlow Condensed** (300 hero, 400 h2, 500 h3 and labels)
- Body: **Work Sans** 300
- Data, status tags, email, scan output: **DM Mono**
- Logo wordmark: never typeset. The logo is always the master artwork (see Logo).
- Never use weight 600 or 700. All-caps only for labels, nav, buttons, with letter-spacing ≥ 3px.

### Logo
- The header logo is `images/solenhive-logo-dark.png`: Marc's 3000px master PNG with colors swapped for dark backgrounds (navy letters → white, mark circle → `#1e3a5f`, gold unchanged). Letterforms and mark geometry are the master's, untouched. Shown at 36px tall; same `<img>` on all three pages.
- Header uses the wordmark + mark lockup without the tagline (the tagline is unreadable at header size); the brand standard allows this for app headers.
- Favicons are cropped from the same master mark.
- Never retype the wordmark in a font, redraw the mark, or recolor the logo with CSS filters. To regenerate, recolor the master PNG.

---

## Home page sections (in order)
1. **Header** — sticky, logo left, nav right (Platform · Services · About · Contact · "Book an audit"); hamburger below 900px
2. **Hero** — headline, sub, two CTAs, scan-result panel (excerpt of the report below, links to `#scan`)
3. **Proof strip** — "Running in production", three true statements
4. **Platform** — four capability cards with LIVE / IN BUILD status, then the white-label band
5. **Inside a scan** (`#scan`) — real report from one live scan, rebuilt in HTML: stats, ad platform coverage, findings. Site identity, vendor names, and industry terms removed. Hero panel numbers must match it.
6. **Services** — Digital audit (featured, fixed scope), Fractional media leadership, Measurement setup
7. **About** — founder photo + bio + skill chips
8. **Contact** — copy + email link, and a form that composes an email to hello@solenhive.com (no backend yet)
9. **Footer** — legal line left, links right

Any element with `data-interest="…"` pre-selects that option in the contact form when clicked.

### Footer legal line (all pages, identical)
`&copy; <year> Marc Carlton LLC. Solenhive is operated by Marc Carlton LLC.` — update the year each January.

### Legal pages
- Operator is defined as "Marc Carlton LLC, doing business as Solenhive". Bump the page's effective date whenever its content (not just styling) changes.

---

## Design rules
- Dark-first: navy backgrounds only, never white or light
- Borders for depth — no drop shadows, no gradients on text
- Sharp corners on buttons, inputs, and cards
- Max content width 1200px; side gutter `clamp(20px, 4vw, 60px)`
- Section padding `clamp(72px, 9vw, 120px)`
- Touch targets ≥ 44px; text contrast ≥ 4.5:1
- Must work at 390px width with no horizontal scroll

---

## Tracking
- Amazon Ad Tag in `index.html` `<head>`: PageView on load, `Contact` event on email-link click and form submit.
- No GA4 yet. When adding it, add consent handling and update the Privacy Policy's tracking section in the same change.

---

## Deployment
- Push to `master` (Vercel production branch); Vercel auto-deploys every push
- No build step — static files deploy as-is
- Custom domain: `solenhive.com`

---

## Autonomy
- Run routine edits, searches, and reads without asking
- Interrupt only for destructive or irreversible actions, or work outside the request

---

## Do not
- Do not add npm, package.json, or build tooling
- Do not add CSS or JS frameworks
- Do not name products, clients, or employers (see Positioning)
- Do not use light backgrounds
- Do not ship placeholder text or placeholder images

---

*CLAUDE.md — Solenhive Website v2.0 · Last updated: October 2026*
