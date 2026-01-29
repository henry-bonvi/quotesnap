# QuoteSnap — AI-Powered Quoting for Tradies

## Purpose
Turn job photos into professional quotes in 60 seconds. Built for Australian tradies who waste hours every night typing up quotes.

## Research Context
**Pain Points Discovered:**
- Tradies spend 2-3 hours/day creating quotes manually
- Slow quoting = lost jobs (first to quote wins ~60% of the time)
- Most tradies undercharge because they don't know market rates
- Existing tools (Tradify, ServiceM8) are full suites at $30-50+/mo — overkill for just quoting

**Sources:**
- Reddit r/smallbusiness — pricing/quoting pain points (295+ upvotes on pricing objection post)
- Reddit r/SaaS — construction PM SaaS at $28k MRR validates trades vertical
- Reddit r/sweatystartup — cleaning companies, trade startups struggling with efficiency
- IndieHackers — "services before SaaS" pattern, micro-SaaS validation stories

**User Quotes:**
- "I spend 2 hours every night on quotes"
- "I lose jobs because I'm too slow"
- "Am I even charging the right price?"

## Tech Stack
- Static HTML + Tailwind CSS (CDN)
- Vanilla JavaScript (rate calculator)
- Netlify hosting + forms
- Plausible analytics

## Free Tool
**Tradie Rate Calculator** — tradies select their trade, location, and experience to see where their hourly rate falls vs market average. Includes tips to charge more.

## Links
- Landing page: https://quotesnap.netlify.app (pending deployment)
- Related: YardPilot (home services CRM)

## Status
- [x] Market research
- [x] Landing page with waitlist
- [x] Free tool (Rate Calculator)
- [x] Plausible analytics
- [ ] Deploy to Netlify
- [ ] Reddit promo posts
- [ ] Facebook group promo

## How It Would Work (Architecture)

The landing page sells "photo → quote in 60 seconds". Here's the realistic internal pipeline:

### Pipeline: Photo → Quote

**Step 1: Job Recognition (Vision AI)**
- User snaps a photo + optional voice note or text description
- GPT-4o Vision (or Claude) analyses the image
- Extracts: job type, scope indicators (size of area, number of fixtures, condition), materials visible
- Voice note transcribed and merged as context
- Weakest link — vision AI is good at "that's a bathroom needing retiling" but not "that's exactly 12sqm". Hence Step 2.

**Step 2: Guided Scope Refinement**
- AI presents its best guess, user confirms/adjusts via quick form
- Smart follow-up questions based on job type: "Roughly how many sqm?" / "Standard or premium materials?" / "Demolition needed?"
- 3-5 taps max. This is where accuracy goes from 60% → 90%+
- Photo gives a head start so user isn't starting from scratch

**Step 3: Pricing Engine (Core IP)**
- Materials database: scraped/maintained from Bunnings, Reece, Beacon Lighting etc. Updated monthly. Per-category averages (e.g. "standard wall tiles = $35-55/sqm installed")
- Labour rates: same data as Rate Calculator — trade, location, experience
- Job templates: pre-built formulas per job type. E.g. "Bathroom retile = (area × tile cost) + (area × labour rate × hours/sqm) + (demolition flat fee) + (waterproofing)"
- Start with 20-30 common templates per trade, expand from usage data
- User's own rates override defaults

**Step 4: Quote Generation**
- Assemble: line items, materials, labour, subtotal, GST, total
- Apply user's branding (logo, ABN, terms, contact)
- Generate PDF server-side (Laravel + DomPDF or Browsershot)
- Preview in-app before sending

**Step 5: Delivery**
- One tap: SMS or email to customer
- Customer gets clean link or PDF attachment
- Track: opened, viewed, accepted/declined

### What Makes This Reliable vs Gimmicky

Photo alone can't deliver accurate quotes. The trick:
1. **Photo = head start, not the whole answer.** Pre-fills 60-70%, guided refinement gets to 90%+
2. **Job templates are the backbone.** AI doesn't guess pricing — maps job to a template with real cost formulas
3. **User's own rates ground it.** We calculate materials + their rate × estimated hours
4. **"60 seconds" works** because photo skips the blank page problem. Even with 3-5 refinement taps, way faster than typing from scratch

### Biggest Risks
- **Material prices going stale** — need automated scraping or API partnerships
- **Job template coverage** — weird jobs need graceful fallback ("custom quote builder")
- **Photo quality** — dark/blurry site photos need more guided questions

### MVP Scope (v1)
- 3 trades first (plumber, electrician, landscaper)
- 10 job templates per trade
- Manual material price database (monthly updates)
- Basic branded PDF
- SMS delivery via Twilio

## Status
**Parked** — landing page + waitlist live, architecture specced. May revisit later. Focus is on YardPilot + ReplyMate + LeadScouts.

## Product Ladder
Standalone SaaS for now. Potential future integration with YardPilot as a quoting module for home services businesses.
