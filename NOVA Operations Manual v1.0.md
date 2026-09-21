# NOVA OPERATIONS MANUAL v1.0
**Nusantara Alpha · Indonesia Stock Exchange (IDX/JCI) · Swing horizon 3 days – 6 weeks**
NOVA = "Nusantara Alpha" — a system designed to generate market-beating returns on the JCI. NOVA v1.0 supersedes the AIRS lineage (final AIRS version: v3.6.7) in full, incorporating the v2 Framework Upgrade (Persistence Track & Event Track). Companion files: the latest *NOVA Session State* (§3C truth file) and *NOVA v2 Framework Upgrade — Persistence Track* (origin spec). On conflict: **file > chat memory; Manual > Session State on procedure; Session State > everything on positions.**

## §1. Command Architecture (seven commands)
| # | Command | Inputs | Authority | End product |
| --- | --- | --- | --- | --- |
| a | RUN NOVA MACRO | MACRO DAILY variant: macro dashboard images + econ calendar (today). MACRO WEEKLY variant: econ calendar (this week + upcoming) + full corporate action calendar archive | Advisory layer | Regime call, stress watch, calendar gates, barbell inputs |
| b | RUN NOVA SHORTLIST | Watchlist column pages + Top Gainer CSV + Top Val/Vol/Freq CSV + sensor outputs (foreign print / insider print) | Triage only, no scoring | Short List (≤10) + Cut List + **Persistence Counter update** |
| c | RUN NOVA MIDDAY | 1H charts + 7-day broker summaries + midday CSVs + midday macro + foreign activity card | Active checker, provisional | **SUSPENDED — see §4** |
| d | RUN NOVA [date] | Daily charts + EOD broker summaries + EOD CSVs + macro + journal screenshot | **Authoritative** | Full 8-step EOD report, binding scores |
| e | RUN NOVA DEEP DIVE [X] | 1D + 1W + 1M charts + D/W/M broker summaries | Binding (single name) | Full 8-step single-stock report + Detail Card |
| f | SAVE NOVA SESSION STATE | All confirmations + journal + **Persistence Board** | Persistence layer | §3C state file |
| g | RUN NOVA DETAIL CARD [date] | Locked score board (post-EOD) — never invents scores | Render layer (BINDING post-EOD) | Client-facing PNG per §11.8 locked template |
Ad-hoc discipline questions are always legal without a full report; answers cite framework law. **Intraday distress consults (owner ruling 20-Sep-2026):** while MIDDAY is suspended (§4), if any morning-bought position falls intraday, the owner may ask a text-only what-to-do consult (price + position) at any time; the analyst answers with a 3-line addendum (hold / trim / exit + reason + level). Stops remain LAW and execute without the analyst.

## §2. RUN NOVA MACRO
Two scheduled variants of one command:
* **MACRO DAILY** (weekday evenings, ~21:30 WIB): global indices (US futures, Asia), US/Indo yield curve, USD/IDR + 17,850 defense line, DXY, VIX, Brent/WTI (S2 tripwire 100), gold/silver/copper/nickel, CPO, Newcastle coal, crypto (context only), Investing.com calendar TODAY tab, Stockbit calendar TODAY page, news events.
* **MACRO WEEKLY** (Sunday ~12:30 WIB): Investing.com economic calendar THIS WEEK tab + all 11 Stockbit calendar pages captured and stored as the week's archive. **Archive rule:** a calendar page is analyzed ONLY when a holdings/watchlist/shortlist name matches a corporate action; otherwise acknowledged and archived without analysis.
* **Midday macro** (12:30 WIB): dormant while MIDDAY is suspended.

Outputs: regime verdict (BULL / NEUTRAL / NEUTRAL-BEAR / BEAR), Holy Grail eligibility Y/N, stress scenario status (S1/S2/S3 with two-confirmation rule), calendar gates, barbell scenario set. **Sector rotation review:** "Ekosistem Data Center" is a standing sub-sector — land/estates (DMAS, SSIA, KIJA, AKRA) · operators (DCII, EDGE, TLKM, ISAT, EXCL) · power/backup (POWR, PGAS, UNTR) · cabling (SCCO, KBLI, VOKS, JECC, KBLM) · fiber/towers (TOWR, TBIG, MTEL, DNET) · EPC (TOTL, NRCA, PPRE). If no fresh MACRO run exists, the saved snapshot governs; staleness >1 session is flagged in the report header.

**Index Rebalancing / Index Flow Theory:** standing watch layer inside MACRO.
* **Review calendars:** MSCI — Feb / May / Aug / Nov (highest priority, incl. MSCI EM) · FTSE GEIS — Mar / Jun / Sep / Dec · LQ45 & IDX80 — reviews Jan→Feb and Jul→Aug.
* **Alert rule:** watch the announcement month ahead; the alpha window runs announcement → execution. MACRO flags any roster name entering an index-flow window; G6 may credit expected passive demand, never retroactively after implementation.

**Monday Week-Ahead Brief:** Monday's first session opens with a table-only brief from the Sunday archive — macro events, corporate actions matching holdings/watchlist, cum dates. No deep analysis.

## §3. RUN NOVA SHORTLIST — union screening + Persistence Counter
**Universe** = screener result list ∪ Top Gainer board ∪ Top Val/Vol/Freq board, deduplicated. The scanner must surface qualified names absent from the screener list.
**Output:** Short List (hard cap 10 new candidates; selection by committee judgment with written reasoning) + Cut List (every rejected name + one-line reason + the lane/gate that failed — permanent audit trail) + **Persistence Counter update (§3A)**. Known-blacklisted names skip triage → Cut List "blacklist." No early trimming below the cap. **Holdings auto-shortlist on top of the 10** and are never displaced.
**Precision clause:** the shortlist is NEVER trimmed to save cost. Cap management happens only through committee judgment on quality.

**§3A. PERSISTENCE COUNTER (v2 Framework Upgrade).** At every SHORTLIST, three triggers are scanned across the uploaded boards/screeners:
* **T1 Board recurrence** — ≥3 appearances in the last 5 sessions on gainers and/or vol/val/freq boards.
* **T2 Foreign streak alarm** — net foreign buy streak ≥3 sessions with NO public news/disclosure on the name.
* **T3 Insider print persistence (2-day rule)** — ≥2 consecutive sessions on the AI Strongest Insider Print screener.

Any trigger fires the name onto the **Persistence Board** (§3B). A name that disappears from all sensors before threshold = noise.
**Standing Friday sweep (owner ruling 20-Sep-2026):** every Friday SHORTLIST reviews ALL sensor outputs including day-1 names, to catch build-phase names early and pre-write ladders.

**§3B. PERSISTENCE BOARD (NOVA's memory).** Standing table carried in the session state, updated at SHORTLIST and EOD. Columns: `Name · Days-on-board · NFB streak · Screener presence (FOR/INS) · State · WHY status · Ladder · First-flagged date`. Legal states — exactly one per name, never silent:
1. **WHY QUEUE** — trigger fired, investigation pending (max 2 sessions)
2. **EVENT TRACK** — scored under §7B, verdict live
3. **WATCH-DEFER** — gates passed but G5 geometry failed; pullback ladder WRITTEN and armed
4. **CUT (documented)** — reason logged; re-entry only on fresh trigger

**Silent exclusion of any triggered name is banned.**
**G5-Defer Law (v2 core):** chase discipline governs ENTRY PRICE, never RADAR STATUS. A name passing flow/trend gates but failing entry geometry goes to WATCH-DEFER with a ladder — never to the Cut List. Only flow failure, trend failure, or a documented Tier-3 WHY earns a cut.

## §4. RUN NOVA MIDDAY — SUSPENDED (owner ruling 20-Sep-2026)
MIDDAY is **on hold — not abolished**. Suspension is an operating-mode decision; the full MIDDAY specification below remains law and is resumed on owner command after NOVA go-live stabilization.
**Design rationale for eventual resumption (INDY case, 10-Sep-2026):** a morning buy met midday foreign selling the same day; MIDDAY caught it, but the exit was not executed same-session and the loss grew past 2%. Resumed MIDDAY exists to convert that early catch into a same-day exit while losses are small. Until resumption, intraday protection runs via §1 distress consults + broker-app price alerts; stops are LAW and execute without the analyst.
**Standing spec (dormant, unchanged):** MIDDAY executes the full 8-step framework internally with compressed Step-8-only output (provisional Quick Scan + 12-row Detail Cards), one-line audit trail per score change, fired actions stated in full, midday-origin catches flagged "EOD confirmation required," power to fire stops/exits/trims intraday. EOD remains the binding record (§6).

## §5. RUN NOVA [date] — EOD, authoritative
Inputs: daily charts + latest EOD broker summaries + EOD CSVs + EOD macro + Investing.com calendar-today + **journal screenshot for holdings/fills reconciliation**.
Full 8-step report under §11 format lock: Step 1 Global Macro · Step 2 Sector Rotation · Step 3 Broker Analysis **+ Persistence Board sub-block (§3B)** · Step 4 Technical + MYCD · Step 5 5-Gate+G6 Scoring **(+ Event Track scoring §7B for Persistence Board names)** · Step 6 Committee Deliberation (+ §11.6 Barbell when gates/stress active) · Step 7 Tracking vs Prior Reports · Step 8 Final Decision (Layer 1 Quick Scan **with Track column** + Layer 2 Detail Cards + Portfolio Allocation + Risk Monitoring + Entry Discipline checklists).
**WHY DESK (v2):** runs inside EOD for every name in WHY QUEUE. Investigation sequence: ① ownership trail (insider 3M%, shareholders Δ, KPEI filings) → ② corporate-action calendar (RUPS, PMHMETD/rights issue, inbreng, M&A, dividends) → ③ group/context patterns → ④ tape cross-examination (value/volume build vs MA50 baseline; volume = lie detector). Catalyst classification:

| Tier | Catalyst | Consequence |
| --- | --- | --- |
| Tier 1 | M&A / control change / rights issue with strategic investor / inbreng / asset injection | G7 full credit — Event Track MOD BUY eligible |
| Tier 2 | Special dividend, major contract, buyback, earnings setup | WATCH floor, re-review on new evidence |
| Tier 3 | Routine RUPS, minor filings, nothing found | CUT with documented reason |
| Unknown | Tape building, no hypothesis | **G7 half credit (owner ruling 20-Sep-2026, Option A) — the tape itself is the evidence; MOD BUY eligible** |

## §6. Authority & Contradiction
* **EOD Authority Rule:** EOD scores are binding for the track record; intraday downgrades hold until EOD confirms or reverses them.
* **Contradiction Rule:** a probe contradicted by EOD broker data → exit at next open.
* **Stop-Override Protocol:** a fired stop is executable law. Sole exception: explicit owner decision + replacement hard stop, logged to P8. Any close below the replacement stop = market exit without discussion.

## §7. Scoring — STANDARD TRACK (untouched)
G1 Macro/Sector 20% · G2 Trend 20% · G3 Flow 25% · G4 Momentum 15% · G5 Entry/R:R 20% · G6 Demand Event modifier −0.5 to +1.0 (never rescues failed G3).
Verdicts: 🟢 HIGH BUY 5.0 · 🟢 MOD BUY 4.0–4.5 · 🟡 WATCH 3.0–3.5 · 🔴 AVOID <3.0 · 🔵 HOLD · 🔴 EXIT.
**Barbell-Positioning Rule:** a stock whose sector is classified as a Loser / unfavorable leg by the current Macro Scenario Barbell is capped at 🟡 WATCH on the Quick Scan regardless of score ≥3.8. Score still computed and shown; verdict capped until the barbell reclassifies. Held positions unaffected.

## §7B. Scoring — EVENT TRACK (v2, parallel system)
For Persistence Board names only. Standard track is untouched; a name may hold scores on both tracks.

| Gate | Weight | Content |
| --- | --- | --- |
| G1 Macro/Sector | 10% | Regime compatibility (lighter — idiosyncratic plays) |
| G2 Trend/Structure | 15% | Above MA20, base integrity, no breakdown |
| **G3E Persistence Evidence** | **30%** | NFB streak length · Bandar Acc/Dist · insider 3M% · shareholders Δ · RSR · value/volume build vs MA50 |
| G4 Momentum | 10% | SRSI/MACD — SRSI >95 pinned = automatic fail (blow-off block) |
| G5 Entry/R:R | 10% | Ladder anchored day-avg/week-avg; chase ≤2% rule unchanged |
| **G7 Catalyst Hypothesis** | **15%** | Tier 1 = full · Unknown = half · Tier 2/3 = zero |
| G6 modifier | ± | Demand-event modifier, unchanged |

**Verdicts:** MOD BUY ≥3.8 AND G7 ≥ half credit · WATCH 3.0–3.7 · AVOID <3.0. **No HIGH BUY exists on the Event Track** — conviction caps at MOD BUY until news confirms.
**Sizing & risk law:** PERSONAL-ONLY ≤2% + 10% participation cap, always, every class. Half probe on entry; second half only on tape confirmation (2nd Acc day or partial catalyst leak). Stop = LAW below the accumulation base. **Anti-trap rule:** base breaks on volume before any news → exit at market, no arbitration.
**Lifecycle:** news confirmed → re-score on STANDARD track same session (converts to flow trade, or exit if dilutive/sell-the-news) · breakout fails post-news → distribution-trap cell, exit next open · no news within 10 sessions → probe expires at market, re-entry needs fresh trigger · catalyst lands Tier 2/3 → downgrade review.

## §8. Lanes & Provenance
Nine-lane screener stack. **Lane 8 Insider Print [INS]** · **Lane 9 Foreign Print [FOR]** · **[BND]** bandar-proxy · **[BR] board recurrence (v2, new)**. Tags print on Quick Scan rows and Detail Card titles. Provenance ≠ score; a tag is stripped when its sponsoring print flips, triggering thesis review. Quick Scan carries the **Track column** (STD / EVT / EVT→STD).

## §9. Broker Tiers
Foreign 5-star: AK (UBS), BK (JPM), RX (Macquarie), DX (UBS alt). Domestic institutional: CC, BB, MG, CP, YU; ZP = bandar proxy. Retail: XL, PD, YP, SQ, XC. Retail-carried tapes with institutional selling fail G3.
**Smart Money / Broker Summary Theory:**
* **Core principle:** Broker Summary = claim; Price Action + Volume = evidence.
* **Evidence matrix:** Net Sell + price holds = possible hidden accumulation (probe-grade, verify). Net Buy + price rises = buying confirmed (full G3 credit). Net Buy + breakout fails = possible distribution / retail trap (G3 capped, contradiction watch).
* **Volume = lie detector:** claims without confirming volume are unverified; volume against the claim downgrades it.
* G3 scoring must state the evidence-matrix cell; unverified claims score the cautious half of the flow band.

## §10. Entries, Exits, Risk
* **Entry ladder:** Pullback – Optimal – Acceptable, anchored to POC / day-avg / week-avg — never last price.
* **Chase discipline:** Standard ≤2% above anchor (non-bull); Extended +2–5% only under bullish macro/Holy Grail; +8% hard ceiling. **G5 failures defer (§3B), never cut.**
* **Liquidity-as-Attribute:** BIG CAP A ≥500B/day · BIG CAP B 100–500B · MED CAP C <100B = PERSONAL-ONLY probe ≤2%, 10% participation cap.
* Value <5B/day = log only, no probe.
* **Execution-Gated Carry-Over:** unfilled ladders expire at their window unless re-armed.
* **Resolution Windows:** FAST 3–7d / SWING 2–6w with ATR reachability check — **ATR must always be stated (§11.8 law).**
* **TP/SL convention:** TP1/TP2 upside % from anchor/optimal entry; stops close-based unless stated.
* **Events justify holds, never chases.**
* **Blacklist:** unquantifiable legal/governance risk skips triage.

## §11. Format Lock (permanent)
The locked EOD specimen (with all amendments) is the permanent structural reference: same tables, fields, column sequences, every session. Includes: canonical header + regime/stress lines; Step 1–8 structure; §11.6 Macro Scenario Barbell closing Step 6 when calendar/stress active (advisory — never changes scores/verdicts/sizing); 12-row Detail Cards for ALL holdings + actionable names; TP%-from-anchor convention block under Layer 2; provenance tags + Track column; Persistence Board sub-block in Step 3. Format drift is a bug; re-issue on demand.
**§11.7 DEEP DIVE:** full 8-step single-stock adaptation on D/W/M charts + D/W/M broker summaries, ending in the 12-row Detail Card with binding score.
**§11.8 DETAIL CARD client-facing template (locked):**
1. **Header** — title + framework/version line + regime + barbell split · BINDING / PROVISIONAL stamp · gate banners.
2. **Quick Scan (ALL)** — full board: Stock(+tags) / Score (delta arrows) / Verdict / Class / Signal / Foreign / **Anchor (day-avg vs close, explicit)** / **Track (STD/EVT/EVT→STD)**. Midday-origin names carry amber chips.
3. **Top Buys** — BUY + MOD BUY only, best 3–4, HARD MAX 5, held names routed to Holdings. Green-header 12-row cards, TP% from Optimal/anchor, NO-CHASE row on every card, frozen-ladder stamps.
4. **Holdings & Requested** — blue-header HOLD cards incl. EXIT variants; "Stops are LAW" row. Tier C cards carry red PERSONAL-ONLY chip.
5. **Macro Scenario Barbell** — leg / weight / expression / evidence / action-bias + Winners / Losers / Pivot-triggers strip; advisory-only.
6. **Footer** — framework law lines on navy bar.
**Detail Card field law (owner rulings, permanent):**
* **Anchor row (permanent):** must state the day-avg vs close relationship explicitly — e.g. *"Day avg 3,883 — close 3,890 ≈ anchor (chase band valid/blocked)."*
* **Resolution Window row (permanent, owner ruling 20-Sep-2026):** must always state the ATR figure with the reachability check — e.g. *"SWING (2–6w) — TP1 = 2.1× ATR(700) from ladder."* An omitted ATR is a format violation.
* Locked 12 rows: Verdict/Score · Entry Zone · Anchor · Entry Quality · Size · Service Eligibility · Stop Loss · TP1/TP2 · Resolution Window · Thesis · Key Risk · Re-eval. Event Track cards show G3E + G7 in Gate Notes.
**Client-facing language rules:** class labels BIG CAP A / BIG CAP B / MED CAP C (animal icons retired client-facing) · sub-5B daily value rendered in plain language · RMKE/WBSA/BULL = investing holdings, Quick Scan only unless requested · Tier C stamps (PERSONAL-ONLY + 10% participation cap).
**Render protocol (permanent):** Python + Playwright ONLY (chromium CLI banned) · light-theme EN (light grey / light blue shell, navy header/footer — owner ruling 17-Sep-2026) · 1194px full-page screenshot · PIL trim · output `"NOVA Detail Card [date] [EOD|MIDDAY] (EN light).png"`. Post-EOD = BINDING stamp. Never invent scores — render the locked board.

## §12. Session State (§3C)
SAVE NOVA SESSION STATE persists: macro snapshot, latest EOD essentials, holdings (lots/avg/stops/override flags), active ladders/triggers, **Persistence Board in full (v2 — this is NOVA's memory)**, open flags, track record, framework version. File wins over chat memory. **Session protocol:** consecutive trading days may run in ONE chat session (MACRO → SHORTLIST → EOD → SAVE per day) with no re-boot while the chat lives; the §3C file remains the fail-safe. Full re-boot mandatory on framework version change.

## §13. Reviews & Audits
* **P7** ladder-discipline review (weekend).
* **P8** deviation review (weekend): chase violations, non-executed stops, override log.
* Cut List audit: triage tightness check — **now includes Persistence Board misses (any CUT name that later triggered T1/T2/T3 is reviewed against its documented cut reason).**
* Track record kept from the journal (authoritative for W/L).
* **v2 field-trial review (after 10 sessions):** count Persistence Board triggers, WHY outcomes, Event Track fills vs expiries, trap-cell losses. Thresholds (G3E 30%, G7 15%, 10-session expiry) tunable at review; the structural corrections (§1 distress consults, §3A/§3B, §7B) are not.

## §15. Data Operations
**§15.1 MotionTrade CSV protocol.** Ranking boards exported as CSV, never screenshotted. Columns: Code, Last, Change, Prev, Open, High, Low, Freq, Vol, Val(K), Cap(M). Units: **Vol = lots · Val(K) = thousand rupiah · Cap(M) = million rupiah · Change = % vs previous close**. Full 761-ticker universe, pre-sorted. Midday→EOD deltas computed when both snapshots exist. In-file code screening preferred over additional screenshots.
**§15.2 File naming & archive.** `YYYY-MM-DD_[slot]_[dataset].csv` — slots: midday / eod; datasets: gainers / volvalfreq.
**§15.3 Daily capture schedule (WIB).**
* **MIDDAY (12:15–13:00):** suspended while §4 holds (owner captures foreign-activity image + sensor outputs ad hoc for the Persistence Counter).
* **EOD (21:15–21:30):** gainers + volvalfreq CSV · watchlist image · EOD macro image · calendar-today image · D charts + broker summaries (holdings + A-band ≤4 + foreign-card-flagged names) · journal screenshot.
* **SUNDAY (12:30):** MACRO WEEKLY archive per §2.
* **DEEP DIVE:** on request only.
**§15.4 Data completeness gate.** On each data drop, the analyst acknowledges receipt, checks completeness against §15.3, and flags any missing item BEFORE running analysis. No re-runs unless data was actually missing.

## §14. Changelog
* **NOVA v1.0 (20-Sep-2026)** — System renamed **NOVA — "Nusantara Alpha"** (AIRS lineage closed at v3.6.7). v2 Framework Upgrade patched in: Persistence Counter (T1/T2/T3, §3A) · Persistence Board + legal states + G5-Defer Law (§3B) · WHY Desk + catalyst tiers + Unknown half-credit ruling (§5) · Event Track scoring G1 10/G2 15/G3E 30/G4 10/G5 10/G7 15 with sizing & lifecycle law (§7B) · Track column + [BR] tag (§8) · Persistence Board in session state (§12) · Persistence-miss audit (§13). MIDDAY suspended as operating mode with INDY-case resumption rationale (§4); intraday distress consults added (§1). Detail Card law: ATR statement in Resolution Window row made permanent (§11.8). Origin case: ULTJ (04–18 Sep 2026).
* **v3.6.7** — Barbell-Positioning Rule; Smart Money / Broker Summary Theory (§9); Index Rebalancing / Index Flow (§2); Anchor row day-avg-vs-close ruling.
* **v3.6.0** — TP%-from-anchor convention; [INS]/[FOR] tags.
* **v3.6.1** — §11.6 barbell block.
* **v3.6.2** — Execution-Gated Carry-Over; contradiction rule formalized.
* **v3.6.3** — MACRO command; union-screening SHORTLIST; MIDDAY active checker; DEEP DIVE full 8-step; permanent format lock; [BND]; stop-override protocol.
* **v3.6.5** — Data Operations layer (§15); MACRO DAILY/WEEKLY; Sunday archive rule; Monday brief; journal screenshot; precision clause.
