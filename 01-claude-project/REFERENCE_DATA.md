# Reference Data — Woodworking Engineering

## 1. Wood Properties

### Meranti Putih (Pakit) — Primary structural material

| Property | Value | Notes |
|---|---|---|
| Density (air dry) | 400-580 kg/m³ | Medium-soft hardwood |
| Compression parallel to grain | 30-45 MPa | Strong direction |
| Compression perpendicular to grain | 5-7 MPa | Weak direction (cross-grain) |
| Bending strength (MOR) | 60-85 MPa | |
| Modulus of elasticity | 9,000-12,000 MPa | |
| Janka hardness | ~2.5-3.5 kN | Soft-medium |
| Humidity sensitivity | High | Loses ~30% strength when wet |

**Practical notes for Meranti Putih:**
- Tends to crack along grain under concentrated stress
- Bolt holes can elongate under cyclic loads (use fender washers)
- Acceptable for most furniture and shelf applications
- NOT suitable for highest-load structural members
- Requires sealing/varnishing in humid environments

### Alternative woods available in Kalimantan (for upgrade considerations)

| Wood | Hardness vs Meranti | Cost | Notes |
|---|---|---|---|
| Bengkirai (Yellow Balau) | 2-3× harder | Moderate | Good middle-ground upgrade |
| Kapur | 1.5-2× harder | Moderate | Common, reliable |
| Keruing | 1.5-2× harder | Moderate | Heavy and durable |
| Ulin (Borneo Ironwood) | 4-5× harder | Expensive | Difficult to work, premium structural |
| Jati (Teak) | 2-3× harder | Expensive | Premium, beautiful, stable |

---

## 2. Fastener Properties

### Steel bolt density
- **7.85 g/cm³** (mild steel)
- Used for weight calculations of bulk fasteners

### Standard bolt weights (approximate, per piece, grade 8.8, hex head)

| Size | Weight |
|---|---|
| M5 × 30 | ~5 g |
| M6 × 30 | ~7 g |
| M8 × 30 | ~17 g |
| M10 × 30 | ~33 g |
| M12 × 30 | ~55 g |

### Hole spacing rules
- **Minimum hole spacing**: 3× hole diameter (for 8mm hole = 24mm minimum)
- **Recommended for wood durability**: 5× hole diameter
- **Edge distance**: minimum 2× hole diameter from any wood edge

### Drawer slider ratings (typical)

| Slider Width | Standard Rating | Heavy Duty Rating |
|---|---|---|
| 27mm | 8-15 kg | 20-25 kg |
| 35mm | 15-20 kg | 25-30 kg |
| 45mm | 20-25 kg | 30-35 kg |
| 50-58mm (industrial) | 35-50 kg | 60-100+ kg |

**Apply 0.7 safety factor** to all ratings for real-world cyclic use.

---

## 3. Calculation Methodologies

### 3.1 Compression stress at joint
```
Stress (MPa) = Force (kN) / Contact Area (cm²) × 10
```

**Example**: 50kg load on 4×6cm column footprint
- Force = 50kg × 0.01 = 0.5 kN
- Area = 4 × 6 = 24 cm²
- Stress = 0.5 / 24 × 10 = 0.21 ... wait check unit conversion

**Correct conversion**:
- 50kg load = 50 × 9.81 N = 490 N = 0.49 kN
- Area = 24 cm² = 24 × 10⁻⁴ m² = 2.4 × 10⁻³ m²
- Stress = 490 N / 2.4×10⁻³ m² = 204,167 Pa = 0.20 MPa

**Compare to limit**: Meranti perpendicular grain = 5-7 MPa
- Safety factor = 5 / 0.20 = ~25×

### 3.2 Bolt count for inventory weight estimation
```
Total weight = Number of bolts × Bolt weight per piece
Number of bolts ≈ Drawer volume × Packing efficiency / Bolt volume
```

Packing efficiency for random loose bolts in a container: **~45%**

### 3.3 Drawer load safe limit
```
Safe load = Slider rating × 0.7 (cyclic use safety factor)
```

### 3.4 Impact (thrown / dropped tool) load — energy method
```
E      = m · g · h     (impact energy, J)
v      = √(2 g h)      (impact velocity, m/s)
F_avg  ≈ E / d         (average force over stopping distance d)
```
Peak force scales as **1/d** → a *softer* landing surface (larger `d`) lowers peak force;
a *rigid* surface raises it. This is the opposite of static-load intuition.

**Worked**: m = 1.5 kg (heavy wrench), h = 0.5 m (moderate toss) → E = 1.5×9.81×0.5 = **7.36 J**.
- Bare plywood, d ≈ 1.5 mm: F ≈ 7.36 / 0.0015 = **4,900 N (~500 kgf)** — concentrated on a
  tool edge → splits Meranti, fatigues joints.
- 8–10 mm rubber mat, d ≈ 10 mm: F ≈ 7.36 / 0.010 = **740 N (~75 kgf)** → **~6× reduction**.

**Design rule**: in any throw/drop zone use a **rigid frame + compliant impact surface**
(rubber mat). Applied in `DESIGN_SPECIFICATIONS.md` §17 (mechanic tool cart).

---

## 4. Common Errors To Avoid (project history)

These are errors that have occurred in this project. Actively avoid repeating them.

### Error 1: Confusing column face orientation
**Wrong**: Assumed 8mm holes were drilled in the 4cm face, calculated only 1.6cm of wood remaining on each side.
**Correct**: Holes are in the 6cm face, leaving 2.6cm on each side. Always verify which face is being drilled.
**Prevention**: Ask "which face are the holes in?" before calculating wood-around-hole margin.

### Error 2: CVT roller weight direction
**Wrong**: Stated heavier rollers = more low-end torque (this is backwards).
**Correct**: Lighter rollers stay in lower ratio longer = more low-end torque. Heavier rollers open variator faster = more top speed.
**Prevention**: Verify centrifugal mechanics; heavier rollers generate more centrifugal force, which OPENS the variator earlier.

### Error 3: Nail withdrawal concern wrong direction
**Wrong**: Worried that vertical column load would pull nails out of the floor-to-beam connection.
**Correct**: Nails inserted upward from below have the head stopped by the floor. Gravity works WITH the nail, not against it. Withdrawal is not a concern in this direction.
**Prevention**: Visualize the nail direction and the force direction before assuming withdrawal risk.

### Error 4: Treating fully-supported beam as a spanning bridge
**Wrong**: Suggested 4×6cm beam was undersized for a 3m span, concerned about sagging.
**Correct**: If the beam is continuously supported (nailed to floor full length, or anchored to wall full length), it doesn't span — it's a load distributor. No sagging risk because there's no unsupported span.
**Prevention**: Check support conditions before applying beam-sagging logic.

### Error 5: Swivel front wheels for a sliding unit
**Wrong**: Suggested swivel front + fixed rear casters for the rolling sprocket unit.
**Correct**: The unit only moves in one straight line (in and out of fixed location). All fixed wheels track straighter, simpler, cheaper.
**Prevention**: Confirm the motion pattern before applying cart-steering conventions.

### Error 6: T-bracket orientation confusion
**Wrong**: Described T-bracket as having "horizontal arms extending both directions along the beam" at outer corners where the beam only extends in one direction.
**Correct**: At outer corners with material in only two directions, either use L-bracket OR orient T-bracket with the long arm along the column (gripping above and below joint) and single perpendicular arm onto the beam.
**Prevention**: Visualize where wood material exists before describing bracket orientation.

### Error 7: Wood grain direction on joint loads
**Reminder**: Wood is 5-7× weaker perpendicular to grain than parallel.
- Lap joint loads on the side beam = perpendicular to side beam grain
- Bottom beam loaded by column = perpendicular to bottom beam grain
- Both are cross-grain compression
- Acceptable here ONLY because contact areas are large (not concentrated)
**Prevention**: Always identify grain direction relative to load direction.

---

## 5. Safety Factor Guidelines

Standard safety factors used in this project:

| Component | Safety Factor | Rationale |
|---|---|---|
| Wood compression | 5-10× | Wood is variable, defects, creep |
| Drawer slider | 0.7 × rated | Cyclic loading, real-world conditions |
| Bolt/screw shear | 1.5-2× | Quality variations |
| Overall shelf load | 1.5× | General engineering practice |
| Bracket steel thickness | Minimum 2-3mm | For structural use |

---

## 6. Bracket Geometry Quick Reference

### When to use L-bracket
- Outer corners (material in only 2 perpendicular directions)
- Top/bottom of outermost columns
- Where beams end at a column

### When to use T-bracket
- Inner joints (material in 3 directions)
- Column bases between continuous beams
- Where reinforcement needs to grip multiple points on one piece

### T-bracket orientation options
**Option A**: Long arm onto column (grips column at 2 points above/below joint), single horizontal arm onto beam — works at outer corners
**Option B**: Long arm spans the beam (grips beam on both sides of column), single arm onto column — works at inner positions where beam continues

Choose based on which orientation has full wood contact for all arms.

### When to use a 3-way corner bracket
- A **true 3-axis box corner** — three boards meeting at a point (two walls + a floor), e.g.
  the bottom corners of the mechanic tool bin (§17). One flange screws to each of the three
  mutually perpendicular faces, tying all three boards with a single part.
- A single L-bracket or a flat corner brace **cannot restrain the third (out-of-plane) axis**.
  If 3-way brackets aren't available, substitute **2× 90° L-brackets per corner** placed on
  two different edges, so all three axes are caught between them.
- Pair with a **cleat** under the floor board so impact is carried in shear by wood, not by
  the bracket screws.

### Bracing an internal divider that butts into a wall
- A divider butting into the face of a wall is **end-grain meeting face-grain**. Screwing
  straight into the divider's **end grain holds poorly** (low withdrawal strength).
- Tie it with a **small 90° L-bracket at each end** instead — both flanges then land on
  **face grain** (one on the divider face, one on the wall face), which holds well.
- Bonus: dividers braced to both long walls act as **internal anti-racking ribs**, stiffening
  the whole box (cf. the back panel / side partitions on the main shelf, §8 of the spec).

### Edge bracing — what actually helps (and what doesn't)
- A **continuous cleat** (or glue line) along a seam beats **discrete L-brackets spaced along
  the same edge** — it distributes load over the full length instead of at a few points. Don't
  add edge brackets where a cleat already runs (redundant, and extra holes split soft wood).
- **Edge-parallel brackets do not resist racking.** Racking (a box parallelogramming) is beaten
  by **triangulation or a diaphragm**: internal ribs/dividers, a panel (back/bottom), diagonal
  **corner gussets**, or a **top perimeter lip** that frames an open rim. Reach for those before
  adding straps along straight edges.

---

## 7. Climate Adaptation (Kalimantan Tropical)

### Humidity protection
- Silica gel packets in bearing storage, fastener drawers, electronic parts
- Replace silica gel every 6 months
- Sealed wood (varnish, polyurethane, or oil finish) for all exposed surfaces

### Rust prevention for metal components
- Zinc-plated or galvanized fasteners preferred
- Bare steel must be painted or oiled before installation
- Stainless steel for highest-stress fasteners (if budget allows)

### Wood treatment
- Initial coat: wood preservative against rot/insects
- Finish coat: polyurethane or alkyd varnish for moisture resistance
- Reapply every 2-3 years on exposed surfaces

---

## 8. Storage Calculation Reference

### Volume estimates for common parts
- Bearing 6201 box: ~50 cm³
- Bearing 6301 box: ~75 cm³
- Piston kit box (10×10×8): 800 cm³
- M8 bolt (30mm): ~3 cm³
- Sprocket (depending on size): 80-200 cm³ flat

### Inventory planning for high-volume items
- 20 units/day consumption = 600/month = need at least 600 units storage capacity for monthly restock cycle
- For weekly restock: 140 units capacity
- For bi-weekly restock: 280 units capacity

---

## 9. Conversion References

| From | To | Multiplier |
|---|---|---|
| kg | N | × 9.81 |
| cm² | m² | × 10⁻⁴ |
| MPa | N/mm² | × 1 (same) |
| inches | cm | × 2.54 |
| pounds | kg | × 0.454 |

---

## 10. Project-Specific Constants

```
COLUMN_WIDTH = 4 cm
COLUMN_DEPTH = 6 cm
COLUMN_HEIGHT = 200 cm
HOLE_DIAMETER = 8 mm
HOLE_SPACING = 10 cm
SECTION_CLEAR_WIDTH = 80 cm
SHELF_DEPTH = 50 cm
NUMBER_OF_SECTIONS = 3
NUMBER_OF_COLUMNS = 6
TOTAL_WIDTH = 256 cm
MAX_LOAD_PER_LEVEL = 25 kg
MAX_LOAD_TOTAL = 200 kg
BOLT_SIZE = M8
SAFETY_FACTOR_SLIDER = 0.7

# Mobile mechanic tool cart (D8 — §17) — SIMPLE PLANK BIN ON CASTERS
CART_W = 60 cm
CART_D = 45 cm
CART_BOX_H = 20 cm           # plank box height (open top), casters extra
CART_DECK_H = 13 cm          # bin floor above ground = caster height
CART_RIM_H  = 33 cm          # deck 13 + 20 cm box
CART_CG_H   = 20 cm          # loaded centre of gravity (trivially tip-stable)
CART_CASTER_WHEEL = 100 mm
CART_CASTER_RATING = 50 kg   # each, 2 rigid + 2 swivel-brake
CART_MAT_THICKNESS = 8 mm    # rubber impact liner on the bin floor
CART_LANES = 4               # fixed tool-category compartments (A/B/C/D)
CART_DIVIDER_COUNT = 3       # full-height dividers between the 4 lanes
CART_DIVIDER_H = 20 cm       # full height (flush with the rim)
```

Reference these constants when calculating to ensure consistency with the existing design.