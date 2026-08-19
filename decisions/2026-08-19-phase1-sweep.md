# Phase 1 — Systematic Sweep (supersedes initial findings)

**Date:** 2026-08-19 · **Categories swept:** 23 · **Supersedes:** `2026-08-19-phase1-findings.md`

---

## Headline: my first recommendation was survivorship bias

EverBee sorts by revenue. **A revenue-sorted list always shows winners.** I read the top of
those lists and concluded "new entrants win in 1–4 months." The sweep revealed the base rate
underneath, and it is brutal.

### The clone graveyard

Searching `puzzle book printable` (11,625 listings) exposes the *full* distribution of the
murder-mystery elimination format that I recommended:

| Shop | Age | Rev/mo |
|---|---|---|
| **CypherBlake** (bundle) | 2 mo | **$5,671** |
| **CypherBlake** (single) | 1 mo | **$2,142** |
| CleverlyClued | 2 mo | $560 |
| AtelierDesMysteres | 1 mo | $381 |
| ClueVerse | 1 mo | $250 |
| HiddenQuestLab | 2 mo | $199 |
| ChewieMacRuns | 2 mo | $194 |
| DailySparkDigitals | 2 mo | $185 |
| PuzzleForgePress | 2 mo | $150 |
| CleverlyClued (×3 more) | 2–3 mo | $166 / $146 / $311 |

**Seven-plus new entrants in the last 1–3 months. Every one under $600/month. Median ~$200.**
That is the realistic outcome for entrant #8, not $11k.

The same pattern in `cold case file` (781 listings): MidnightBureau takes $11,508, and the
entire rest of the category sits at $127–$582 — **including MidnightBureau's own other
listings** ($582, $485, $215). Their #1 listing is 86% of their revenue.

### The generalised finding

**In this category, revenue concentrates in individual breakout listings, not in shops or
formats.** A generator producing 200 variants of a format whose winners win on positioning
would most likely produce 200 listings earning $0–100 each.

---

## The central strategic tension

Sweeping 23 categories surfaced something more important than any single niche:

> **The more programmatically generatable a category is, the more commoditized it is.**

This is not coincidence, it is equilibrium. If a product can be generated, it can be cloned,
and price collapses. Observed directly:

- **Laser-cut SVG** — perfectly generatable → "20 million files for $18" → top listing $2,520
- **Word search** — trivially generatable → top listing $1,154 in 26,034 listings
- **Murder-mystery logic puzzles** — generatable → 7 clones in 3 months, all under $600
- **Cross stitch** — algorithmically generatable → 396,297 listings, keyword score **0**

Meanwhile the highest-revenue categories are gated by *design and UX quality*, which is
exactly what a generator does not provide.

**Implication for the project:** automation's edge is probably not in generating the product.
It is in the operational layer — listing creation, SEO, analytics, expansion decisions — over
a product with a genuine quality barrier. That is a meaningful reframe of the original thesis
and should be reflected in the gameplan.

The exception worth hunting: categories where generation produces something a hand-maker
genuinely **cannot** match (volume that is itself the value, or personalization at scale).

---

## New discriminator: revenue distribution within a shop

Better signal than raw competition count. **Does one shop hold multiple strong listings?**
If yes, the formula is repeatable and suits automation. If one listing carries everything,
success was positioning or luck.

| Category | Repeatability evidence | Verdict |
|---|---|---|
| **Budget/finance spreadsheets** | PrioriDigitalStudio: **4 listings** in top 20 ($15.4k, $7.4k, $2.8k, $2.3k) | **Repeatable** |
| **Teacher/classroom printables** | AlwaysSunnyCo: **6 listings** in top 20 ($8.7k → $1.2k) | **Repeatable** |
| Crochet patterns | BrianaKdesigns ×2, MJsOffTheHook ×2 | Repeatable, not generatable |
| Digital planners | LittleBirdieCanada ×2, PrioriDigitalStudio ×2 | Repeatable |
| **Murder mystery** | One listing = 86% of shop revenue | **Not repeatable** |

---

## Full sweep data

| Category | Listings | Top rev/mo | Notes |
|---|---|---|---|
| printable wall art | 2,620,344 | $6,750 | Mega-bundle spam ("35,000 prints") |
| instant download printable | 1,932,149 | $11,508 | Top-down scan |
| digital planner | 688,673 | $9,753 | DPCDigitals $99 → $6,732 @ 1 mo |
| crochet pattern pdf | 535,071 | $12,090 | Healthy spread, not generatable |
| laser cut file svg | 467,393 | $2,520 | Commoditized |
| cross stitch pattern pdf | 396,297 | $11,200 | Keyword score 0 |
| coloring pages printable | 365,026 | $3,821 | Low price ceiling |
| svg bundle cricut | 292,678 | $7,794 | IP-risky (Disney/Pokemon bundles) |
| wedding invitation template | 249,634 | $4,788 | Canva-template design work |
| stl file 3d print | 195,800 | $5,418 | Top slots are manual services |
| teacher classroom printable | 88,457 | $8,740 | **AlwaysSunnyCo ×6 — repeatable** |
| procreate brushes | 71,892 | $12,500 | Top is a $250 tattoo outlier |
| resume template | 43,541 | $2,586 | Weak |
| **budget planner spreadsheet** | **34,550** | **$15,433** | **Highest revenue swept; ×4 repeatable** |
| notion template | 26,213 | $4,577 | PlanoraNotion 1100% growth @ 3 mo |
| word search printable | 26,034 | $1,154 | Generatable but worthless |
| murder mystery | 21,155 | $11,508 | Concentrated |
| tarot cards printable | 11,803 | $700 | Dead |
| puzzle book printable | 11,625 | $5,671 | Clone graveyard |
| logic puzzle | 8,285 | $5,671 | CypherBlake holds #1 and #2 |
| escape room printable | 6,446 | $2,757 | Kids segment, $8–24 |
| cold case file | 781 | $11,508 | One winner, rest under $600 |
| custom soundwave art (physical) | 3,646 | $3,760 | Validates seller's separate business |
| sound wave art digital | 1,120 | $72 | Dead |

---

## Seasonality — resolved

Google Trends, "murder mystery game", worldwide, 5 years:

- **Baseline roughly doubled** — ~25 (2022–23) to ~45–50 (2026). Genuine secular growth.
- Episodic spikes (a large one Feb 2023, a peak ~85 around Mar 2026), not a clean annual
  Halloween cycle.
- **Currently past the March 2026 peak**, sitting mid-range.
- **Regional:** UK 100, New Zealand 96, Australia 74, Canada 70, **US 66**. This category
  skews Commonwealth, not US — a partial exception to the "target US buyers" rule in
  GAMEPLAN §8.3.

**Verdict: not primarily seasonal.** That concern is cleared. It does not rescue the
concentration problem.

---

## Revised scoring

| Candidate | Score | Change |
|---|---|---|
| **Budget/finance spreadsheet templates** | **76.5** | **New #1** |
| Murder-mystery logic puzzles | 72.5 | 83.5 → 74.5 → 72.5 (competition quality 5→3→2) |
| Teacher/classroom printables | 69.0 | New entry |
| Cross stitch bundles | 71.0 | unchanged |
| Laser-cut SVG | 65.5 | unchanged |
| STL 3D print | 65.5 | unchanged |

### Why budget/finance spreadsheets now lead

- **Highest top-line revenue of all 23 categories swept** ($15,433/mo).
- **Moderate competition** (34,550) — an order of magnitude below the printable giants.
- **Proven repeatability** — one shop holds 4 of the top 20 slots.
- **Genuinely generatable, with a quality moat.** Structure, formulas, and category variants
  (wedding · travel · freelance · household · student · small business · debt payoff · ADHD ·
  couples) are code-generatable, while *design and UX polish* remain a real barrier that
  clones struggle to clear. This is the rare category with generatability **and** a moat —
  the exception the strategic tension above predicts should be hunted.
- Prices €18–58, comfortably clear of the €10 German floor.
- Low policy risk, no IP exposure, no AI-art dependency.

### Confidence and what is still unverified

**Moderate, not high.** I have been wrong once in this session by over-reading top-of-list
data. The specific gap: I have top-20 data for spreadsheets but have **not** run the same
distribution analysis I ran on mystery — the equivalent of the clone-graveyard check.

**Before locking, verify:**
1. Full revenue distribution in the spreadsheet category — are recent entrants earning, or is
   PrioriDigitalStudio another MidnightBureau?
2. Shop Analyzer on PrioriDigitalStudio and ExclusiveDesignLab — listing counts and shop age.
3. Support burden reality check — Excel/Sheets products may generate far more buyer questions
   than a PDF, which matters given there is no messaging API.
