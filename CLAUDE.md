# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview
Single-page marketing website for Forge Performance Co., a premium performance ecosystem brand.
- **Live URL:** https://teamfpco.com
- **Repo:** https://github.com/TeamForgeJordan/teamfpco.github.io
- **Primary file:** `index.html` (all HTML, CSS, and JS in one file — no build tools, no frameworks)
- **Assets:** `assets/` folder for images and logos
- **Hosting:** GitHub Pages — changes go live ~30 seconds after `git push`

## Development

No build step. Open `index.html` directly in a browser, or serve locally:

```bash
python3 -m http.server 8080
# visit http://localhost:8080
```

## Git Workflow

```bash
git add <file>
git commit -m "brief description"
git push
```

## Brand Architecture

Forge Performance Co. is the parent umbrella brand. Each sub-brand has its own identity but draws authority from the Forge name.

```
FORGE PERFORMANCE CO.
├── SoulFuel              — Integrative Health Coaching
├── Forge Intelligence    — AI Ethics & Literacy Consulting
└── Forged Forward        — Podcast (Spotify & YouTube)
```

## Founder
**Jordan** — Marine Corps Veteran · Certified Integrative Health Coach · Technologist · Systems Thinker
Contact: jordan@teamfpco.com | NW Arkansas · Remote Worldwide | Mon–Fri · 06:00–18:00 CST

## Brand Voice & Tone

Direct, confident, grounded in lived experience. Motivational without being hollow. Identity-focused. Never hype.

**Signature lines:**
- "Strength is not found. It is forged."
- "You don't need perfection — you need alignment."
- "Discipline is the most underrated form of self-respect."

| Context | Tone |
|---------|------|
| Website / Sales Pages | Confident, premium, invitation-based |
| Social Media | Personal, grounded, direct — founder voice |
| Podcast | Warm, conversational — trusted mentor |
| AI / B2B Consulting | Expert, authoritative, precise |

## Visual Identity

### Color Palette
- `--black: #080808` / Forge Black `#0F0F0F` — primary background
- `--steel: #1a1a1c` / Steel Gray `#2B2B2E` — section backgrounds, cards
- `--pearl: #f0ede8` — primary text
- `--copper: #b46e3d` — primary accent, CTAs ⭐
- `--ember: #d4895a` — warm highlight, Forged Forward accent
- `--silver: #9ca3af` / Metallic Silver `#C9CED6` — Forge Intelligence accent
- Forged Bronze `#6A4F33`

Always use CSS variables — never hardcode color values.

### Typography
- **Primary:** Montserrat Bold/900 — headers, logo, CTAs
- **Secondary:** Inter Regular/300 — body copy, UI text
- **Accent:** Playfair Display Italic — SoulFuel sub-brand ONLY

| Element | Font | Size | Weight |
|---------|------|------|--------|
| Hero Headline | Montserrat | clamp(48px, 7.5vw, 108px) | 900 |
| Section Header | Montserrat | clamp(48px, 6.5vw, 88px) | 900 |
| Sub-Header | Montserrat | clamp(28px, 3vw, 40px) | 900 |
| Body Copy | Inter | 15–17px | 300 |
| Caption/Label | Inter | 9–13px | 700 |

Font sizes use `clamp()` for fluid scaling — never fixed px for headlines.

### Logo
Hexagon + Copper Flame
- `assets/images/alt_primary_logo_transparent.png` — primary (nav, footer, overlays) ✅
- `assets/images/primary_logo_transparent.png` — alternate

## Sub-Brand Identities

### SoulFuel — Integrative Health Coaching
- **Tagline:** "Align your habits with your identity."
- **Accent:** Aged Copper `#B46E3D` / Ember Glow `#D4895A`
- **Programs:** Foundation (8wk/8 sessions) · Signature (16wk/12 sessions, Most Popular) · Mastery (24wk/16 sessions)
- Pricing discussed on discovery call only — **never displayed on site**

### Forge Intelligence — AI Ethics & Literacy Consulting
- **Tagline:** "AI literacy for the human performance professional."
- **Accent:** Metallic Silver `#C9CED6` anchored with Copper `#B46E3D`
- **Services:** Session · Workshop · Ethics Badge/Micro-Credential · Institutional Retainer
- "Inquire Now" CTA scrolls to #contact — not a booking link (different audience)

### Forged Forward — Podcast
- **Tagline:** "Real conversations. Real growth."
- **Accent:** Ember Glow `#D4895A`
- **Platforms:** Spotify · YouTube
- Topics: Identity & Becoming, Performance & Energy, Veteran Mindset, Habits & Alignment, AI & The Future, Discipline & Freedom

## Site Structure (Single Page)

1. **Hero** — "Strength / Is Not Found. / It Is Forged." — 100svh, content bottom-anchored
2. **Mission** — `#mission` — "You Don't Need Perfection. You Need Alignment."
3. **Ecosystem** — `#ecosystem` — Three cards: SoulFuel / Forge Intelligence / Forged Forward
4. **Founder** — `#founder` — Split layout, headshot left, content right
5. **Contact** — `#contact` — Formspree form + info panel
6. **Footer**

### Overlays (slide up from bottom, Escape closes)
- `#aboutOverlay` — Mission, Vision, North Star Method
- `#overlay-soulfuel` — IHC explainer, Programs, Discovery Call CTA
- `#overlay-intelligence` — Services, Inquiry CTA
- `#overlay-podcast` — About the show, Topics, Guest pitch form
- `#overlay-privacy` / `#overlay-terms`

## Key Integrations
- **Contact form** → Formspree `https://formspree.io/f/mnjgqrnb` → jordan@teamfpco.com
- **Discovery Call / Apply** → MS Bookings `https://outlook.office.com/book/ForgePerformanceCo@teamfpco.com/s/KTdW_Kn33E-D4ct4IgryLw2`
- **Inquire Now** (Forge Intelligence) → scrolls to `#contact`
- **Spotify** → https://open.spotify.com/show/5ft7GNkKRGCrXb3bovPTbC
- **YouTube** → https://www.youtube.com/@forgedforwardpodcast

## Social Links
- Instagram: https://www.instagram.com/forgeperformance.co/
- LinkedIn: https://www.linkedin.com/company/forgeperformanceco
- YouTube: https://www.youtube.com/@forgedforwardpodcast
- Spotify: https://open.spotify.com/show/5ft7GNkKRGCrXb3bovPTbC

## Tech Stack
- **Hosting:** GitHub Pages
- **Domain:** teamfpco.com (Cloudflare DNS)
- **Forms:** Formspree (free tier)
- **Booking:** Microsoft Bookings (M365)
- **Email:** jordan@teamfpco.com (M365)
- **Payments:** Stripe (configured, post-discovery-call only)

## Design Rules — Never Break These
- All changes must feel **premium** — no generic patterns, no stock UI
- Buttons: `btn-fill` (copper bg) for primary CTAs, `btn-outline` for secondary
- Overlays slide up from bottom — maintain this pattern for any new overlays
- **Headings max 2 lines** — tighten copy before increasing font size
- Custom cursor (`.c-dot` / `.c-ring`) hidden on screens ≤1024px — keep it this way
- **No pricing displayed anywhere** — investment discussed on discovery call only
- **Never use "NBHWC" or "board-certified"** — always "Certified Integrative Health Coach"
- Overlay close buttons: bordered, labeled "Close ✕", copper hover
- Scroll-to-top button: fixed bottom-right, appears after 400px scroll

## Responsive Breakpoints
- **1100px** — tablet: grids collapse, eco cards go 2-column
- **768px** — mobile: hamburger nav, single column, full-width buttons
- **480px** — small mobile: everything tightens, topics go single column

## Assets
```
assets/
└── images/
    ├── alt_primary_logo_transparent.png  — primary Forge logo (nav, footer, overlays) ✅
    ├── primary_logo_transparent.png      — alternate Forge logo
    ├── founder-headshot.jpeg             — PENDING upload
    └── logo-forgedforward.png            — Forged Forward podcast logo (pending placement)
```

## North Star Method
The ideological backbone of all Forge content. Five principles:
1. **Direction Before Intensity** — Clarity precedes volume.
2. **Identity Anchors Behavior** — Sustainable performance emerges from who you are.
3. **Alignment Over Optimization** — More is not better. Better is better.
4. **Structure Creates Freedom** — Systems create capacity, not constraint.
5. **Human First, Performance Always** — Performance is earned through respect for the human system.

## Pricing (Internal — Never Display on Site)
Pricing is a brand signal. These numbers exist so Claude understands premium positioning only.

| Offering | Investment |
|----------|------------|
| SoulFuel Foundation | $1,400 |
| SoulFuel Signature | $2,400 |
| SoulFuel Mastery | $3,500 |
| AI Ethics Session | $1,500–$2,500 |
| AI Workshop + Digital Companion | $3,000–$4,500 |
| AI Ethics Badge / Micro-Credential | $500–$1,500/cohort · $97–$197/participant |
| AI Institutional Retainer | $2,000–$5,000/month |

Payment plans available on all SoulFuel programs.

## Pending Items
- [ ] Founder headshot → upload to `assets/images/founder-headshot.jpg`
- [ ] SoulFuel logo → pending redesign
- [ ] Forge Intelligence logo → not yet created
- [ ] Stripe payment links → post-discovery-call
- [ ] Google Analytics → add once traffic grows
- [ ] Email follow-up sequence → post-booking automation (M365)
- [ ] Update Beacons.ai / all social bios → point to teamfpco.com
