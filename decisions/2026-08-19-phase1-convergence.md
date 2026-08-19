# Phase 1 — Convergence

**Date:** 2026-08-19 · Closes the search. Same metric throughout: **W₆** = listings ≤6 months
old earning ≥$1,000/month.

---

## Wedding websites — dropped

Rejected on the seller's objection, which was correct and which my own framework should
have caught. Wedding sites sell on **taste**: buyers choose "old money sage green" because
it looks right, not because it has an RSVP widget. A parametric generator would emit 200
competent, characterless variants. That is exactly the generatable⟺commoditized rule, and
I had been reasoning from deliverable format rather than from what the buyer is paying for.

---

## Grid-craft family — measured, and dead

Hypothesis: crochet is the most open market measured (W₆ = 140), and its *chart-based*
sub-segment uses the same image→grid algorithm as cross stitch. One engine, several markets.

**Falsified.**

| Category | W₆ |
|---|---|
| graphgan pattern | **0** |
| c2c crochet pattern | **0** |
| tapestry crochet pattern | 2 |
| bead loom pattern | **0** |
| peyote stitch pattern | **0** |
| plastic canvas pattern | **0** |

**Crochet's openness does not transfer to its generatable sub-segment.** Those 140 winners
are garments, amigurumi and construction-based blankets — real design work with physical
testing. The chart-based corner of crochet is empty.

## Other generatable categories — also closed

| Category | W₆ |
|---|---|
| printable labels | 6 |
| printable stickers | 4 *(unvalidated — measured during a throttled window)* |
| seamless pattern digital paper | 3 |
| montessori printables | 2 |
| flashcards printable | 1 |
| bingo cards printable | **0** |
| name tracing worksheet | **0** |

---

## The result the search converged on

Across ~60 categories, all measured identically, exactly **two** combine an open market with
a deliverable a generator can actually produce:

| Category | W₆ | Verifiable without physical testing? |
|---|---|---|
| **machine embroidery design** | **31** | **No** — needs a machine to confirm it sews |
| **cross stitch pattern pdf** | **12** | **Yes** — chart correctness is screen-checkable |

Everything else is either closed (0–8), not generatable (crochet, quilting, sewing), taste-
gated (wedding, wall art, planners), or manual to deliver (Canva templates).

### The trilemma

This is the real finding of Phase 1, and it explains every dead end above:

> **Open market · fully generatable · verifiable without physical goods — pick two.**

- Open + generatable, *not* verifiable → **machine embroidery** (stitch quality needs a machine)
- Open + verifiable, *not* generatable → **crochet, quilting, sewing** (design is the product)
- Generatable + verifiable, *not* open → **puzzles, word search, bingo, laser SVG, spreadsheets**

Cross stitch is the one candidate that scrapes all three, and it pays for that with the
weakest market of the three groups.

---

## Options

**A — Machine embroidery fonts.** Best market (W₆ = 31, 53% newcomer share), $17–36 price
band, value *is* the combinatorial expansion (letters × sizes × stitch types × formats).
Requires solving physical verification: a domestic embroidery machine is roughly €300–500,
or a paid tester. Without one, we ship blind and reviews punish us.

**B — Cross stitch bundles.** W₆ = 12, fully screen-verifiable, no hardware. Chart generation
is deterministic; artwork comes from public-domain archives (vintage botanical, art nouveau,
woodblock), which sidesteps both AI-disclosure and IP risk. Weaker market, hopeless head-term
SEO — entry must be long-tail and bundle-led.

**C — Invert the thesis.** Accept that no category offers a fully automatable *product* with
a good market, and instead automate the *operations* — listing creation, SEO, pricing,
analytics, expansion decisions — over a product with one human design step. This is the
option the evidence actually points at, and it contradicts the original "Claude makes
everything" framing. Worth stating plainly rather than engineering around.

---

## Method note

Two measurement defects were found and fixed earlier (wrong column; read lag). During this
run EverBee began throttling under rapid queries and returned stale counts — caught by a
control returning 0 where 12 was expected. Settle time was raised to 14s and controls were
placed at both ends of each batch. Figures above passed an adjacent control; the one that
did not is flagged inline. Untested and worth a later pass: canva template bundles, invoice
and business templates, reading journals, calendars.
