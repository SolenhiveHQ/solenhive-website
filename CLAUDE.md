# Solenhive Website — Claude Code Instructions

## Project overview
Single-page marketing website for Solenhive, a Florida-based marketing strategy and digital ventures firm. Built in HTML/CSS/JS. Deployed on Vercel via GitHub.

## Tech stack
- Pure HTML, CSS, JavaScript — no frameworks, no build tools
- Single file: `index.html`
- Logo: `solenhive-logo.svg`
- Deployed via Vercel (auto-deploys on push to `main`)

## File structure
```
solenhive-website/
├── index.html
├── solenhive-logo.svg
├── CLAUDE.md               ← this file
└── README.md
```

---

## Brand rules — never violate these

### Colors
```
--navy:       #0d1b2e   ← primary background
--navy-mid:   #132238   ← card / section backgrounds
--navy-light: #1e3a5f   ← borders, subtle surfaces
--gold:       #e8c44a   ← accents, CTAs, highlights
--white:      #ffffff   ← primary text on dark
--text-muted: #8fa3bb   ← secondary text
--text-dim:   #5a6a7e   ← tertiary text, tagline
```

### Typography
- Font stack: `'Gill Sans', 'Gill Sans MT', 'Trebuchet MS', Calibri, sans-serif`
- Weight: always 300 (light) for headlines and body. 400 for UI labels only
- Never use font-weight 600 or 700
- Letter-spacing on all-caps: minimum 2px
- All-caps only for: nav links, section labels, buttons, tagline

### Logo
- The SVG logo file must never be modified
- On dark/navy backgrounds: use the inverted version (gold circle, dark comb)
- On light backgrounds: use the standard version (navy circle, gold comb)
- Always include the tagline "STRATEGY BUILT TO SCALE" beneath when space allows

---

## Page sections (in order)
1. **Nav** — fixed, frosted glass blur, logo left, links center, CTA right
2. **Hero** — full viewport height, eyebrow + headline + subtext + two CTAs
3. **About** — two-column: copy left, stat cards right
4. **Services** — three-column card grid (Marketing Strategy, SaaS Development, Digital Consulting)
5. **Products** — five product cards (Dealer Quant, Fliptify, Digital Listening Post, Freedom Forge, Locosol)
6. **Consulting** — two-column: intro + pull quote left, service list right
7. **Contact** — centered, email link, location
8. **Footer** — copyright left, nav links right

---

## Products reference
| Product | Category | Status |
|---|---|---|
| Dealer Quant | Automotive analytics SaaS | In development |
| Fliptify | Real estate flip analysis SaaS | In development |
| Digital Listening Post | Social media intelligence SaaS | Planning |
| Freedom Forge | Personal financial planning | Planning |
| Locosol | Location intelligence | In development |

All products are described as "A Solenhive product" in any sub-branding context.

---

## Design rules
- Background is always navy (`#0d1b2e`) — never white or light
- Cards use `#132238` background with `#1e3a5f` borders
- Gold (`#e8c44a`) is used sparingly — CTAs, labels, accents only
- No gradients on text
- No drop shadows — use borders for depth
- No rounded corners on buttons — sharp edges only
- Section padding: 120px top/bottom on desktop, 80px on mobile
- Max content width: 1100px centered
- Horizontal padding: 60px desktop, 28px mobile

---

## Responsive breakpoints
- Desktop: 900px+
- Mobile: below 900px
  - Hide nav links (hamburger menu or simplify)
  - Stack all grids to single column
  - Reduce section padding to 80px

---

## What to do when asked to make changes

### Adding a new section
- Follow the existing pattern: section label (gold, all-caps) → headline → rule → content
- Add the section to the nav links
- Add a smooth scroll anchor (`id` on the section)

### Updating copy
- Keep headlines short — 6 words max
- Body copy: plain English, no jargon, outcomes-first
- Never use: "leverage", "synergy", "disrupt", "innovative", "cutting-edge"

### Adding a new product card
- Use the existing `.product-card` class
- Always include: tag (category), name, description, status badge
- Status options: "In development" / "Planning" / "Live" / "Coming soon"

### Changing colors
- Only use colors from the brand palette above
- Never introduce new colors without noting them in this file

---

## Contact details to update before launch
- Email: replace `hello@solenhive.com` with real email address
- Year: update `&copy; 2024` in footer to current year
- Domain: once live, update any hardcoded URLs

---

## Deployment
- Push to `main` branch on GitHub
- Vercel auto-deploys on every push
- No build step needed — static HTML, deploys instantly
- Custom domain: `solenhive.com` (connect via Vercel dashboard → Settings → Domains)

---

## Autonomy
- Run all tool calls and actions without asking for confirmation unless interruption is truly necessary (e.g., a destructive or irreversible action is about to affect shared infrastructure, remote systems, or data that cannot be recovered)
- Do not pause to confirm routine file edits, searches, or reads — execute them directly
- Only interrupt the user when the action is outside the scope of the current request or carries meaningful risk of data loss or unintended side effects

---

## Do not
- Do not add npm, package.json, or any build tooling
- Do not split into multiple files unless explicitly asked
- Do not add external CSS frameworks (Bootstrap, Tailwind, etc.)
- Do not add JavaScript frameworks (React, Vue, etc.)
- Do not change the font stack
- Do not use light backgrounds — this is a dark-first site
- Do not add placeholder images — use SVG shapes or CSS only

---

*CLAUDE.md — Solenhive Website v1.0*
*Last updated: 2024*
