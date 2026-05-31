# Go-Live Deployment Plan — Granite Models Trades OS Homepage

**Target:** granitemodels.store (production) · **Host:** Render · **Deploy trigger:** Jon, manual
**Prepared:** 2026-05-31 · **Risk tolerance:** low traffic, but treat as a real production change.

---

## 0. Current state
- Work = 10 commits on branch `claude/gallant-einstein-aiOog`, currently LOCAL-ONLY in an ephemeral
  build container. Live site runs from `main` on Render.
- Render serves the Flask app via `Procfile` (`gunicorn app:app`). Render serves `/videos` and
  `/static` straight through Flask — no serverless size limits (the 5.4 MB steel video is fine).
- `vercel.json` / `.vercelignore` are in the repo but **Render ignores them** (preview-only, harmless).

## 1. The one real blocker (must resolve first)
This build environment is network-locked: **no `git push` (403), no Vercel, no open internet.**
The binary video files cannot leave this container through available channels.

**Resolution (pick one):**
- **A — RECOMMENDED:** Re-open this repo in a Claude environment with a normal network policy.
  Then Claude pushes the full branch (code + videos) to GitHub and the rest of this plan runs cleanly.
- **B:** Jon deploys from his own machine. Code goes to GitHub (text is pushable via the GitHub
  integration); Jon supplies the 4 trade videos (renamed copies of his own uploads) and the redacted
  toolbox video (delivered to Jon directly), then pushes.

> Until the work reaches GitHub `main`, **nothing can go live.** This is step 1, not an afterthought.

## 2. Promotion path (professional, reviewable)
1. Push branch `claude/gallant-einstein-aiOog` to GitHub (code + all 5 videos).
2. Open a Pull Request: `claude/gallant-einstein-aiOog` → `main`.
3. Review the PR diff (sanity-check the rendered changes, file list, no stray files).
4. Run the **Pre-flight checklist** (section 3). All must pass.
5. Merge the PR into `main`.
6. **Jon manually deploys on Render:** Render dashboard → the granite-models service →
   **Manual Deploy → "Deploy latest commit"**. Watch the build logs to green.
7. Run the **Post-deploy verification** (section 4) against the live site.

## 3. Pre-flight checklist (verified green in staging 2026-05-31)
- [x] Homepage renders; all internal routes 200 (`/ /contact /leads /pricing /privacy /terms`).
- [x] All 5 demo videos serve (200): hardscape, asphalt/sealcoat, steel-fab dashboard,
      steel shape library, redacted Ticket Service Toolbox.
- [x] All nav/CTA anchors resolve (#trades, #demo-videos, #granite-trades-network, #build-with-us).
- [x] No bad strings: no "McKee", "Granted", "ASF/Sirois", "info@granitemodels.com",
      "123 Contractor Way", "guaranteed leads".
- [x] Public info: email granitemodels@gmail.com; NO phone, NO address published.
- [x] Founder = Jon Anderson; network = Granite Trades Network (GTN).
- [x] Lead emails → granitemodels@gmail.com only (Lorie removed).
- [ ] **Render env vars set (Jon to confirm):** `SENDGRID_API_KEY`, OpenRouter chat key,
      `FLASK_SECRET_KEY`. If missing, forms/chat fail quietly; site still works.
- [ ] **SendGrid sender verified:** `support@granitemodels.store` must be a verified sender.

## 4. Post-deploy verification (on live granitemodels.store)
- Homepage loads; hero, 20 trades, command center, steel spotlight, GTN, opportunities, demo library.
- Play one video (e.g., steel dashboard) — confirms /videos serving on prod.
- Trade demo modals open (Hardscape, Asphalt) and play.
- Submit a test "Build With Us" entry → confirmation shows; confirm email arrives at granitemodels@gmail.com.
- Nav links + footer links work; /leads (Stripe), /pricing, /contact load.
- Check Render logs for errors.

## 5. Rollback (one click)
- Render keeps prior deploys: **Render dashboard → Deploys → previous good deploy → "Redeploy".**
- Or revert the merge commit on `main` and redeploy.
- Pre-change baseline commit on main: `0b2571b` (the homepage before this work).

## 6. Known, accepted-for-now items (fix after launch)
- `/contact`, `/leads`, `/pricing` keep OLD copy/theme (22 trades, 30 years, lead-gen wording) and
  will get proper backgrounds + alignment to the new positioning in a follow-up pass.
- Site-wide `<meta description>` in base.html still says "22 trade dashboards / 30-year" — update later.
- Number consistency (20 vs 22 trades, 25 vs 30 years) — reconcile in the follow-up pass.
- Scope ID demo + real image assets for the 8 placeholder slots — add when ready.

## 7. What does NOT change in this deploy
- No changes to the Stripe/leads checkout logic, pricing logic, or the live /leads functionality
  beyond the reworded hero.
- No database migrations. (Feedback SQLite table self-creates on first submission.)
- No DNS/Cloudflare/domain changes.
