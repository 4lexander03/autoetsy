# Phase 1 — Puzzle / Quiz / Game Branch: Deep Measurement

**Date:** 2026-08-19 · **Question:** is there anything left in the murder-mystery /
quiz-engine branch, beyond seasonal Halloween product?
**Metric:** W₆ = listings **≤6 months old** earning **≥$1,000/month** (see
`2026-08-19-phase1-measured.md` for protocol).

---

## Answer: no. The branch is closed.

24 categories measured. The best result in the entire branch is **murder mystery at 8**,
and that 8 is concentrated in two shops already fighting off clones. Everything else is 0–5.

| Category | W₆ |
|---|---|
| **murder mystery** | **8** |
| baby shower games printable | 5 |
| bridal shower games printable | 2 |
| logic puzzle | 2 |
| puzzle book printable | 2 |
| brain teaser printable | 2 |
| trivia game printable | 1 |
| printable games for adults | 1 |
| bachelorette party games printable | 1 |
| couples game printable | 1 |
| cold case file | 1 |
| family game night printable | **0** |
| date night game printable | **0** |
| escape room printable game | **0** |
| sudoku printable | **0** |
| crossword puzzle printable | **0** |
| word search printable | **0** |
| scavenger hunt printable | **0** |
| would you rather printable | **0** |
| conversation cards printable | **0** |
| drinking game printable | **0** |
| christmas games printable | **0** |
| quiz printable | **0** |
| icebreaker game printable | **0** |

**This is not a seasonality artifact.** The evergreen categories — family game night, date
night, conversation cards, trivia, couples games — are the ones scoring flat zero. Nothing
was hiding behind Halloween.

### For scale, measured identically

| Reference category | W₆ |
|---|---|
| wedding invitation template | **160** |
| crochet pattern pdf | 140 |
| machine embroidery design | 31 |
| digital planner | 27 |
| cross stitch pattern pdf | 12 |
| **entire puzzle branch, best single category** | **8** |

The branch's ceiling is a quarter of machine embroidery and one twentieth of wedding
invitations.

### Why it fails

Printable games are cheap ($5–25), weakly differentiated, and compete against a large free
internet. Buyers browse rather than deep-search, so a new listing gets no discovery
foothold. The generation problem is genuinely tractable — that was never the issue. **The
engine would work; the market will not pay for it.**

---

## Measurement corrections made during this run

Two defects were found and fixed. Both were caught by controls, not by inspection.

1. **Wrong column.** Listing Age Max was set by screen coordinate, but the truncated header
   read `p Age` — it was **Shop Age**. An entire batch of zeros measured "shops younger than
   6 months", not listings. Invalidated and re-run.
2. **Read lag.** Counts were being read before the table refreshed, so each reading returned
   the *previous* category's value. Detected when a control returned 1 instead of 8.

**Fix:** measurement now runs in-page, hooks `fetch`/`XHR` to track in-flight requests, and
reads the count only after the network has been quiet for 1.5s.

**Validation:** two controls re-run after the fix — `cross stitch pattern pdf → 12` and
`murder mystery → 8`, the latter twice, both matching the values obtained independently
earlier. Earlier figures in `phase1-measured.md` are therefore corroborated, not suspect.

---

## The lead worth chasing instead

**Wedding invitation templates: W₆ = 160 — the highest measured anywhere, by 5×.**

Previously dismissed because the deliverable is an editable Canva template (manual studio
work per SKU). But the actual top listings are a different product:

- "Olive Green Save the Date **Website** Template | Digital Wedding Invitation with RSVP"
- "Sage Green and Ivory Wedding **Website** Template with RSVP and Countdown Timer"
- "Old Money Wedding **Website** Template with RSVP: Classic Digital Invitation"

**These are web pages.** A wedding website with RSVP, countdown and monogram is HTML/CSS —
which is fully generatable, unlike a Canva file. If a meaningful share of that W₆ = 160 sits
in the *website* sub-segment rather than the print sub-segment, it combines the highest
market openness measured with a genuinely automatable deliverable.

**Not yet verified.** Needs: the W₆ split for `wedding website template` specifically, how
those sellers deliver (hosted? Canva Sites? HTML zip?), and whether delivery can be
automated within Etsy's instant-download model. That is the next measurement.
