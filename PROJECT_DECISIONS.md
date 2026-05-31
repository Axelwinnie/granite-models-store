# Granite Models — Confirmed Project Decisions (locked)

Source: Jon's direction. Keep this current. Applies to the whole multi-page build.
Last updated: 2026-05-31

## Identity / brand
- Founder & owner: **Jon Anderson** (owner of GMA — Granite Models Automations).
  - The mockups' "Jon C. McKee / Jon McKee" is a PLACEHOLDER → replace with Jon Anderson everywhere.
- Brand of the network: **GRANITE**, NOT "Granted". Jon confirmed: "the name is Granite Trade System
  Network. Not granted. It's granite."
  - ALL specs + mockups say "GRANTED TRADES NETWORK" — that is WRONG. Correct to GRANITE everywhere
    (logo art in mockups included).
  - Full name per Jon: "Granite Trade System Network". CONFIRM exact public wording + short form
    (is it still "GTN"?) before it goes on a live page.

## Contact info (public-facing)
- Phone: **NONE.** Do not publish a phone number anywhere. Remove phone fields / "Call Us" blocks, or replace with email + contact form.
- Email: **granitemodels@gmail.com** (matches existing SOCIAL in app.py).
  - Mockups show "info@granitemodels.com" → WRONG, use the gmail address.
- Physical/home address: **NONE.** Remove "123 Contractor Way, Builder, TX 75001" and any street address.
  - General region (New Hampshire) already appears in the footer; that's fine. No exact address.
- Hours / timezone: TX/CT in mockups is placeholder. With no phone, drop "call hours."
  Email response wording (e.g., "within 24 hours") is OK and generic.

## Testimonials
- Real and WILL be used (Jon confirmed). Section stays.
- Placeholder names/quotes in mockups (Mike R., Jason T., Carlos M., etc.) → REPLACE with real,
  attributed quotes + companies before going live. "We'll replace things that don't add up first."

## Opportunities page
- Jon is **NOT offering jobs**. This is not a job board.
- Purpose: advertise the business — trade dashboards, trade tools, and the lead marketplace.
- Reframe the mockup's "featured job listings" away from fabricated job postings.
- Tie to the existing live /leads (lead marketplace) with careful "Marketplace Expansion" wording.
- No guaranteed-work / guaranteed-lead claims.

## Still NEEDED from Jon (before relevant pages go live)
- [ ] Granted vs Granite naming confirmation.
- [ ] Granted Trades Network live URL (placeholder #granted-trades-network for now).
- [ ] Are the dashboard screenshots REAL product captures? (Command Center, trade dashboards.)
- [ ] Resource Center: are the 500+ downloadable templates real/ready now, or "coming soon"?
- [ ] Stats confirmation: "25+ years", "1000+ projects", "hundreds of contractors", etc.
- [ ] Final testimonial quotes + names + companies (with permission).
- [ ] Individual IMAGE ASSET files (separate from the page mockups) — one per slot.
- [ ] Newsletter signup destination (SendGrid list? new DB table?).

## Videos (Jon is sending these now)
- Host: YouTube, Unlisted. Jon sends video IDs/URLs; I embed (privacy-enhanced, rel=0). No download needed.
- The 8 demo slots wanted (matches Demo Videos mockup #5):
  1. Command Center Overview
  2. Project Tracking Demo
  3. Estimating Tools Demo
  4. Document Management Demo
  5. Landscaping Dashboard Demo
  6. Steel Fabrication Dashboard Demo
  7. AI Business Tools Demo
  8. Granted Trades Network Demo
- Any slot without a video stays "Demo coming soon" — page still ships.

## Separate Programs — tracked changes (NOT this website repo)

### Ticket Service Toolbox (formerly "ASF Maintenance Toolbox")
- This is a STANDALONE program on its own registry. It is NOT part of granite-models-store
  and cannot be edited from the website session. These are tracked tasks for that program.
- **RENAME:** "ASF Maintenance Toolbox" → **"Ticket Service Toolbox"**.
  - Promote the new name throughout that program's ENTIRE codebase at a later date.
  - Priority: LOW for now — website comes first. Jon: "It's its own standalone program... not too worried."
- **Top nav bar cleanup (in that program):**
  - Remove **"ASF"** branding (top-left logo text).
  - Remove the user name **"Pete Sirois"** — it sits in the top nav **between the notification bell
    and Logout**. Delete it entirely; no user name needed there.
  - These are the ONLY two changes for the program; it's all in the top nav bar.
- **Website impact:**
  - After the program is updated, RE-RECORD a clean demo for the website.
  - The current `asf-toolbox.webm` (shows ASF + Pete Sirois) is OBSOLETE — do NOT publish.
    Removed from the website repo. The "Ticket Service Toolbox" is a TOOL demo (not a trade) and
    stays "Demo coming soon" until the clean re-record arrives.

## Process (locked)
- All work on dev branch `claude/gallant-einstein-aiOog`. NOTHING pushed/live until full verification.
- Before live: every button/route/link connected and tested; mobile pass; no overclaim; rollback ready.
- Phased build: Home → static marketing pages → forms → Opportunities → Resource Center → global QA → promote.
