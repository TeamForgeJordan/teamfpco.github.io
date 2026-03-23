cd /path/to/forge-com
cat > CLAUDE.md << 'EOF'
# Forge Performance Co. — CRM Project

## Brand
- Company: Forge Performance Co. (teamfpco.com)
- Founder: Jordan, Marine Corps veteran, NBHWC certified
- Sub-brands: Forge Intelligence (AI ethics consulting), SoulFuel (integrative
  health coaching), Forged Forward (podcast)
- Voice: direct, military precision, no fluff

## Design system
- Background: #0F0F0F (Forge Black)
- Accent: #B46E3D (Aged Copper)
- Warm highlight: #D4895A (Ember Glow)
- Surface: #2B2B2E (Steel Gray)
- Surface 2: #3E454C (Smoke Slate)
- Text primary: #F4F4F4 (Iron Pearl)
- Text secondary: #C9CED6 (Metallic Silver)
- Border: #2B2B2E
- Fonts: Montserrat Bold/SemiBold (headings), Inter Regular/Medium (body)
- Border radius: 6px

## Tech stack
- API: Cloudflare Workers + D1 (TypeScript, Hono router)
- Dashboard: React + Vite → Cloudflare Pages
- Auth: Custom JWT session (30-day), login at admin.teamfpco.com/login
  - Sign out in nav, password reset via Resend to jordan@teamfpco.com
  - Cloudflare Access has been removed — custom auth only
- Email: Resend (verified on teamfpco.com domain)
- Automation: Make.com (not yet connected — holding until clear use case)
- Deployment: GitHub Actions (auto-deploy on push to main)

## Live URLs
- Dashboard: https://admin.teamfpco.com (custom JWT auth, login at /login)
- API: https://api.teamfpco.com
- Website: https://teamfpco.com (GitHub Pages, separate repo: teamfpco.github.io)

## GitHub
- Repo: TeamForgeJordan/forge-com (private)
- Auto-deploy: .github/workflows/deploy-dashboard.yml and deploy-api.yml
- Push to main triggers automatic build and deploy for both API and dashboard

## Cloudflare services in use
- Workers: forge-crm-api
- Pages: forge-crm-dashboard
- D1: forge-crm (production database)
- DNS: teamfpco.com zone
- Note: Cloudflare Zero Trust Access was removed — replaced by custom JWT auth

## Secrets (set via Wrangler, never commit)
- JWT_SECRET: Cloudflare Worker secret
- WEBHOOK_SECRET: inbound webhook validation
- MAKE_WEBHOOK_NEW_CONTACT: placeholder, needs real Make.com URL
- MAKE_WEBHOOK_STAGE_CHANGE: placeholder, needs real Make.com URL
- RESEND_API_KEY: live key, verified on teamfpco.com domain
- VITE_API_TOKEN: set in Cloudflare Pages environment variables + GitHub secrets

## Database
- D1 SQLite, 3 tables: contacts, interactions, bookings
- Schema: api/src/db/schema.sql
- Production DB initialized and live
- Local dev: npm run db:init:local in api/

## What is built and working
- Full CRM API with contacts, interactions, bookings endpoints
- JWT auth on all API routes (custom 30-day session), dev bypass for local dev
- Service account auth (scope: contacts:write, key prefix fpco_) for external intake
- Dashboard with 4 pages: Dashboard home, Contacts, Pipeline, Bookings
- Dashboard home: KPI cards, pipeline summary, recent activity feed
- Contacts: sortable table, search, filter by sub-brand and stage
- Contact detail: slide-in panel, inline edit, interaction log
- Pipeline: kanban board by stage
- Bookings: table view
- Add Contact modal with full form
- Web Leads dashboard view
- Make.com outbound webhook triggers on new contact and stage change (wired,
  but Make.com scenarios not yet created)
- Responsive layout (desktop, tablet, mobile)
- GitHub Actions auto-deploy pipeline
- Resend auto-reply email on contact form submission
- /form-submissions endpoint (replaces Formspree on teamfpco.com)
- Contact form on teamfpco.com updated to POST to CRM API

## Contact form & lead intake
- Website contact form POSTs to https://api.teamfpco.com/form-submissions
- Formspree has been fully replaced
- Auto-reply sent via Resend on submission
- Submissions appear in Web Leads dashboard view

## Booking strategy
- Discovery call booking link is NOT public on the website
- Booking link is sent privately via Resend auto-reply after contact form submission
- Rationale: qualifies leads before calendar access, fits high-touch positioning
  of Forge Intelligence, avoids noise while brand is building
- book.teamfpco.com is the planned booking subdomain (not yet built)
- Next task: add booking link to Resend auto-reply email template

## What still needs to be built
1. Add booking link to Resend auto-reply email (first priority next session)
2. Wire Make.com scenarios — create actual scenarios for new contact and stage
   change webhooks, update MAKE_WEBHOOK_NEW_CONTACT and
   MAKE_WEBHOOK_STAGE_CHANGE secrets with real URLs
3. Build book.teamfpco.com — booking page in same brand system
4. Consider Microsoft OAuth for dashboard auth long term
5. React Native mobile app for CRM (planned — see Mobile App section below)

## Mobile App (planned)
- Stack: Expo + React Native (iOS + Android from single codebase)
- Auth: connects to existing JWT system at api.teamfpco.com
- Goal: native contacts view, lead management, push notifications for
  new form submissions
- IDE: Google Antigravity (agent-first IDE) + Claude Code extension
- Start in Antigravity Playground before touching production CRM repo

## Dev environment
- Primary IDE: Google Antigravity (agent-first, VS Code fork)
  - Claude Code extension installed inside Antigravity
  - Workflow: Antigravity/Gemini for planning → Claude Code for implementation
  - Use Review-driven development mode (agent asks before acting)
- Claude Code picks up this CLAUDE.md automatically on session start

## Dev commands
- API dev server: `cd api && npm run dev`
- Dashboard dev server: `cd dashboard && npm run dev`
- DB init local: `cd api && npm run db:init:local`
- Type check API: `cd api && npx tsc --noEmit`
- Deploy: push to main — GitHub Actions auto-deploys both API and dashboard

## Git workflow
```bash
git add <file>
git commit -m "brief description"
git push
```

## Rules
- Parameterized SQL only — never concatenate user input into queries
- All secrets via Wrangler env vars or GitHub secrets — never hardcode
- Always rebuild dashboard from GitHub push — never manual wrangler deploy
- Match brand exactly — no default blue buttons, no white backgrounds
- Keep bundle small — no heavy UI libraries
- Never expose booking link publicly on the website — email-gate only
EOF
git add CLAUDE.md
git commit -m "update CLAUDE.md with CRM completion, auth system, booking strategy, Antigravity setup"
git push