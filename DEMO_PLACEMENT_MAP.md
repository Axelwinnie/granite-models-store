# DEMO PLACEMENT MAP — Trade Dashboard Demos

Source manifest: `DEMO_VIDEOS_MANIFEST.txt` (19 demos, ~1920x1080 WebM, in OneDrive).
Goal: every demo lands on its **exact** trade card on /tools (Dashboards gallery). No mix-ups.

## How publishing works
The gallery auto-detects a demo when a file named **`videos/dash-<slug>.webm`** exists.
So placement = rename each uploaded demo to its target name below, drop it in `videos/`, deploy.

## DETERMINISTIC MAP (manifest prefix → trade → target file)
The rename is driven ONLY by the filename prefix (before `_interactive_demo`). Exact map:

| Manifest prefix | Trade card        | slug             | Target filename                |
|-----------------|-------------------|------------------|--------------------------------|
| concrete        | Concrete          | concrete         | dash-concrete.webm             |
| construction    | Construction      | construction     | dash-construction.webm         |
| electrical      | Electrical        | electrical       | dash-electrical.webm           |
| excavation      | Excavation        | excavation       | dash-excavation.webm           |
| fencing         | Fencing           | fencing          | dash-fencing.webm              |
| hardscape       | Hardscape         | hardscape        | dash-hardscape.webm            |
| hvac            | HVAC              | hvac             | dash-hvac.webm                 |
| insulation      | Insulation        | insulation       | dash-insulation.webm           |
| irrigation      | Irrigation        | irrigation       | dash-irrigation.webm           |
| **landscape**   | Landscaping       | landscaping      | dash-landscaping.webm          |
| logging         | Logging           | logging          | dash-logging.webm              |
| **mechanic**    | Mechanic / Auto   | mechanic-auto    | dash-mechanic-auto.webm        |
| painting        | Painting          | painting         | dash-painting.webm             |
| paving          | Paving            | paving           | dash-paving.webm               |
| plumbing        | Plumbing          | plumbing         | dash-plumbing.webm             |
| **pool**        | Pool & Pond       | pool-pond        | dash-pool-pond.webm            |
| sealcoat        | Sealcoat          | sealcoat         | dash-sealcoat.webm             |
| septic          | Septic            | septic           | dash-septic.webm               |
| **steel**       | Steel Fabrication | steel-fabrication| dash-steel-fabrication.webm    |

**Watch the 5 renames in bold** — the prefix differs from the slug:
landscape→landscaping, mechanic→mechanic-auto, pool→pool-pond, steel→steel-fabrication.

## Trades with NO demo yet (stay "Demo Coming Soon")
- **Masonry** (no manifest video)
- **Roofing** (no manifest video)

## Deterministic rename logic (run when videos are uploaded)
```python
PREFIX_TO_SLUG = {
  'concrete':'concrete','construction':'construction','electrical':'electrical',
  'excavation':'excavation','fencing':'fencing','hardscape':'hardscape','hvac':'hvac',
  'insulation':'insulation','irrigation':'irrigation','landscape':'landscaping',
  'logging':'logging','mechanic':'mechanic-auto','painting':'painting','paving':'paving',
  'plumbing':'plumbing','pool':'pool-pond','sealcoat':'sealcoat','septic':'septic',
  'steel':'steel-fabrication',
}
# for each uploaded *.webm:
#   prefix = name.split('_interactive_demo')[0].lower()
#   slug   = PREFIX_TO_SLUG[prefix]
#   copy -> videos/dash-<slug>.webm
```

## Verification after placement (mandatory — no mix-ups)
For EACH of the 19: open /tools, click that trade's card, confirm the video that plays is the
correct trade (landscaping shows lawn jobs, HVAC shows furnace jobs, steel shows fab, etc.).
Cross-check count: 19 cards "Demo Available", Masonry + Roofing still "Coming Soon".

## STATUS
- [x] Gallery + auto-detect built; Mechanic/Auto card added.
- [ ] Awaiting the 19 .webm files (only the manifest .txt was uploaded so far).
- [ ] On upload: rename per map → verify each → deploy.
