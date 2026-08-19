# Etsy Digital Shop — Gameplan

> Living document. Status: **Phase 0, pre-account.** Last updated 2026-08-19.

---

## 0. North star

**Make money.** Not "build an impressive system." Every decision below gets judged against
revenue per hour invested, and the system exists only because it compounds better than
manual work does.

### Honest base rates

Most Etsy digital-download shops earn under $100/month and quit. The ones that don't
almost always have one of: a genuinely hard-to-copy product engine, an unusually good
niche read, or years of accumulated SEO. We are buying the first one. That is the entire
strategic bet.

### Targets and kill criteria

| Milestone | Target | If missed |
|---|---|---|
| Shop open, 15–20 listings live | Week 4 | Re-scope product engine; it's too complex |
| First sale | 30 days after listings go live | Diagnose: thumbnails first, then price, then niche |
| $100 cumulative revenue | Month 3 | Niche re-pick — run Phase 1 again with new data |
| $500/month | Month 8 | Decide: double down, pivot channel, or stop |

**Hard budget cap to first revenue: $150.** Detail in §8. If we pass that with zero sales,
we stop and re-plan rather than spending more.

---

## 1. Operating principles

1. **Claude is not the automation — Claude writes and operates the automation.**
   Anything that runs identically 500 times is a deterministic script. Anything requiring
   judgment is a Claude session. Never blur these; that's the standard failure mode.
2. **Judge on constraints, market on preference.** An LLM judge is reliable for "is this
   under 140 chars / does it contain the keyword / is the AI disclosure present / is the
   bundle complete." It is worthless at "which of these will sell." Only the market
   answers that.
3. **More SKUs in the market beats more generations in the simulator.** The market is the
   only evaluator that can't be gamed, and it evaluates for free.
4. **Rank, don't A/B.** With 0–5 sales per listing per month, significance testing is
   impossible. Ranking survives small samples; significance does not. See §6.
5. **Collect data before you need it.** Etsy keeps no history for us. See §6.1 — this is
   the single cheapest high-value thing in the plan.
6. **Gates are enforced by hooks, not by trust.** A model that can talk its way past a
   guardrail does not have a guardrail.

---

## 2. Identity decisions

### 2.1 Email — new dedicated account, not personal

**Decision: create a fresh Gmail (or Fastmail/Proton) for the shop before anything else.**

Reasons, in order of weight:

1. **Automation will need programmatic inbox access later.** Order notifications, review
   alerts, and post-purchase mail all land in this inbox, and Phase 5 reads it. You never
   point that at a personal inbox.
2. **The shop is a separable asset.** If it ever gets sold, transferred, or handed to a
   VA, the account goes with it cleanly.
3. **Blast radius.** A compromise or lockout on either account doesn't take out the other.
4. **Volume.** Etsy is a heavy sender. Don't pollute your personal mail.

**The address is deliberately brand-neutral, not brand-named.** Customers effectively never
see it — Etsy messaging is in-platform, and once the domain exists `hello@<brand>.com`
becomes the customer-facing address, forwarded here. So this inbox is pure infrastructure:
login, API notices, developer-portal mail. Keeping it neutral means it survives the naming
decision (§2.3) and can umbrella a second shop later without a new account.

**Chosen: `northbeamstudio@gmail.com`** (fallbacks: `quietforgestudio@`,
`openkilnstudio@`, `northbeamworks@`). Low-stakes by design.

At creation: enable 2FA and store backup codes offline, add recovery phone + recovery
email, and **do not use a `+alias` of the personal Gmail** — same account, defeats the
purpose.

### 2.2 Custom domain — register at name-lock (post-Phase 1)

**Decision: register the `.com` the same day the shop name is locked (~$12/yr), not before.**

Deferred because the domain should match the final brand, and the brand now waits for
Phase 1 (§2.3). Nothing in Phase 0 is blocked by its absence.

Register it then because:
- $12 protects the name across channels; rebranding later costs days.
- **The OAuth redirect URI must be `https://`** — a domain makes Seller App setup easier.
  *(Fallback if needed sooner: a free `*.workers.dev` Cloudflare Workers subdomain is
  HTTPS and satisfies the requirement.)*
- The Phase 5 webhook endpoint needs an HTTPS callback URL on a domain you control.
- A future off-Etsy channel (Gumroad/Payhip/own store) needs it, and that's where margin
  actually lives long-term.

Set up **Cloudflare Email Routing** (free) to forward `hello@<brand>.com` → the Gmail.
Add Gmail "send as" so replies come from the brand address. Keep the Gmail as the Etsy
account login — Etsy account emails are changeable, so this is low-risk either way.

### 2.3 Shop name — the hard constraint

Etsy rules (verified): **4–20 characters, letters and numbers only, no spaces, no
punctuation, unique, non-infringing.** Sources conflict on how many post-opening changes
are allowed (one vs. five), so **design as if you get zero.**

**Decision: defer the name until Phase 1 completes.**

The name is *not* required to create the Etsy account — the account is only a login. The
shop, and therefore the name, is created at the opening step, which requires a finished
product and is post-Phase 1 regardless. Deferring is a strict upgrade: a name chosen with
the niche in hand can carry SEO weight and thematic fit instead of being deliberately
meaningless. The email decoupling in §2.1 is what makes this free.

Lean warm rather than technical. Etsy's audience skews craft/home; a warm name over a
technical product reads fine, the reverse does not.

**Fallback shortlist** if Phase 1 produces no better niche-aligned candidate — `.com`
verified free 2026-08-19, **recheck before relying on it**, these expire from under us:

| Name | Chars | Read |
|---|---|---|
| **Loomwick** | 8 | Making/craft connotation, short, spellable. Top pick. |
| **Kilnvale** | 8 | Firing/making, broad, clean. |
| **Sorrelwick** | 10 | Botanical, distinctive, warm. |
| **Larchwick** | 9 | Botanical, clean, easy to spell. |
| **Arborwick** | 9 | Solid, slightly generic. |
| **Marlvale** | 8 | Neutral, quiet. |
| **Quillfen** | 8 | Leans paper/printable — mild niche lock-in, use only if that's acceptable. |

Etsy availability could not be checked programmatically (Etsy 403s bots). **The signup
form checks instantly and authoritatively** — check the top 3 there, in order.

Before locking: quick trademark sanity check on USPTO TESS / EUIPO eSearch. Coined words
are low-risk but the check is five minutes.

### 2.4 Branding — two stages, and the priority is not the logo

**The most important line in this section: on Etsy, the logo is hygiene; the listing
thumbnail is revenue.** Thumbnails drive click-through in search, click-through drives
views, views drive everything downstream. Do not spend two days on a logo.

**Stage 1 — Minimal viable identity (now, ~1 hour, no niche required):**
- Wordmark
- Shop icon (500×500)
- Shop banner
- 2–3 colour palette + one font pairing

Enough that the shop doesn't look abandoned at opening. Deliberately cheap and disposable.

**Stage 2 — The visual system (after Phase 1, when the niche is known):**
- Refined identity applied to the actual product category
- **`tools/mockups/` — a programmatic listing-image generator.** This is the real
  deliverable. It has to run 500 times with consistent output, so it is *code*, not a
  design file. Templates for: hero thumbnail, in-context mockup, feature callouts,
  size/contents chart, and a what-you-get summary card.
- Confirm exact current image dimensions from Etsy's spec page at build time rather than
  trusting cached numbers.

**Tooling:** `ui-ux-pro-max:design` for logo and banner generation; the `design` canvas
skill for iterating the visual system interactively. The thumbnail generator itself is
written as a normal script — a design tool can't be in the automated loop.

---

## 3. The sequencing constraint

**Opening a shop requires at least one finished listing.** So the dependency chain is:

```
email (neutral) → Etsy account → ID verification → bank/card ──┐
                                                               │
Phase 1 niche research (in parallel) → niche locked            │
                       ↓                                       │
        name locked + domain registered                        │
                       ↓                                       │
                 first product ←────────────────────────────────┘
                       ↓
             shop created + opens (fee paid)
                       ↓
        Seller App → API key → OAuth (needs https redirect)
                       ↓
             daily snapshot job starts  ← §6.1, do not delay
```

Two things must start immediately and in parallel: **account identity setup** (yours) and
**Phase 1 niche research** (mine). The first product is the gate on everything else.

---

## 4. Account setup runbook

### Yours (cannot be automated)

**Now:**
- [ ] Create dedicated email account — `northbeamstudio@gmail.com` or first free fallback
- [ ] Enable 2FA, save backup codes offline, set recovery phone + email
- [ ] Create Etsy account **from your normal home IP, no VPN**, with a real phone number
- [ ] Complete Persona ID verification (government ID + selfie) promptly
- [ ] Add bank account in your legal name + a card for fees
- [ ] Do *not* pay the setup fee / open the shop until product #1 exists

**After Phase 1:**
- [ ] Lock shop name — verify availability in the Etsy shop-creation form (authoritative)
- [ ] Trademark sanity check: USPTO TESS / EUIPO eSearch
- [ ] Register the matching `.com`
- [ ] Cloudflare Email Routing → forward `hello@<brand>.com` to the Gmail; add Gmail "send as"

> **Why the IP/VPN note:** new seller accounts on fresh emails are exactly the pattern
> Etsy's automated fraud detection targets. A suspension at signup is slow and painful to
> reverse. Look boring.

### Mine

- [ ] Phase 1 niche research (parallel subagents, scored rubric)
- [ ] Stage 1 brand assets
- [ ] Repo scaffolding, `CLAUDE.md`, gate config schema
- [ ] Etsy docs MCP wired up
- [ ] `tools/etsy/` CLI — OAuth + read-only commands first

---

## 5. Phases

**Phase 0 — Foundations.** Repo, CLAUDE.md, Etsy Dev MCP, OAuth (PKCE), read-only CLI
commands verified before any write path exists.

**Phase 1 — Niche selection.** 6–8 candidates researched by parallel subagents against a
shared rubric. Weighted heavily toward **generatability** — can a program produce unlimited
defensible variants from an input? Output: ranked table + generator sketch + build-cost
estimate per candidate, in `decisions/`. Human picks. EverBee bought for this phase.

**Phase 2 — The product engine.** The moat. Parameters → deliverable bundle (print-ready
PDFs at multiple sizes, source formats, preview PNG, README). Plus `tools/mockups/`.
This is where a large build is justified; everything else is plumbing.

**Phase 3 — Listing pipeline, human-gated.** `product-build` → `listing-create` → draft →
review summary → approve → publish. Idempotent, resumable, keyed on local SKU, with
rollback. **Launch 15–20 listings, not 200** — mass-publishing on day one is the
enforcement pattern.

**Phase 4 — The learning loop.** Daily snapshot cron + weekly analytics session producing
a decision doc. Rank-and-expand (§6). This is what makes it a business rather than a
listing dump.

**Phase 5 — Customer ops & scale.** `order.paid` webhook → HTTPS endpoint (Cloudflare
Worker or small VPS, HMAC-verified) → post-purchase email + review nudge. Message drafting
via skill, you send. Then: more variants, adjacent niches, second channel.

---

## 6. Selection & experimentation

### 6.1 Snapshot job — START THE DAY LISTING #1 GOES LIVE

Etsy's API exposes **no analytics endpoint** — no impressions, no visits, no time series.
`ShopListing` carries only *lifetime* `views` and `num_favorers`. Impressions and search
position are dashboard-only (manual CSV export).

Therefore: **poll listings daily, store the counters, difference them to build our own
time series.** If we don't, the data is gone forever and cannot be backfilled. ~30 lines
of code that determines whether Phase 4 has anything to reason about.

### 6.2 Signal inventory

| Signal | Volume/listing/month | Latency | Source |
|---|---|---|---|
| Views (differenced) | ~20–200 | 1 day | API snapshot |
| Favorites | ~1–10 | 1 day | API snapshot |
| Sales | ~0–5 | weeks | API receipts |
| Reviews | ~0–1 | weeks–months | API |
| Impressions / search position | — | — | dashboard only, manual |

### 6.3 Why not A/B testing

Distinguishing a 2% from a 3% conversion rate at reasonable power needs **thousands of
views per variant**. A new listing sees ~50/month. That test never finishes, and the
market moves under it. Sales are the truest signal and the most data-starved — that fact
shapes everything here.

### 6.4 What we do instead

- **Tier 1 — Fan-out + constraint check (day one).** Generate 8–10 candidates in parallel
  (titles, tags, thumbnails, niches), judge filters to the *valid* ones, market picks the
  winner. Best-of-N sampling, not evolution. Cheap, needs no statistics.
- **Tier 2 — Rank-and-expand at product-family level (Phase 4, highest value).** Monthly:
  rank all SKUs by blended score → top decile spawns variants along the winning dimension
  → bottom decile delisted or reworked. Track `parent_sku` + `generation` for lineage.
  Ranking is robust where significance testing is impossible.
- **Tier 3 — Bandits over fixed A/B.** Thompson sampling degrades gracefully at low
  volume; fixed splits don't. Never requires declaring significance.
- **Tier 4 — Evolving agent prompts.** Only legitimate target is the listing-copy
  generator, backtested against ≥50 listings of our own history. Months away. Low payoff.

### 6.5 What we explicitly avoid

Multi-generation agent tournaments with an LLM judge. The judge shares the generator's
blind spots, so it selects for *legibility to the judge*, not quality — Goodhart's law with
extra steps. A 20-agent × 5-generation run is 100 agent invocations; that budget buys a
year of EverBee plus a lot more SKUs, and SKUs generate real fitness data.

### 6.6 Schema additions

- `experiments`: hypothesis, variant, listing_id, start/end, metric snapshots, outcome, decision
- `products`: + `parent_sku`, `generation`
- **`fitness.py|ts`**: the blended score defined in code, not re-judged each week, so
  rankings stay comparable over time.

---

## 7. Guardrails

Autonomy model: **full auto after a proving period.** That must be built in from day one,
not retrofitted.

1. **Per-operation gate flags**, not a global switch — `publish` can graduate while
   `delete` and `price_change` stay gated permanently. Read from config by a PreToolUse
   hook so the model cannot argue past it.
2. **Audit log + rollback** on every write. Unattended publishing without one-command
   rollback is how a bug becomes 200 bad listings.
3. **Graduation criteria, agreed in advance:** publish gate lifts after ~50 listings with
   zero policy flags, zero malformed deliverables, and ≥1 clean weekly analytics cycle.
4. **Permanent circuit breakers:** auto-halt on any Etsy 4xx spike, any listing removal by
   Etsy, or any review below 4 stars.

### Policy compliance (non-negotiable, encoded in CLAUDE.md)

- AI disclosure ticked wherever generative AI meaningfully shaped output; attribution
  becomes **"Designed by"** not "Made by."
- Design must be original — a generator we wrote qualifies cleanly.
- Verify exact current disclosure wording in-browser before the first publish; Etsy's help
  pages block automated fetching and the wording has moved.

---

## 8. Cost model

Seller is resident in **Germany**. Numbers below are the German fee stack.

| Item | Cost | When |
|---|---|---|
| Gewerbeanmeldung | €15–70 (varies by Kommune) | Before first listing |
| Etsy one-time setup fee | $15–29 — **verify at signup, may not apply in DE** | At shop opening |
| Legal texts service (IT-Recht Kanzlei o.ä.) | ~€10/mo | Before shop opens |
| Domain | ~€12/yr | At name lock |
| Listing fee | $0.20 (~€0.18) each, renews every 4 months | Per listing |
| Transaction fee | 6.5% | Per sale |
| Payment processing (DE) | **4% + €0.30** | Per sale |
| Offsite Ads | 12–15%, **mandatory above $10k/yr** | Per attributed sale |
| EverBee Growth | ~€30 | **Phase 1 only — one month, then cancel** |
| eRank Basic/Pro | €6–10/mo | Phase 3 onward, ongoing |
| Webhook host | €0–5/mo | Phase 5 |

### 8.2 Research tooling — decided 2026-08-19

Two different jobs, two different tools:

- **EverBee (Phase 1, one month).** Revenue-per-listing estimates are the one input the
  Etsy API cannot provide and no competitor matches. Scores criteria 2 and 4 of the
  rubric. Cancel at niche-lock.
- **eRank (Phase 3+, ongoing).** Keyword research for listing SEO, at a third of the
  price. Better fit for the recurring job.
- **Sale Samurai — rejected** despite the deepest per-keyword data (CTR, Google CPC):
  **no CSV export.** A tool that only renders in a browser UI cannot feed this system.
- **Alura — not needed.** Overlaps both without beating either.

**Caveat on all of them:** sales figures are proxy estimates (reviews, favourites, scraped
sold counts), directionally useful and not accurate. Use them to **rank niches against
each other**, never to forecast revenue — same discipline as §6.3. Any "this niche does
€X/month" claim is suspect by construction.

**No public APIs exist** for any of these, so they remain a manual batch source: export
CSV → `data/exports/` → analyze. Never in the automated loop.

### 8.3 Market targeting — decided 2026-08-19

**Listings are written in English and priced for US buyers**, despite the seller being
German. Etsy's traffic is US-dominated, Etsy handles EU VAT for us automatically, and the
addressable market is several times larger. This feeds Phase 1 scoring: evaluate demand in
the US market, not the German one.

**Budget to first revenue: ~€250–300.** Higher than the US path because of registration
and legal texts. Still small; build time remains the scarce resource.

### 8.1 Pricing floor — derived from the German fee stack

The **€0.30 flat fee per transaction** is what kills cheap listings. Net after fees:

| List price | Fees (no ads) | Net | Fee % | With Offsite Ads (15%) |
|---|---|---|---|---|
| €3 | €0.62 | €2.38 | 20.5% | 35.5% |
| €5 | €0.83 | €4.18 | 16.5% | 31.5% |
| €10 | €1.35 | €8.65 | 13.5% | 28.5% |
| €20 | €2.40 | €17.60 | 12.0% | 27.0% |

**Rule: nothing prices below €10, target band €12–25.** Cheap digital items are a trap in
Germany — the flat fee plus a possible ads hit can take a third of a €5 sale. This also
pushes the product engine toward *bundles and higher-value deliverables* rather than
single cheap files, which should feed into Phase 1 scoring.

VAT note: Etsy adds VAT on top for EU buyers and remits it, so our list price is net —
no margin hit. Minor caveat: payment processing is charged on the gross incl. VAT, adding
roughly +0.8 percentage points to the effective rate.

---

## 9. Repo layout

```
etsy-shop/
  GAMEPLAN.md            # this file
  CLAUDE.md              # standing rules: voice, policy, pricing floor, gates
  .mcp.json              # etsy-docs MCP
  .claude/
    skills/              # niche-research, product-build, listing-create,
                         # sales-review, customer-reply
    agents/              # market-scout, listing-writer
    settings.json        # permission allowlist + gate hook
  tools/
    etsy/                # CLI: auth, listings, receipts, reviews, webhooks
    generator/           # THE PRODUCT ENGINE
    mockups/             # listing-image generator
  data/
    shop.db              # SQLite: products, listings, keywords, experiments, sales
    exports/             # EverBee CSVs, Etsy stats dumps
  products/              # generated sources + deliverable bundles per SKU
  decisions/             # dated markdown: what we tried, what happened, why
```

---

## 10. Germany — legal & tax setup

> Not legal or tax advice. These are the known requirements and the questions to bring to
> a Steuerberater. The Gewerbe/Steuernummer items have real lead time — start them early.

### 10.1 Registration — trigger is **niche-lock**, not now

Researching and building is *Vorbereitungshandlung*; the obligation attaches when
commercial activity begins — i.e. when we list and sell. So registration starts **the day
the niche is locked and the engine build begins**, which is optimal timing: the 2–8 week
Steuernummer wait then runs concurrently with the 2–4 week build rather than serially
after it. If Phase 1 finds nothing viable, nothing was spent and no IHK obligations were
incurred.

**Hard line: registered before the first listing goes live.** Not before the first line of
code, but not one day after publishing either.

1. **Gewerbeanmeldung** at the local Gewerbeamt, €15–70. Required *before* listing
   anything, since regular selling with profit intent is commercial activity.
   Side effect: IHK membership becomes mandatory (Grundbeitrag is typically waived for
   small Kleingewerbe in the early years, but confirm locally).
2. **Fragebogen zur steuerlichen Erfassung** via ELSTER → **Steuernummer in 2–8 weeks.**
   This is the long pole in the whole plan. Needed for invoicing.
3. **Kleinunternehmerregelung §19 UStG** — since 2025: €25,000 prior year /
   €100,000 current year. **Opt in.** Ticking "no" binds you to Regelbesteuerung for
   **five years** and cannot be reversed — do not check that box casually.
4. **USt-IdNr** — only if needed; the Impressum must list it *if you have one*.

### 10.2 VAT on digital items — mostly handled for us

**Etsy collects and remits VAT on automatically-downloaded digital items sold to EU
buyers**, regardless of where the shop is based. We do not add VAT to listing prices and
do not file VAT returns on those sales.

Question for the Steuerberater: how Etsy's deemed-supplier treatment interacts with the
Umsatzsteuervoranmeldung and EÜR under Kleinunternehmerstatus. Do not guess at this.

### 10.3 Legal texts — Abmahnung risk is real

Etsy provides form fields but **not** compliant German texts. Required: **Impressum, AGB,
Widerrufsbelehrung, Datenschutzerklärung**, in German.

- **Decision: subscribe to a legal-texts service** (IT-Recht Kanzlei or equivalent,
  ~€10/mo) with an Etsy-specific digital-content package and update service. Standard
  German practice and cheap insurance relative to one Abmahnung.
- **Digital content + Widerrufsrecht:** the buyer must expressly consent to immediate
  performance and acknowledge losing the right of withdrawal. Etsy has a function for
  this — verify it is enabled and correctly worded before the first sale.
- **Open risk to monitor:** the electronic Widerrufsbutton required from 19 June 2026
  (§ 356a BGB / EU 2023/2673). Etsy shipped a function on 30 June 2026 which
  IT-Recht-Kanzlei considers not fully compliant. Track this; keep our own texts current.
- **Privacy consideration:** the Impressum needs a ladungsfähige Anschrift — your home
  address becomes public unless you use a business-address service. Decide deliberately.

### 10.4 Sequencing consequence

Gewerbeanmeldung + Steuernummer must start **now**, in parallel with Phase 1, or the
2–8 week wait becomes the blocker exactly when product #1 is ready to publish.

---

## 11. Reference

- Etsy Dev MCP (docs only, no key): `https://mcp.api.etsycloud.com/mcp`
- Access level needed: **Seller App** — not Personal, not Commercial
- Webhook events available: `order.paid`, `order.canceled`, `order.shipped`, `order.delivered`
- **No messaging API in v3** — customer replies are drafted by Claude, sent by human
- Rate limits: per-API-key QPS/QPD, `x-remaining-today` header; irrelevant at our scale
