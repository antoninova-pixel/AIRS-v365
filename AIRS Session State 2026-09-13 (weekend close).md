# AIRS SESSION STATE — 2026-09-13 (WEEKEND CLOSE)
**Framework v3.6.5 + 13-Sep-2026 addendum** · Saved Sunday 13-Sep-2026, post MACRO WEEKLY + MACRO DAILY · Last binding engine: **EOD 11-Sep-2026** · Next IDX session: **Mon 14-Sep-2026**

---

## 0. FRAMEWORK VERSION & BOOT AMENDMENTS (13-Sep-2026 addendum)
- **7 commands** now: MACRO, SHORTLIST, MIDDAY, EOD, DEEP DIVE, SAVE SESSION STATE, **DETAIL CARD (g)**.
- **Input packs trimmed**: MIDDAY = 1H charts + 7-day broker summaries + foreign activity card 13:00 WIB only. EOD = daily charts + EOD broker summaries + calendar-today + journal screenshot only. CSVs + macro carried from MACRO/SHORTLIST runs.
- **HARD GATE (owner ruling 13-Sep): no same-day MACRO on record = EOD DOES NOT RUN.** Flag and stop; no provisional EOD, no exceptions.
- **Inv-holding reclass**: RMKE / WBSA / BULL = investment holdings outside the swing universe (◈) — Quick Scan listing only, no Detail Cards unless requested.
- **Rendering mandate**: Detail Cards via Python + Playwright ONLY (chromium CLI banned — repeated crashes 13-Sep). Light theme EN, ~1194px viewport, full-page capture, PIL trim. Output: `AIRS Detail Card [DD MMM YYYY] [EOD|MIDDAY] (EN light).png`.
- Boot rulings now a–e (e = DETAIL CARD product structure).

## 1. MACRO SNAPSHOT (MACRO DAILY 13-Sep, Friday 11-Sep finals)
- **Regime: S2 STRESS (softening)** — one clean session from NEUTRAL-BEAR reclassification, but FOMC gates any upgrade. Holy Grail eligible: **N**.
- Brent **104.47** (−2.94%, still closed >100 → 3rd-consecutive-close re-screen trigger CONDITIONALLY FIRED; day-count verification due Monday EOD) · WTI 99.99 (back under 100) · TTF −3.08%.
- VIX **15.84** (−11.21%; >20 escalation watch STOOD DOWN) · VIX futures 16.75.
- USD/IDR **17,607** (below 17,850 defense line) · DXY 99.087 flat pre-FOMC.
- US 10Y 4.975% / 2Y 4.644% (+2.07% front-end backup pre-FOMC) · **Indo 10Y 7.156% / 30Y 7.226% — still elevated**, funding-cost pressure persists.
- JKSE 6,541.38 (−0.73%, clawed back half the midday loss) · S&P +0.86% / Nasdaq +0.96% post-CPI risk-on · Nikkei −1.93% (BoJ pre-positioning) · HSI −0.60% / CSI300 −0.84%.
- Newcastle coal 146.75 (flat-soft) · Nickel 16,431.75 (−1.17%, mild ANTM headwind) · Gold 4,390 · CPO 4,814 (−1.45%).
- **Barbell (advisory): S1 45% / S2 25% / S3 30% — lean S1.**

## 2. CALENDAR GATES (binding until amended by EOD)
| Gate | Window (WIB) | Rule |
|---|---|---|
| **FOMC add-freeze** | Wed 16-Sep session → Thu 17-Sep 01:30 presser | No fresh adds without committee sign-off; pre-staged frozen-ladder limits exempt |
| Post-FOMC event hold | Thu 17-Sep full session | Discretionary exits allowed; new entries only on EOD-confirmed tapes |
| BoJ watch | Fri 18-Sep 10:00 (1.25% fcst vs 1.00%) | Carry-unwind tail risk; position-size caution Friday |
| CPI add-freeze | **EXPIRED by time** | Formal un-freeze decision still pending (flag 6) |
| BMRI / PSAB cum-dates | Cum Mon 15-Sep, ex Tue 16-Sep | No chase into cum-date strength; Tuesday strength = low-quality until tapes confirm |
| **Clean execution window** | **Mon 14 – Tue 15-Sep only** | Frozen ladders + EOD-confirmed names only, S2 sizing |

*FOMC decision Thu 17-Sep 01:00 WIB (corrected — state file's "15–16 Sep" was wrong). US Retail Sales Wed 19:30, Philly Fed/Claims Thu 19:30 also on watch.*

## 3. EOD 11-SEP ESSENTIALS (binding board)
**Quick Scan scores (binding):** PTBA **4.1** MOD BUY [FOR-confirmed] · TINS **3.9** (pubex G6 spent; 4,740 declared no-chase) · ERAA **3.8** (Tier C PERSONAL-ONLY) · ANTM **3.7** (day-tape crack flagged) · ENRG **3.4** WATCH half-weight (midday sponsorship confirmation DENIED — AK −17.1B Friday) · BBRI trigger 3,320–3,350 tagged intraday, **not closed = not qualified** · BUMI fill-pending · AMMN HOLD 3.0 lineage · RMKE HOLD 3.0 (◈) · INDY **EXIT 2.2** · WBSA / BULL EXIT (◈).
**Barbell printed on card:** S1 45/S2 25/S3 30, lean S1. Detail Card product shipped: `AIRS Detail Card 11 SEP 2026 EOD (EN light).png`.

## 4. PORTFOLIO (lots/avg/stops/override flags)
| Name | Status | Stop / Floor | Notes |
|---|---|---|---|
| **AMMN** | HOLD — core metal | **4,640 LAW** (zero patience, day 3) | Weekly AK +168B base vs domestic-carried tape; TP 5,250/5,400; 3rd approach of 4,640 likely breaks — stop check is the decision |
| **RMKE** | HOLD (◈ inv-holding, personal) | **396 LAW** (Friday low 406: 10pt margin) | 230 @ 436; thin tape, no sponsorship; held by stop discipline only |
| **BUMI** | **Presumed filled — journal confirm Monday** | per ladder | Real foreign money Friday (coal complex) |
| **INDY** | **EXIT — VARIANT B CONFIRMED (owner decision 13-Sep, logged P8)** | **Replacement hard floor 2,770 (Friday low) — LAW** | ½ market Mon open · ½ limit 2,880–2,910 (Friday supply shelf); unfilled limit expires EOD Tue 15-Sep → market Wed open. BK −9.6B / AK −9.2B 5-star distribution; sell-the-bounce, not a hold. INDY does not survive Wednesday |
| **WBSA / BULL** | Exits executing (◈) | — | Fill reports due Monday |

## 5. ACTIVE LADDERS / TRIGGERS (live Mon–Tue clean window, S2 sizing)
- **ANTM** probe 3,150–3,180 — ⚠️ day-tape crack: CC −34.3B / AK −26.9B Friday; **2nd consecutive CC/AK sell day Monday = [FOR] strip + name-level add-freeze**. Warrant ANTMDRCZ6A (strike 4,570) now live — sentiment side-signal only.
- **PTBA** frozen ladder — [FOR]-confirmed, flow-driven (not commodity-driven).
- **UNTR** frozen ladder. **POWR** frozen ladder — 995 declared no-chase.
- **TINS** frozen — 4,740 declared no-chase; thesis sits with [FOR]-confirmed flow, not calendar.
- **BMRI** ladder 4,280–4,320 **post-ex-date only** — no cum-date chase (cum Mon, ex Tue; Rp 66 div, 10.94% carry thesis).
- **ERAA** personal probe ≤2% on 575–585 retest — Tier C, 10% participation cap.
- **ENRG** — NO entry; AK/BK Monday tape = binary re-qualification. Warrant ENRGDRCH7A strike 2,040 (above TP2 1,650 — supportive color, no score impact).
- **BBRI** — NO entry; close ≥ 3,320–3,350 re-check Monday.
- **Oil re-screen (flag 5)**: if Brent 3rd-consecutive >100 close confirmed Monday → re-screen **MEDC / PGAS / ELSA / AKRA / ESSA** (warrant-noise caveat: whole complex issued structured warrants 11-Sep — G3 reads need warrant-flow awareness). WTI <100 + TTF −3% argue trigger is weakening.
- Chase discipline: Standard ≤2% above anchor (S2); Extended/Pursuit blocked.

## 6. PROVENANCE REGISTER
TAPG **[BND]** (thesis review disposition OWED by owner) · BBRI **CONFLICT** · PTBA **[FOR]** · TINS **[FOR]-confirmed** · ANTM **[FOR] conditional** (Monday tape check) · ENRG midday-origin provisional — confirmation DENIED at EOD.

## 7. OPEN FLAGS (carried to Monday 14-Sep)
1. **Journal reconciliation** (WBSA/BULL/INDY/BUMI fills; TAPG 0-lot "missed buy" row) — gates track-record update. Mandatory Monday.
2. Brent consecutive-close count → oil re-screen decision (Monday EOD).
3. ANTM Monday tape: 2nd CC/AK sell day = [FOR] strip + add-freeze.
4. ENRG AK/BK Monday tape = binary re-qualification.
5. BBRI close ≥3,320–3,350 check.
6. CPI add-freeze formal un-freeze decision (expired by time; paperwork).
7. BMRI/PSAB ex-date Tuesday — tape-quality distortion.
8. BoJ Friday 10:00 — carry-unwind tail.
9. FOMC Thu 01:00 + presser 01:30 — add-freeze from Wednesday session.
10. USD/IDR 17,607 below defense line; Indo 10Y 7.156% elevated — residual stress legs.

## 8. TRACK RECORD
**12W / 5L / 1F** — frozen pending Monday journal reconciliation (flag 1).

## 9. MONDAY 14-SEP SEQUENCE
1. First session opens with **Week-Ahead Brief (table-only)** from the Sunday archive.
2. **Journal reconciliation** before any track-record update.
3. **INDY Variant B executes**: ½ market at open; ½ limit 2,880–2,910; floor 2,770 law.
4. WBSA/BULL fill reports; BUMI fill confirmation.
5. Tape checks: ANTM (CC/AK), ENRG (AK/BK), BBRI (close vs trigger).
6. EOD 14-Sep (requires same-day MACRO first — HARD GATE): Brent close count, oil re-screen if confirmed, CPI un-freeze formal decision, regime reclassification review (one clean session → NEUTRAL-BEAR, FOMC-gated).

*Standing owner rulings (state-file + boot a–e) confirmed and locked. Self-audit against the specimen section-by-section before every shipment; deviations flagged, never silent. "FORMAT VIOLATION" → full re-issue, no debate.*
