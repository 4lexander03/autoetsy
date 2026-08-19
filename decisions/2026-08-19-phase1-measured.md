# Phase 1 — Measured Protocol & Results

**Date:** 2026-08-19 · **Supersedes:** all prior Phase 1 scoring
**Status:** this is the first Phase 1 analysis based on a metric computed *identically*
across every candidate. Prior documents were intuition scores and are retained only as a
record of how the analysis went wrong.

---

## Why the earlier approach failed

Three structural faults, in order of severity:

1. **Thrashing, not converging.** Recommendation moved 83.5 → 74.5 → 72.5 → new leader at
   76.5 across four turns. That is reaction, not refinement.
2. **Scoring was theater.** 1–5 values assigned by intuition, multiplied by weights, to
   produce numbers with decimal points. The inputs moved freely between turns. A rubric
   whose inputs the analyst can re-score at will is an opinion in a table.
3. **Different tests for different candidates.** The "clone graveyard" check was applied to
   exactly one category — the one already under suspicion. That is confirmation, not
   comparison.

---

## The protocol

EverBee's inline column filters (unused until now) permit a directly comparable measurement.

**For each candidate category, holding filters constant and varying only the search term:**

- **W₁ₖ** = count of listings earning **≥ $1,000/month**
  (Revenue Min = 1000) → *how many winners exist at all*
- **W₆** = count of those **≤ 6 months old**
  (Revenue Min = 1000, Listing Age Max = 6) → *how many slots opened to newcomers recently*
- **Newcomer share** = W₆ / W₁ₖ → *is the category open or incumbent-locked*

W₆ is the number that matters. It answers the only question that counts for a new shop:
**can a listing created now actually earn?**

Read counts from `Showing: 20 of N`. Filters persist across search-term changes, so the
measurement is cheap and consistent.

---

## Results

| Category | Listings | W₁ₖ | **W₆** | Newcomer share | Generatable |
|---|---|---|---|---|---|
| **crochet pattern pdf** | 535,071 | 272 | **140** | 51% | **No** |
| digital planner | 688,673 | 79 | 27 | 34% | Medium |
| printable wall art | 2,620,344 | — | 18 | — | Medium |
| **stl file 3d print** | 195,800 | 30 | **13** | 43% | Medium |
| **cross stitch pattern pdf** | 396,297 | 31 | **12** | 39% | **High** |
| murder mystery | 21,155 | 13 | 8 | 62% | High |
| notion template | 26,213 | 9 | 8 | 89% | Medium |
| teacher classroom printable | 88,457 | 13 | 6 | 46% | Medium |
| **budget planner spreadsheet** | 34,550 | 31 | **2** | **6%** | Medium-High |
| laser cut file svg | 467,393 | 10 | 2 | 20% | High |
| puzzle book printable | 11,626 | **2** | — | — | High |

---

## What the measurement overturns

**Budget/finance spreadsheets — my recommendation one turn ago — is the most
incumbent-locked category measured.** Only 2 of 31 winners are under six months old (6%).
It looked strong because incumbents earn a lot; it is in fact nearly closed to entrants.
The metric caught this immediately, which is precisely what the intuition scoring failed to
do.

**Murder-mystery puzzle books: `puzzle book printable` contains exactly 2 listings earning
≥$1,000/month in the whole category of 11,626.** Both are CypherBlake. This confirms the
clone-graveyard finding numerically.

**Crochet is the most open market by a factor of five** — 140 listings created in the last
six months are earning $1,000+/month. But crochet patterns require physical design and
testing; they are not generatable, so automation provides no product edge there.

---

## Extended measurement — full candidate set

Motivated by a strategic observation: the image→grid-chart algorithm is not cross-stitch
specific. It also serves knitting colorwork, tapestry crochet, perler beads, punch needle
and plastic canvas. If those markets are open too, one engine serves several. Measured:

| Category | **W₆** | Generatable | Deliverable automatable |
|---|---|---|---|
| **wedding invitation template** | **160** | Medium | **No — Canva/Templett, manual setup** |
| crochet pattern pdf | 140 | No | n/a |
| **machine embroidery design** | **31** | **High** | **Yes — stitch files** |
| digital planner | 27 | Medium | Partly |
| printable wall art | 18 | Medium | Yes (but AI-art policy risk) |
| stl file 3d print | 13 | Medium | Yes |
| cross stitch pattern pdf | 12 | High | Yes |
| quilt pattern pdf | 12 | Low | Yes |
| sewing pattern pdf | 12 | Low | Yes |
| svg bundle cricut | 12 | High | Yes |
| knitting pattern pdf | 8 | Medium | Yes |
| murder mystery | 8 | High | Yes |
| notion template | 8 | Medium | Partly |
| teacher classroom printable | 6 | Medium | Partly |
| procreate brushes | 5 | Medium | Yes |
| coloring pages printable | 3 | High | Yes |
| budget planner spreadsheet | 2 | Medium-High | Yes |
| laser cut file svg | 2 | High | Yes |
| perler bead pattern | **0** | High | Yes |

The two most open markets are **not usable**: wedding invitations deliver editable Canva
templates (no meaningful API — every SKU is manual studio work), and crochet patterns need
physical design and testing. Openness alone is not the answer; openness **and** an
automatable deliverable is.

---

## Recommendation: machine-embroidery fonts & monogram alphabets

**W₆ = 31 — the highest of any category with a genuinely automatable deliverable, 2.5×
cross stitch. W₁ₖ = 59, so newcomer share is 53%: the market is genuinely open, not
incumbent-locked.**

### Why this one, specifically

Reading the actual winning listings, the category is dominated by **fonts and monogram
alphabets**, not pictorial designs:

- "BX Embroidery Fonts Bundle: 600 Font Pack"
- "70 BX Embroidery Fonts 0.5" 0.75" 1" 1.25" 1.5" 1.75" 2" Sizes, Monogram Alphabet"
- "Block Shadow Embroidery Font, 9 Sizes, A-Z sorted, Fill Stitch Monogram"
- "Fishtail Monogram 2 Color Embroidery Font, 5 Sizes 8 Formats + BX"
- "3D Puff Foam Embroidery Machine Fonts Bundle"

**The advertised value is literally the combinatorial expansion**: letters × sizes × stitch
types × machine formats. "6 Sizes, 8 Formats + BX" is the selling point. A hand-digitiser
produces one alphabet slowly; a generator produces 26 letters × 9 sizes × 11 formats — thousands
of files — deterministically, with machine-verifiable output.

**This is the exception the generatability/commoditization tension predicts should exist:**
a category where generation *is* the product value rather than a shortcut around craft, and
where the tedium is the barrier to entry.

### Observed economics

| Shop | Price | Rev/mo | Age | Growth |
|---|---|---|---|---|
| BlueGemEmbroidery | $19.70 | $6,580 | 4 mo | 400% |
| BlueGemEmbroidery | $17.00 | $5,950 | 10 mo | 600% |
| MoziCraft | $12.00 | $5,436 | 7 mo | 31% |
| RetroStitchArt | $35.86 | $4,841 | 10 mo | 33% |
| NinviaStore | $79.90 | $3,835 | 8 mo | 0% |
| HandmoribyLucia | $26.12 | $3,187 | 3 mo | 1100% |

Sweet spot $17–36, clear of the €10 German floor. Multiple recent entrants at $3–6.5k/mo.

### The critical constraint: font licensing

Digitising someone else's typeface and selling it is an IP problem, and OFL fonts do not
solve it (OFL forbids selling the font alone and requires derivatives stay OFL).

**Resolution: generate letterforms parametrically rather than digitising existing type.**
The best-selling styles — fishtail, block shadow, diamond, circular, 3D puff, satin
monogram — are *geometric constructions*, not typefaces. Building them from parametric
skeletons sidesteps licensing entirely and is exactly the kind of generator this project
was conceived around. Any use of third-party type requires an explicit embroidery/commercial
licence and must be treated as a hard gate.

### Honest weaknesses

- **Domain complexity is real.** Good digitising means stitch direction, density, underlay,
  pull compensation, and push-pull distortion. Bad output ruins fabric and earns 1-star
  reviews. This is a harder engine than a PDF puzzle generator.
- **Output verification needs physical testing** — at minimum a machine or a tester. We can
  verify files parse and stitch counts are sane, but not that they *sew well*, and that gap
  is where the reviews live.
- **Format coverage is table stakes** — PES, DST, JEF, EXP, VP3, HUS, XXX, and BX. Missing
  formats means missing buyers.
- **Denominator caveat:** W₆ counts depend on search-string breadth, which differs between
  categories. Absolute comparisons are indicative, not exact.

- **W₆ = 12** — twelve listings created in the last six months earning $1,000+/month.
  Six times budget spreadsheets, and unlike murder mystery it is not one shop.
- **Genuinely generatable.** Image → chart conversion is a deterministic algorithm: colour
  quantization to a DMC floss palette, grid mapping, symbol assignment, PDF chart generation
  with legend and floss list. Correctness is machine-verifiable.
- **Price tolerance is high** — winning products are themed *bundles* at $50–175, well clear
  of the €10 German floor. Observed: GildedMothPatterns $70 → $11,200/mo (9 mo old);
  HappyLittleMouse $175 → $4,550/mo (8 mo old).
- **Sourcing the artwork is the real problem, and it has a clean answer: public-domain
  archives.** Vintage botanical plates, art nouveau, Japanese woodblock, natural-history
  illustration. No AI-art dependency, no IP exposure, unlimited source material — and the
  themes that actually sell in this category (gothic, dark academia, botanical, celestial,
  cottagecore) map directly onto public-domain collections.
- **The moat is pipeline quality**, not the idea: floss-count optimisation, colour reduction
  that still reads at stitch scale, Pattern Keeper compatibility, printable chart layout.
  Clones with a naive image-to-grid converter produce unstitchable output.

### Honest weaknesses

- 396,297 listings and an EverBee keyword score of **0** — SEO on head terms is hopeless.
  Entry must be through long-tail themes and bundle positioning, not "cross stitch pattern".
- W₆ = 12 is a modest absolute number. This is a real but narrow opening.
- Support burden is higher than a PDF game: floss substitutions, Pattern Keeper questions,
  print sizing.

---

## Commitment on method

This recommendation rests on a measurement, not a score. **It should only be overturned by
the same kind of evidence** — a category with a higher W₆ that is also generatable. Further
intuition-level arguments, mine included, do not qualify.

Remaining gaps, stated rather than glossed: W₁ₖ for printable wall art was not captured;
W₆ was not measured for the ~10 categories swept but not shortlisted; and the $1,000/month
threshold is a judgement call — a $500 threshold would rank categories differently.
