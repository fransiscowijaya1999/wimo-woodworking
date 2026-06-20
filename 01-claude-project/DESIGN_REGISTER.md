# Design Register — Fast Iteration Index

**Purpose of this file.** A one-card-per-design index so a new idea can be slotted into
the right design and improved *without* re-reading every document. Each card captures the
**intent, rationale, hard constraints, known gotchas, and status** — the context the
spec's type-organized tables don't hold — plus a pointer to where the authoritative
numbers live.

**How to use it (sync discipline — read before editing).**
- `DESIGN_SPECIFICATIONS.md` is the **single source of truth for all numbers**
  (dimensions, materials, loads, hardware). Cards quote at most a one-line identifier and
  otherwise point to the spec. If a card and the spec ever disagree, the **spec wins** and
  the card is the bug — fix it.
- **Open questions live only in `DESIGN_SPECIFICATIONS.md` §15** (the master list). Cards
  point there; they don't restate them.
- When a design **decision** changes: update the spec (and `REFERENCE_DATA.md` §10 if a
  constant moved) **first**, then refresh this card's rationale / status.
- "⚠️ Watch for" lines link to catalogued mistakes in `REFERENCE_DATA.md` §4 ("Common
  Errors To Avoid"). Re-check those before touching the related design.
- New design? Add a card here at the same time you add its spec section.

**Status legend:** `idea` → `designed` → `ready to build` → `in build` → `built`.

---

## D1 — Main modular parts shelf (the core system)
- **Intent:** Primary storage backbone — 3 bays of bolt-adjustable timber shelving that
  everything else mounts into.
- **Status:** `in build` (structure designed; drawer carpentry in progress).
- **Spec:** §1–9, §11 · diagrams: front/side/top elevations, dado + T-plate details.
- **Identifier:** 3 bays, ~256 cm wide × 200 cm tall, Meranti columns on the M8 @ 10 cm
  hole grid.
- **Why it's shaped this way / hard constraints:**
  - **Modularity is sacred:** M8 bolt-and-nut, 10 cm vertical pitch, fully reversible. Any
    shelf / drawer / adapter must land on this hole pattern.
  - **Holes on the 6 cm face** (leaves safe margin each side), never the 4 cm face.
    ⚠️ §4 Error 1 (face-orientation mix-up).
  - **Beams are continuously supported** (top wall-anchored, bottom floor-nailed, full
    length) → they distribute load, they don't span. ⚠️ §4 Error 4.
  - **Floor nails go upward from below** — gravity assists, withdrawal is a non-issue.
    ⚠️ §4 Error 3.
  - Meranti Putih is soft → bolt-hole creep; **always spec fender washers**.
  - Vertical compression at the column feet is ~25× under limit — not a concern.
- **Open questions:** see §15 (section-assignment layout, bracket count, wall-anchor
  hardware, Meranti treatment).

## D2 — Standard drawer (light–medium load)
- **Intent:** General-purpose drawer that bolts into a shelf bay.
- **Status:** `in build`.
- **Spec:** §10.
- **Identifier:** 80 cm clear × 50 cm deep, mounts on the 4-corner M8 pattern.
- **Why / hard constraints:**
  - Must match D1's column hole pattern.
  - Slides rated 20–25 kg; **use 70 % of rating** (`SAFETY_FACTOR_SLIDER`).
  - **Weigh the loaded drawer before install**, compare to rating × 0.7, redistribute if
    over; mark filled weight on the drawer.
  - Adapter by weight: **wood plank** for light, **iron flat bar** for heavy.
- **Open questions:** see §15 (slider weight-rating purchasing plan).

## D3 — Rolling sprocket unit (ground-level pull-out)
- **Intent:** Floor-level, top-down-access cart for the heaviest items (sprockets).
- **Status:** `designed`.
- **Spec:** §13 · rolling-sprocket-unit summary diagram.
- **Identifier:** ground-level cart, width = column gap − 2 cm, sprockets stand on edge.
- **Why / hard constraints:**
  - **All casters fixed, no swivel** — it travels one straight line in/out; the columns
    are its side guides. ⚠️ §4 Error 5 (swivel-wheel suggestion).
  - Stop = friction strip + rear rubber bumper; optional slight inward floor incline.
  - Solid bottom + top cover when closed (dust).
- **Open questions:** none.

## D4 — Bearing storage cabinet (within one bay)
- **Intent:** Dense small-drawer cabinet, one bearing part number per drawer.
- **Status:** `idea` (build-vs-buy undecided).
- **Spec:** §14.
- **Identifier:** many small drawers (~15–18 cm wide), one bearing PN each.
- **Why / hard constraints:**
  - **Tiered by turnover:** Tier 1 high movers → larger drawers / bulk bins; Tier 2
    standard; Tier 3 rare → multi-part-number drawers.
  - Front = working stock, back = backup stock.
  - **Silica gel** in drawers (humidity).
- **Open questions:** see §15 (custom 50 cm build vs off-shelf cabinet).

## D5 — Piston kit storage (pigeon-hole grid)
- **Intent:** Open cubby grid; rows = motorcycle model, columns = oversize.
- **Status:** `idea`.
- **Spec:** §14.
- **Identifier:** cubby grid, model × oversize (STD / 0.25 / 0.50 / 0.75 / 1.00).
- **Why / hard constraints:** cubby sized slightly larger than the box; grid keeps the
  model × oversize lookup visual and fast.
- **Open questions:** see §15 (confirm box dimensions with supplier before sizing cubbies).

## D6 — Fastener storage (small heavy drawers)
- **Intent:** Drawers for bulk bolts/nuts — small footprint because density is high.
- **Status:** `idea`.
- **Spec:** §14 · weight method in `REFERENCE_DATA.md` §3.2 / §8.
- **Identifier:** small high-density drawers; weight-governed.
- **Why / hard constraints:**
  - **Weight, not volume, governs** — keep drawers small; heavy drawers on **lower levels
    only**.
  - **Iron flat-bar adapter** required for the heavy-duty slider mounting.
  - Internal trays → clear-plastic compartments.
- **Open questions:** see §15 (slider rating selection — shared with D2).

## D7 — Desk-side stationary drawer organizer (standalone)
- **Intent:** Small free-standing tool/stationery box in a shelf opening beside the work
  table. **Not** part of the modular shelf — no M8 interface.
- **Status:** `ready to build` (carpentry workshop).
- **Spec:** §14 · diagram `02-designs/desk-drawer-organizer.svg`.
- **Identifier:** ~24×25×20 cm standalone box, 3 shallow drawers, ball-bearing slides,
  ≈ 5 kg loaded.
- **Why / hard constraints:**
  - Standalone & light-duty → ignore the M8 system entirely.
  - Width grew **20 → 24 cm specifically to absorb slide clearance** — don't shrink it
    back without re-checking slide fit.
  - **12 mm plywood** (anti-consumerism + humidity stability beats solid wood here),
    **glued dados**, all edges sealed. Plywood's dimensional stability keeps slide
    clearance constant year-round in Kalimantan humidity.
  - Seal all wood; **silica-gel packet in the receipts/stamps drawer**.
- **Open questions:** none (material pinned in §14).

## D8 — Mobile mechanic tool cart (workshop side)
- **Intent:** Rolling open-bin tool cart shared by the mechanics in the open-air workshop.
  **Not** on the modular shelf — it rolls freely; no M8 interface.
- **Status:** `designed`.
- **Spec:** §17 · diagram `02-designs/mechanic-tool-cart.svg`.
- **Identifier:** 60×45×20 cm **open plank bin on 4 casters** (deck ~13 cm, rim ~33 cm),
  **4 fixed braced compartments** (A/B/C/D), **mechanic-built from owner-supplied materials**.
  No carpentry, no shelves.
- **Why / hard constraints:**
  - **Mechanic-built, no joinery (owner directive 2026-06-20).** Wood planks + off-the-shelf
    brackets + bolts/nuts/screws only; owner supplies materials. Keep it a **single shallow
    bin** — don't add a second level or revert to a plywood carcase / leg frame / push handle.
  - **Tip stability is free at this height.** Loaded CG ~20 cm over a 60×45 footprint → it
    **slides before it tips** (~0.95 g fore-aft). That is *why* the bin is low; don't raise it.
  - **3-axis bottom corners → 3-way corner brackets** (one flange per face); a single L or flat
    brace can't catch the vertical axis. Fallback: 2× 90° L per corner. Top corners → 90° L.
    ⚠️ source-check 3-way brackets first. See `REFERENCE_DATA.md` §6.
  - **Cleats carry the bottom in shear** (the impact path); **caster blocks** give the caster
    bolts real wood — don't bolt casters through a lone plank.
  - **8 mm rubber mat on the bin floor** — tools land there; cuts peak force ~6×
    (`REFERENCE_DATA.md` §3.4). Use the thickest plank for the bottom.
  - **4 fixed compartments = 3 full-height dividers**, braced with a small 90° L-bracket at
    each end (face grain, not end-grain screws — `REFERENCE_DATA.md` §6). They double as
    **anti-racking ribs**. Keep lanes **generously oversized** so it stays a toss cart — don't
    cut tool-shaped slots.
  - **No edge-parallel L-bracing** (considered & declined): redundant with the continuous
    cleats + the dividers, which already triangulate the box. Edge straps don't resist racking
    and add split-prone holes in soft Meranti. If more rigidity is ever wanted, add a top
    perimeter lip or corner gussets — not edge straps.
  - **Swivel casters are correct here** (the cart steers) — do **not** apply the all-fixed
    sprocket-unit rule. ⚠️ §4 Error 5 (that was a single-axis unit; this one is not).
  - Open-air canopy → wetter than the parts shop: **seal all wood incl. edges**, galvanized/
    zinc hardware, **brakes** (shared + abuse).
- **Open questions:** see §15 (3-way bracket availability vs L-fallback; caster & plank/mat sourcing).

---

*Maintenance: one card per design; when a design is added or a decision changes, update
the spec first, then this card. If a card and the spec disagree, the spec is right.*
