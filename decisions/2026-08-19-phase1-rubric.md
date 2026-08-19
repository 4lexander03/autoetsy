# Phase 1 — Niche Selection Rubric

**Date:** 2026-08-19 · **Status:** active · **Decides:** product category + engine type

The niche and the engine type are chosen together — a niche we can't generate
programmatically is not a niche we want. This rubric encodes that.

---

## Hard filters (fail any → discard, no scoring)

1. **Fully digital delivery.** Auto-download via Etsy. No physical, no made-to-order
   requiring manual work per sale.
2. **Supports a €12+ price point.** German fee stack makes anything below €10 a trap
   (GAMEPLAN §8.1). If the category's realistic ceiling is €5 files, discard it.
3. **Programmatically generatable.** A script must be able to produce unlimited valid,
   *distinct* variants from parameters or an input file. Not "AI generates an image" —
   deterministic generation we control and can QA.
4. **Original design, defensible under Etsy Creativity Standards.** We must be able to
   answer "who designed this?" with "we wrote the generator."
5. **No licensing landmines.** No fonts/assets/IP we can't license for commercial resale.
   No trademarked characters, teams, brands.
6. **No regulated claims.** Nothing medical, legal, financial-advice, or safety-critical.

---

## Scored criteria

Each 1–5. Weights reflect what actually predicts revenue.

| # | Criterion | Weight | 1 | 5 |
|---|---|---|---|---|
| 1 | **Generatability** | ×3 | Each unit is hand-made | One script → 500 distinct, genuinely useful variants |
| 2 | **Demand depth** | ×3 | Thin, seasonal, fad | Steady year-round search volume, multiple sub-segments |
| 3 | **Price tolerance** | ×2 | Buyers expect €3 | €15–40 normal, bundles accepted |
| 4 | **Competition quality** | ×2 | Saturated with strong, well-designed shops | Many listings but weak execution — beatable on quality |
| 5 | **Personalisation lever** | ×2 | Generic file only | Buyer input (name, data, photo, text) → made-to-order premium |
| 6 | **Repeat/expansion surface** | ×1.5 | One-and-done | Natural families, sets, seasonal refreshes, upsell bundles |
| 7 | **Build cost** | ×1.5 | Months of engine work | Working generator in <2 weeks |
| 8 | **Thumbnail-ability** | ×1.5 | Hard to show value in a square image | Instantly legible, visually striking at thumbnail size |
| 9 | **Support burden** | ×1 | Format/compat questions, printing help | Self-explanatory, no messages |
| 10 | **Policy risk** | ×1 | AI-art adjacent, IP-grey, crowded enforcement target | Clearly original, uncontroversial |

**Max weighted score: 95.** Shortlist anything ≥ 65. Below 55, don't argue for it.

### Notes on the weights

- **Generatability and demand are both ×3** — they're the only two that can't be fixed
  later. Weak design can be improved; a category that can't be generated or that nobody
  searches for is unfixable.
- **Competition quality, not competition volume.** High listing counts with poor execution
  is the *best* signal available — it proves demand and shows the bar is low.
- **Thumbnail-ability is underrated** and gets its own weight because click-through is the
  first gate on Etsy and the one we can most directly engineer (GAMEPLAN §2.4).
- **Personalisation** matters disproportionately: it justifies premium pricing, defends
  against copycats, and is exactly what a parametric generator does best.

---

## Per-candidate deliverable

For each niche researched, produce:

1. **Scorecard** — all 10 criteria with one-line justification each, weighted total.
2. **Engine sketch** — what the generator takes as input, what it emits, roughly how it
   works, and the honest build estimate.
3. **Evidence** — top-10 competing shops: listing counts, price points, review velocity,
   estimated monthly sales (EverBee), quality read on their thumbnails and copy.
4. **Price model** — realistic list price, bundle structure, net after German fees.
5. **First 20 SKUs** — concrete list. If we can't name 20, generatability is a 2, not a 5.
6. **Kill risk** — the single most likely reason this fails.

---

## Method

- 6–8 candidates researched to the same depth, scored on the same rubric.
- **Evidence over intuition.** Every demand and competition claim traces to EverBee data
  or observed Etsy listings, not to a model's prior about what sells.
- Ranked table + recommendation → human picks. This decision is not delegated.

---

## Market scope

Score demand in the **US market**, not the German one. Listings will be English-language
and priced for US buyers (GAMEPLAN §8.3). Etsy traffic is US-dominated and Etsy handles
EU VAT automatically, so seller residence does not constrain the target market.

---

## Open inputs needed before scoring

- **EverBee Growth**, one month, for revenue-per-listing estimates (criteria 2 and 4).
  Numbers used for *ranking only* — see GAMEPLAN §8.2 on proxy-estimate accuracy.

## Confirmed assets (affects criterion 7)

- **Existing parametric audio → wall-art generator codebase (lasercut/CNC), confirmed
  available 2026-08-19.** Materially lowers build cost for any candidate in the
  parametric/generative-art family.
- Consequence: a **digital** variant of that engine — selling SVG/DXF/print-ready files
  rather than physical pieces — enters the pool as a seeded candidate. It is scored on the
  same rubric as everything else, with its build-cost advantage **disclosed on criterion 7
  rather than allowed to bias the other nine**. It does not get waved through on sentiment.

### Scan findings (2026-08-19, structure only)

`C:\dev\rib-slicer-v2` — 158 files, 74 TypeScript sources (~860KB), Vite app, plus
`GENERATOR-SPEC.md` / `CATALOGUE-PLAN.md` / `VIEW-SPEC.md`. **Already exports STL, DXF,
SVG, OBJ.** A digital variant is packaging + batch generation, not core engineering →
criterion 7 scores high. Two distinct audiences from one engine: lasercut/CNC (SVG/DXF)
and 3D printing (STL).

### Structural constraint — personalization does not automate

Etsy instant downloads deliver a **fixed** file. Buyer-supplied audio → custom output
cannot be auto-delivered, and there is **no messaging API** (GAMEPLAN §11) to automate the
handoff. Three separable businesses result:

| Shape | Price | In the automated loop? |
|---|---|---|
| Instant-download catalogue (pre-generated, hundreds of SKUs) | €12–25 | **Yes** |
| Personalized made-to-order files (buyer's audio) | €25–60 | No — manual generate + deliver |
| Physical built pieces (seller's existing plan) | Highest/unit | No |

**Only shape 1 is scored by this rubric.** Shapes 2 and 3 remain viable businesses and can
cross-sell from the digital listings; they are simply out of scope for automation. Any
candidate whose value depends on per-buyer customization must be scored on what its
*instant-download* form can earn, not its personalized form.
