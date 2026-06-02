# DEMO PLACEMENT MAP — Trade Dashboard + Tool Demos

Source: `MANIFEST.txt` — 8 zip parts, 22 demos, clean web-ready names (`<name>-demo.webm`).

## Auto-publish on drop (no renaming needed)
The gallery now detects a trade demo by EITHER name:
`videos/dash-<slug>.webm`  **OR**  `videos/<slug>-demo.webm`.
Jon's clean names are `<slug>-demo.webm`, which match the gallery slugs — so:
**just unzip the files into `videos/` and they publish automatically.**

## TRADE DEMOS (drop into videos/, auto-publish)
landscaping-demo · steel-fabrication-demo · hvac-demo · plumbing-demo · construction-demo ·
electrical-demo · painting-demo · excavation-demo · hardscape-demo · irrigation-demo ·
pool-pond-demo · concrete-demo · sealcoat-demo · paving-demo · fencing-demo · logging-demo ·
septic-demo · insulation-demo · mechanic-auto-demo · **line-striping-demo** (new card added)

All filenames already equal `<slug>-demo.webm` → land on the correct card automatically.

## NO demo provided → stay "Coming Soon"
- **Masonry**, **Roofing** (not in the manifest).

## TOOL DEMOS (special handling)
- `ticket-service-toolbox-demo.webm` → **overwrite** the existing redacted file at
  `videos/ticket-service-toolbox-demo.webm` (the NEW interactive version; card already wired).
- `ai-answering-service-demo.webm` → drop into `videos/`; the AI Answering Service card shows a
  "Watch Demo" button automatically (wired conditionally on the file existing).

## ZIP PARTS (per manifest)
PART1: toolbox, paving, ai-answering | PART2: hardscape, irrigation, pool-pond |
PART3: plumbing, insulation, excavation | PART4: construction, line-striping, electrical |
PART5: fencing, logging, concrete | PART6: painting, sealcoat, hvac |
PART7: landscaping, septic, steel-fabrication | PART8: mechanic-auto

## PROCEDURE (when zips uploaded)
1. unzip each PART → copy *.webm into `videos/`.
2. confirm count: 20 trade cards "Demo Available" (+ Masonry/Roofing "Coming Soon");
   toolbox + AI cards show Watch Demo.
3. spot-check 3-4 cards play the correct trade.
4. commit + push.

## STATUS
- [x] Auto-detect supports `<slug>-demo.webm`; Line Striping card added; AI card wired.
- [ ] Awaiting the 8 zip files (only MANIFEST.txt uploaded so far).
