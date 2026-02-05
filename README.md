# QuoteSnap ⚡

**Turn job photos into professional quotes in 60 seconds.**

Built for Australian tradies who waste hours every night typing up quotes in Word or Excel.

## The Problem

Based on Reddit research (Feb 2026):
- Tradies spend 1-2 hours/night creating quotes manually
- Slow quotes = lost jobs (customers hire whoever responds fastest)
- Existing solutions (ServiceM8, Tradify, etc.) are full job management systems - overkill for just quoting
- Many tradies use Word/Excel templates that look unprofessional

## The Solution

QuoteSnap is a dead-simple mobile quoting app:
1. 📸 Snap photos of the job on-site
2. ⚡ Add line items from your saved services/materials
3. 📄 Generate professional branded PDF
4. 📧 Send via email/SMS before leaving the driveway

## Landing Page

This repo contains the landing page with:
- Value proposition
- Pain points
- Free tool: **Tradie Rate Calculator** (calculates break-even hourly rate)
- Waitlist signup

## Free Tool Hook

The "Tradie Rate Calculator" helps tradies figure out their minimum hourly rate based on:
- Weekly expenses (fuel, tools, insurance, rego, ute payments)
- Target weekly income
- Billable hours per week
- Desired profit margin

This provides immediate value and captures emails.

## Tech Stack

- Static HTML/CSS/JS
- Plausible Analytics
- Netlify hosting

## Deployment

```bash
# Install Netlify CLI if needed
npm install -g netlify-cli

# Deploy
netlify deploy --prod
```

## Validation Plan

1. Deploy landing page with calculator
2. Post in Australian tradie Facebook groups
3. Post in r/AusElectricians, r/AustralianMakers
4. Measure: calculator usage, waitlist signups
5. If >50 signups in first week, build MVP

## Links

- **Live site:** https://quotesnap.netlify.app (pending)
- **Research source:** Reddit r/smallbusiness, r/AusElectricians

---

Part of the [Original Solutions](https://originalsolutions.au) product ladder.
