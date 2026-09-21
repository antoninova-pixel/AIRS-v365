# NOVA REPORT SPECIMEN v1.0
**Nusantara Alpha · EOD output format · Supersedes AIRS EOD Report Specimen v3.6.6**

**[FORMAT LOCK — PERMANENT STRUCTURAL REFERENCE. Governing change (owner ruling 20-Sep-2026): the EOD run executes the FULL 8-step framework INTERNALLY — Step 1 Macro · Step 2 Sector · Step 3 Broker + Persistence Board · Step 4 Technical + MYCD · Step 5 Standard + Event Track scoring · Step 6 Committee + Barbell · Step 7 Tracking · Step 8 Final Decision. Nothing is skipped; scoring quality is identical to the legacy written report. The WRITTEN OUTPUT presents the FINAL DECISION package ONLY: Persistence Board → Quick Scan → Detail Cards → Portfolio Allocation → Risk Monitoring → Entry Discipline. Internal steps are auditable on demand — the owner may request any internal step be surfaced for any name at any time, and fired actions (stops/trims/exits/cuts) are ALWAYS stated with full reasoning even in compressed mode. Format drift is a bug; re-issue on demand.]**

---

## CANONICAL OUTPUT STRUCTURE

**NOVA — Nusantara Alpha v1.0 | Report Date: [date] | Session: EOD (BINDING) | IDX · Swing 3d–6w**
**Regime: [call] · Holy Grail: [Y/N] · Calendar Risk: [status] · Next session: [date + notes]**
**Stress scenario: [active/none + one-line state] · §15.4 data-completeness flags: [any missing inputs, flagged before analysis]**

---

### BLOCK 0 — FIRED ACTIONS & ARBITRATIONS (always first when present)
Every stop/trim/exit/cut/arbitration resolved tonight, with full reasoning. Non-negotiable even in compressed mode.
*Example: "AMMN — HOLD—REDUCE arbitrated: BK −71.8B / ZP −36.9B (day 2) / AK −21.6B, NFF −147.8B, close −2.0% under day avg near day low = confirmed-distribution cell. Weekly ledger +92.3B keeps it HOLD not EXIT. Trim ½ (21 lots) at Friday open; remainder stop 4,800 LAW; 3rd consecutive Dist day = full exit. [FOREIGN] tag DEAD."*

### BLOCK 1 — PERSISTENCE BOARD (v2 — NOVA's memory)
| Name | Days-on-board | NFB streak | Screener (FOR/INS) | State | WHY status | Ladder | First flagged |
| --- | --- | --- | --- | --- | --- | --- | --- |
| [name] | [n] | [n] | [FOR/INS/BR] | WHY QUEUE / EVENT TRACK / WATCH-DEFER / CUT (documented) | Tier 1 / 2 / 3 / Unknown | [ladder or —] | [date] |
*Empty board prints "No active triggers." States are never silent. WATCH-DEFER names always carry a written ladder. CUT names always carry a documented reason.*

### BLOCK 2 — QUICK SCAN (ALL — BINDING)
| Stock | Score (Δ) | Verdict | Class | Signal | Foreign Flow | Anchor (day avg vs close) | Track |
| --- | --- | --- | --- | --- | --- | --- | --- |
| [name (+tags: [FOREIGN]/[INSIDER]/[BR]/MIDDAY-ORIGIN/PO)] | [score + arrow] | [chip] | [BIG CAP A/B / MED CAP C + ✅/❌] | [Acc/Dist/Mixed + evidence cell] | [flow] | [Day avg X — close Y = ±Z% (band verdict)] | STD / EVT / EVT→STD |
*Barbell-Positioning Rule note prints under the table whenever applied. Midday-origin confirmations/kills noted.*

### BLOCK 3 — DETAIL CARDS (12 locked rows each — all holdings + actionable names)
**TP1/TP2 convention:** upside % measured from Optimal/anchor — never from last close. Held positions: % from current anchor or legacy fill.

**[NAME]** — [tags]
| Field | Value |
| --- | --- |
| Verdict / Score | [chip + score / 5.0] |
| Entry Zone | Pullback [x] – Opt [x–y] – Acc [z] |
| Anchor | **Day avg [a] — close [b] = ±% (chase band valid/blocked + one-line tape read)** — mandatory explicit relation |
| Entry Quality | Optimal / Acceptable / Chased [at zone] |
| Size | **FULL / HALF** (+ Tier C probe ≤2% where applicable) |
| Service Eligibility | [class + ✅ Publishable / ❌ PERSONAL-ONLY + 10% cap] |
| Stop Loss | [level + LAW note] |
| TP1 / TP2 | [px (+X.X% from Opt [anchor])] / [px (+Y.Y%)] |
| Resolution Window | **FAST (3–7d) / SWING (2–6w) — TP1 = N.N× ATR([value]) from ladder** — ATR ALWAYS stated; omission = FORMAT VIOLATION |
| Thesis | [one-two lines; Event Track cards state G3E + G7 here] |
| Key Risk | [one line] |
| Re-eval | [date + trigger] |

### BLOCK 4 — PORTFOLIO ALLOCATION
| Position | Action | Exposure |
| --- | --- | --- |

### BLOCK 5 — RISK MONITORING CHECKLIST
- ☑ [event gates, stress tripwires, defense lines, distribution-day counts, standing debts]

### BLOCK 6 — ENTRY DISCIPLINE CHECKLIST
- ☑ All entries anchored to day-avg/week-avg ladders — never last price
- ☑ Chase ≤2% non-bull; Extended/Pursuit blocked
- ☑ Tier C = PERSONAL-ONLY + 10% cap printed on every card
- ☑ Barbell-positioning rule applied where relevant
- ☑ Smart Money evidence cell stated in every G3
- ☑ G5-failures deferred with ladders, never cut (v2)
- ☑ Events justify holds, never chases

**Closing line:** BINDING. + next expected command.

---

## WORKED MINI-EXAMPLE (17-Sep-2026, compressed)

**BLOCK 1 — PERSISTENCE BOARD**
| Name | Days | Streak | Screener | State | WHY | Ladder | First flagged |
| ULTJ | 10 | 9 | FOR | EVENT TRACK → STD review | Tier 1 CONFIRMED (FFI inbreng Rp14.57T + rights issue @2,150, FrieslandCampina control) | news out — re-score STD | 08-Sep (retro) |
*(Retro-annotation: under AIRS v3.6.7 this name was cutlisted 4×; under NOVA the T1/T2 triggers + G5-Defer Law would have held it with a base ladder.)*

**BLOCK 2 — QUICK SCAN row example**
| CUAN [MIDDAY-ORIGIN ✓] | 3.8 new | 🟢 MOD BUY | BIG CAP B ✅ | Acc — confirmed cell | NF +33.4B day | Day avg 940 — close 945 ≈ anchor (band valid) | STD |
| BBRI | 3.1 = | 🟡 WATCH | BIG CAP A | Mixed — barbell-capped | 1M +1,731.8B | Day avg 3,343 — close 3,330 ≈ anchor | STD |

**BLOCK 3 — card example (see 17-Sep EOD report for full set; Window row law: "FAST (3–7d) — TP1 = 1.7× ATR(54.3) from ladder")**

---

*Audit clause: any internal step (1–7) for any name is surfaced on request with no re-run — the analysis exists; only the presentation is compressed.*
