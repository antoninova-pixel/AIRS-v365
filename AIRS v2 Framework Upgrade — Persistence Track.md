# AIRS v2 FRAMEWORK UPGRADE — PERSISTENCE TRACK & EVENT TRACK

**Status:** DRAFT FOR FIELD TRIAL — effective next trading session · Supersedes nothing; runs in parallel with the v3.6.7 standard track · Origin: ULTJ case file (04–18 Sep 2026)

---

## §1 PHILOSOPHY

The standard track asks *"What is smart money doing?"* (foreign flow, broker sponsorship).
The Persistence Track asks *"What does someone already know — and how long have they known it?"*

Three laws:

1. **Persistence is a first-class signal.** A name that keeps appearing is itself evidence — regardless of which sensor sees it.
2. **AIRS has memory.** Evidence accumulates across sessions in the Persistence Board. No session starts from zero.
3. **Chase discipline governs entry price, never radar status.** A failed entry geometry defers a name with a written ladder — it never deletes it.

## §2 SENSORS & TRIGGERS (the 3-trigger counter)

Any ONE of the following fires the Persistence Counter on a name:

| # | Trigger | Threshold |
|---|---|---|
| T1 | **Board recurrence** | ≥3 appearances in the last 5 sessions on gainers and/or vol/val/freq boards |
| T2 | **Foreign streak alarm** | Net foreign buy streak ≥3 sessions with NO public news/disclosure on the name |
| T3 | **Insider print persistence (2-day rule)** | ≥2 consecutive sessions on the AI Strongest Insider Print screener |

A name that disappears from all sensors before reaching threshold = noise. No action, no log burden.

## §3 THE PERSISTENCE BOARD (standing state table)

Carried in every session-state file and updated at every SHORTLIST and EOD. Columns:

`Name · Days-on-board · NFB streak · Screener presence (FOR/INS) · State · WHY status · Ladder · First-flagged date`

**Legal states (exactly one per name, never silent):**
1. **WHY QUEUE** — trigger fired, investigation pending (max 2 sessions in queue)
2. **EVENT TRACK** — scored under §5, verdict live
3. **WATCH-DEFER** — gates passed but G5 geometry failed; pullback ladder WRITTEN and armed
4. **CUT (documented)** — reason logged; re-entry only on a fresh trigger

Silent exclusion of any triggered name is banned.

## §4 WHY DESK

### §4.1 Cadence (ruling: Option B)
- **On-trigger:** any T1/T2/T3 firing gets investigated at the next EOD.
- **Standing Friday sweep:** every Friday SHORTLIST reviews ALL sensor outputs, including day-1 names, to catch build-phase names early and pre-write ladders.

### §4.2 Investigation sequence (in order)
1. Ownership trail — insider 3M %, shareholders-count Δ, KPEI/ownership filings
2. Corporate-action calendar — RUPS agenda, PMHMETD/rights issue, inbreng, M&A, dividend declarations
3. Group/context patterns — parent moves, sector consolidation, related-party transactions
4. Tape cross-examination — value/volume build vs MA50 baseline (volume = lie detector)

### §4.3 Catalyst classification

| Tier | Catalyst | Consequence |
|---|---|---|
| Tier 1 | M&A / control change / rights issue with strategic investor / inbreng / asset injection | G7 full credit — Event Track MOD BUY eligible |
| Tier 2 | Special dividend, major contract, buyback, earnings setup | WATCH floor, re-review on new evidence |
| Tier 3 | Routine RUPS, minor filings, nothing found | CUT with documented reason |
| **Unknown** | Tape building, no hypothesis found | **G7 HALF CREDIT (ruling: Option A) — the tape itself is the evidence; MOD BUY eligible** |

## §5 EVENT TRACK SCORING

Standard-track gates and weights are untouched. Event Track uses its own architecture:

| Gate | Weight | Content |
|---|---|---|
| G1 Macro/Sector | 10% | Regime compatibility (lighter — idiosyncratic plays) |
| G2 Trend/Structure | 15% | Above MA20, base integrity, no breakdown |
| **G3E Persistence Evidence** | **30%** | NFB streak length · Bandar Acc/Dist · insider 3M% · shareholders Δ · RSR · value/volume build vs MA50 |
| G4 Momentum | 10% | SRSI/MACD — SRSI >95 pinned = automatic fail (blow-off block) |
| G5 Entry/R:R | 10% | Ladder anchored day-avg/week-avg; chase ≤2% rule unchanged |
| **G7 Catalyst Hypothesis** | **15%** | Tier 1 = full · Unknown = half · Tier 2/3 = zero |
| G6 modifier | ± | Demand-event modifier, unchanged |

**Verdicts:** MOD BUY ≥3.8 AND G7 ≥ half credit · WATCH 3.0–3.7 · AVOID <3.0.
**No HIGH BUY exists on the Event Track** — conviction caps at MOD BUY until news confirms.

## §6 SIZING & RISK LAW

- PERSONAL-ONLY ≤2%, 10% participation cap — always, every class label, no exceptions.
- Half probe on entry; second half only on tape confirmation (2nd Acc day or partial catalyst leak).
- Stop = LAW below the accumulation base.
- **Anti-trap rule:** accumulation can precede BAD news. Base breaks on volume before any news → exit at market, no arbitration.

## §7 LIFECYCLE

| Stage | Rule |
|---|---|
| News confirmed | Re-score on the STANDARD track same session — converts to flow trade (or exit if dilutive/sell-the-news) |
| Breakout fails post-news | Distribution-trap cell — exit next open |
| No news within 10 sessions | Probe expires at market; re-entry needs a fresh trigger |
| Catalyst lands Tier 2/3 | Downgrade review — WATCH or exit |

## §8 REPORTING INTEGRATION

- Quick Scan gains column **Track**: STD / EVT / EVT→STD.
- EOD Step 3 gains standing sub-block: **Persistence Board** (full table per §3).
- Event Track Detail Cards show **G3E + G7** in Gate Notes in place of standard G3 foreign evidence.
- Provenance tags standing: [INS] insider print · [FOR] foreign print · new **[BR]** board-recurrence tag.
- Cutlist format change: any cut of a triggered name must print its documented reason.

## §9 DAILY FLOW UNDER v2 (EOD-only protocol preserved)

**OLD:** MACRO → SHORTLIST → EOD → DETAIL CARD → SAVE

**NEW:** MACRO → SHORTLIST ⁺ → EOD ⁺ → DETAIL CARD → SAVE ⁺

No new daily commands. The upgrade folds into existing slots:

| Slot | v2 addition |
|---|---|
| **RUN AIRS SHORTLIST ⁺** | Persistence Counter update (T1/T2/T3 scan of uploaded boards/screeners) · Friday = standing sweep · outputs A/B/C triage + Persistence Board delta |
| **RUN AIRS (EOD) ⁺** | WHY desk investigations for WHY QUEUE names (§4.2) · Event Track scoring (§5) · Step 3 prints Persistence Board · verdicts carry Track column |
| **RUN AIRS DETAIL CARD** | Event Track cards use G3E/G7 gate notes · Track column on Quick Scan |
| **SAVE AIRS SESSION STATE ⁺** | Persistence Board written in full — this is the memory |

Quota cost: counter update = arithmetic on already-uploaded CSVs (free); WHY desk ≈ 1 short investigation per triggered name (bounded by the ≤4-name upload protocol).

## §10 FIELD-TRIAL CLAUSE

v2 runs as a live trial from the next trading session. Trial review after 10 sessions: count Persistence Board triggers, WHY outcomes, Event Track fills vs expiries, and any trap-cell losses. Thresholds (G3E 30%, G7 15%, 10-session expiry) are tunable at review — the five structural corrections (§1–§3) are not.

## §11 ULTJ RETRO-VALIDATION (the case that built this)

04–11 Sep: T1 fires (board recurrence day 3) → WHY QUEUE → 14 Sep: "news-driven rally" note = hypothesis on record → WATCH-DEFER with ladder at base 1,700–1,750 · 16 Sep: T2 fires (streak 6) → G3E strong, G7 ≥ half → **Event Track MOD BUY probe ≤2% in the base** → 18 Sep: news confirmed (FFI Rp14.57T inbreng, rights issue @2,150, FrieslandCampina control) → re-score on standard track.
**Result under v2: position captured during build phase, ~1,700s — not chased at RSI 85, not cutlisted.** Framework gap closed.
