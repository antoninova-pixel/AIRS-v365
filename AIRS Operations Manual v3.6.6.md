# AIRS OPERATIONS MANUAL v3.6.6
**AI Investment Rating System · Indonesia Stock Exchange (IDX) · Swing horizon 3 days – 6 weeks**
Supersedes v3.6.5 in full. Companion files: *AIRS Session Starter v3.6.6* (boot law summary) and the latest *AIRS Session State* (§3C truth file). On conflict: **file > chat memory; Manual > Starter on procedure; Session State > everything on positions.**

## §1. Command Architecture (seven commands)
| # | Command | Inputs | Authority | End product |
| --- | --- | --- | --- | --- |
| a | RUN AIRS MACRO | MACRO DAILY variant: macro dashboard images + econ calendar (today). MACRO WEEKLY variant: econ calendar (this week + upcoming) + full corporate action calendar archive | Advisory layer | Regime call, stress watch, calendar gates, barbell inputs |
| b | RUN AIRS SHORTLIST | Watchlist column pages + Top Gainer CSV + Top Val/Vol/Freq CSV | Triage only, no scoring | Short List (≤10) + Cut List |
| c | RUN AIRS MIDDAY | 1H charts + 7-day broker summaries + midday CSVs + midday macro + foreign activity card | Active checker, provisional | **Full 8-step analysis, compressed output: Step 8 only — Quick Scan + Detail Cards + provisional scores (v3.6.6)** |
| d | RUN AIRS [date] | Daily charts + EOD broker summaries + EOD CSVs + macro + journal screenshot | **Authoritative** | Full 8-step EOD report, binding scores |
| e | RUN AIRS DEEP DIVE [X] | 1D + 1W + 1M charts + D/W/M broker summaries | Binding (single name) | Full 8-step single-stock report + Detail Card |
| f | SAVE AIRS SESSION STATE | All confirmations + journal | Persistence layer | §3C state file |
| g | RUN AIRS DETAIL CARD [date] | Locked score board (post-MIDDAY or post-EOD) — never invents scores | Render layer (PROVISIONAL post-MIDDAY / BINDING post-EOD) | Client-facing PNG per §11.8 locked template |
Ad-hoc discipline questions are always legal without a full report; answers cite framework law.

## §2. RUN AIRS MACRO
Two scheduled variants of one command:
* **MACRO DAILY** (weekday evenings, ~21:30 WIB): global indices (US futures, Asia), US/Indo yield curve, USD/IDR + 17,850 defense line, DXY, VIX, Brent/WTI (S2 tripwire 100), gold/silver/copper/nickel, CPO, Newcastle coal, crypto (context only), Investing.com calendar TODAY tab, Stockbit calendar TODAY page, news events.
* **MACRO WEEKLY** (Sunday ~12:30 WIB): Investing.com economic calendar THIS WEEK tab + all 11 Stockbit calendar pages (Economic, Dividend, Stock Split, Reverse Split, Right Issue, Warrant, Bonus, Tender Offer, RUPS, Pubex, IPO) captured and stored as the week's archive. **Archive rule:** a calendar page is analyzed ONLY when a holdings/watchlist/shortlist name matches a corporate action; otherwise it is acknowledged and archived without analysis.
* **Midday macro** (12:30 WIB, feeds MIDDAY): live Asia indices, major currencies, commodities.

Outputs: regime verdict (BULL / NEUTRAL / NEUTRAL-BEAR / BEAR), Holy Grail eligibility Y/N, stress scenario status (S1/S2/S3 with two-confirmation rule), calendar gates (add-freeze windows, event holds), barbell scenario set. **Sector rotation review (v3.6.6, owner ruling 15-Sep-2026):** "Ekosistem Data Center" added as a standing sub-sector — reference universe per owner BEI mapping: land/estates (DMAS, SSIA, KIJA, AKRA) · operators (DCII, EDGE, TLKM, ISAT, EXCL) · power/backup (POWR, PGAS, UNTR) · cabling (SCCO, KBLI, VOKS, JECC, KBLM) · fiber/towers (TOWR, TBIG, MTEL, DNET) · EPC (TOTL, NRCA, PPRE). If no fresh MACRO run exists, the saved snapshot governs; staleness >1 session is flagged in the report header.

**Monday Week-Ahead Brief (v3.6.5):** Monday's first session opens with a table-only brief pulled from the Sunday archive — macro events with dates/times, corporate actions matching holdings/watchlist, cum dates falling in the coming week. No deep analysis.

## §3. RUN AIRS SHORTLIST — union screening
**Universe** = screener result list ∪ Top Gainer board ∪ Top Val/Vol/Freq board, deduplicated. The scanner must surface qualified names absent from the screener list.
**Output:** - **Short List** — hard cap 10 new candidates. When >10 qualify, selection is by **committee judgment** (flow quality, setup geometry, liquidity class, sector fit, event proximity) with written reasoning per pick. No mechanical ranking rule. - **Cut List** — every rejected name + one-line reason + the lane/gate that failed. Overflow beyond the cap is listed with the judgment note. Cut List is the permanent audit trail. - Known-blacklisted names skip triage → straight to Cut List with "blacklist" reason. - No early trimming below the cap: borderline-but-qualified names proceed to FULL AIRS and are killed there, not at triage. - **Holdings auto-shortlist on top of the 10** and are never displaced.
**Precision clause (v3.6.5):** the shortlist is NEVER trimmed to save tokens or cost. Cap management happens only through committee judgment on quality.

## §4. RUN AIRS MIDDAY — active checker (v3.6.6: full analysis, compressed output)
Inputs: 1H charts, 7-day broker summaries (per name, holdings + shortlist), midday CSVs, midday macro image, Stockbit foreign activity card (final at 13:00 WIB). Powers: 1. **Upgrade/downgrade** the standing EOD score per name on intraday evidence (flow flips, level breaks, exhaustion). 2. **Add new catches** found intraday → provisional Detail Card + score, flagged *"midday-origin — EOD confirmation required."* 3. **Fire portfolio actions** intraday (stops, contradiction-rule exits, TP trims), not merely arm them.
**Analysis depth (v3.6.6, owner ruling 15-Sep-2026):** MIDDAY executes the **full AIRS framework internally** — Step 1 Macro · Step 2 Sector · Step 3 Broker · Step 4 Technical+MYCD · Step 5 5-Gate+G6 · Step 6 Committee (+Barbell) · Step 7 Tracking · Step 8 Final Decision. Scoring quality is identical to EOD; nothing is skipped. **Output is compressed to Step 8 only:** provisional Quick Scan (color-coded, locked 7-column layout) + 12-row Detail Cards. The written 8-step report remains EOD-exclusive. Two standing guardrails:
1. **One-line audit trail per score change** — every moved score carries a ≤1-line driver (e.g. *"BBRI 4.2→3.9: G3 flow conflict — midday NFS −95.4B vs weekly AK buy"*). No silent score moves.
2. **Fired actions stated in full** — any intraday stop/exit/trim fired by MIDDAY gets complete reasoning, even in compressed mode. Non-negotiable.
Midday scores remain provisional; the night's EOD run is the binding record (§6).

## §5. RUN AIRS [date] — EOD, authoritative
Inputs: daily charts + latest EOD broker summaries (per name, holdings + shortlist) + EOD CSVs + EOD macro + Investing.com calendar-today + **journal screenshot for holdings/fills reconciliation**.
Full 8-step report under §11 format lock: Step 1 Global Macro · Step 2 Sector Rotation · Step 3 Broker Analysis · Step 4 Technical + MYCD · Step 5 5-Gate+G6 Scoring · Step 6 Committee Deliberation (+ §11.6 Barbell when gates/stress active) · Step 7 Tracking vs Prior Reports · Step 8 Final Decision (Layer 1 Quick Scan + Layer 2 Detail Cards + Portfolio Allocation + Risk Monitoring + Entry Discipline checklists).

## §6. Authority & Contradiction
* **EOD Authority Rule:** EOD scores are binding for the track record; midday/downgrades hold until EOD confirms or reverses them.
* **Contradiction Rule:** a midday probe contradicted by EOD broker data → exit at next open.
* **Stop-Override Protocol (v3.6.3):** a fired stop is executable law. Sole exception: explicit owner decision + replacement hard stop, logged to P8. Any close below the replacement stop = market exit without discussion.

## §7. Scoring — 5 Gates + G6
G1 Macro/Sector 20% · G2 Trend 20% · G3 Flow 25% · G4 Momentum 15% · G5 Entry/R:R 20% · G6 Demand Event modifier −0.5 to +1.0 (never rescues failed G3).
Verdicts: 🟢 HIGH BUY 5.0 · 🟢 MOD BUY 4.0–4.5 · 🟡 WATCH 3.0–3.5 · 🔴 AVOID <3.0 · 🔵 HOLD · 🔴 EXIT.

## §8. Lanes & Provenance
Nine-lane screener stack. **Lane 8 Insider Print [INS]**: insider accumulation passing hard gates (3M/6M %, value, mcap, free float, price-vs-MA20, RSI bands). **Lane 9 Foreign Print [FOR]**: named foreign desks (AK/BK/RX/DX) net-buying with size. **[BND]**: bandar-proxy (ZP-type) driven. Tags print on Quick Scan rows and Detail Card titles. Provenance ≠ score; a tag is stripped when its sponsoring print flips, triggering thesis review.

## §9. Broker Tiers
Foreign 5-star: AK (UBS), BK (JPM), RX (Macquarie), DX (UBS alt). Domestic institutional: CC, BB, MG, CP, YU; ZP = bandar proxy. Retail: XL, PD, YP, SQ, XC. Retail-carried tapes with institutional selling fail G3.

## §10. Entries, Exits, Risk
* **Entry ladder:** Pullback – Optimal – Acceptable, anchored to POC / day-avg / week-avg — never last price.
* **Chase discipline:** Standard ≤2% above anchor (non-bull regime); Extended +2–5% only under bullish macro/Holy Grail; +8% hard ceiling.
* **Liquidity-as-Attribute:** 🐘A ≥500B/day · 🐘B 100–500B · 🐜C <100B = PERSONAL-ONLY probe ≤2%, 10% participation cap.
* **OBMD:** value <5B/day = log, never probe.
* **Execution-Gated Carry-Over:** unfilled ladders expire at their window unless re-armed.
* **Resolution Windows:** FAST 3–7d / SWING 2–6w with ATR reachability check.
* **TP/SL convention:** TP1/TP2 upside % from anchor/optimal entry; stops as close-based unless stated.
* **Events justify holds, never chases.**
* **Blacklist:** unquantifiable legal/governance risk skips triage.

## §11. Format Lock (permanent)
The v3.6.0 EOD specimen (with v3.6.0–v3.6.6 amendments) is the permanent structural reference: same tables, fields, column sequences, every session. Includes: canonical header + regime/stress lines; Step 1–8 structure; §11.6 Macro Scenario Barbell closing Step 6 when calendar/stress active (advisory — never changes scores/verdicts/sizing); 12-row Detail Cards for ALL holdings + actionable names at EOD; TP%-from-anchor convention block under Layer 2; provenance tags on titles. Format drift is a bug; re-issue on demand.
**§11.7 DEEP DIVE (v3.6.3):** full 8-step single-stock adaptation on D/W/M charts + D/W/M broker summaries, ending in the 12-row Detail Card with binding score. The former 4-block format is retired.
**§11.8 DETAIL CARD client-facing template (v3.6.6, owner ruling 15-Sep-2026 — locked from the approved 15-Sep MIDDAY layout):**
1. **Header** — title + framework/version line + regime + barbell split · BINDING / PROVISIONAL stamp · gate banners (red = freeze / blue = info / amber = flags & triggers).
2. **Quick Scan (ALL)** — full board, locked 7-column layout: Stock(+tags) / Score (with delta arrows vs prior board) / color-coded Verdict / Class / Signal / Foreign / Anchor. Navy header row. Midday-origin names carry amber chips.
3. **Top Buys** — BUY + MOD BUY only (score ≥3.8 when owner-specified), best 3–4, HARD MAX 5, held names routed to Holdings. Green-header 12-row cards, TP% from Optimal/anchor, NO-CHASE row on every card, frozen-ladder stamps.
4. **Holdings & Requested** — blue-header HOLD cards incl. EXIT variants; "Stops are LAW" row. Actionable Tier C cards carry red PERSONAL-ONLY chip.
5. **Macro Scenario Barbell** — leg / weight / expression / evidence / action-bias table + **Winners / Losers / Pivot-triggers strip**; advisory-only label; never changes scores/verdicts/sizing.
6. **Footer** — framework law lines on navy bar: TP% from anchor · ladders only · events justify holds never chases · stops are LAW · Tier C caps · provisional/binding statement.
**Client-facing language rules (v3.6.6):**
* **Class labels: BIG CAP A / BIG CAP B / MED CAP C** — animal icons (🐘/🐜) retired on all client-facing outputs (Detail Cards, Quick Scans, card Service Eligibility rows, footers). Internal analytical notes may still use the shorthand.
* **"OBMD" jargon banned on client-facing outputs** — render in plain language, e.g. *"daily value below 5B — log only, no probe."*
* RMKE/WBSA/BULL = investing holdings — Quick Scan only, cards only if requested. Tier C stamps (PERSONAL-ONLY + 10% participation cap).
**Render protocol (v3.6.6, permanent):** Python + Playwright ONLY (chromium CLI banned) · light-theme EN · 1194px full-page screenshot · PIL trim · output `"AIRS Detail Card [date] [EOD|MIDDAY] (EN light).png"`. Post-EOD render = BINDING stamp; post-MIDDAY = PROVISIONAL + midday-origin flags. Never invent scores — render the locked board.

## §12. Session State (§3C)
SAVE AIRS SESSION STATE persists: macro snapshot, latest EOD essentials, holdings (lots/avg/stops/override flags), active ladders/triggers, open flags, track record, framework version. File wins over chat memory. **Session protocol (v3.6.5):** one session per trading day — SHORTLIST → MIDDAY → EOD run in the same session to preserve context; SAVE AIRS SESSION STATE closes every session and the §3C file boots the next.

## §13. Reviews & Audits
* **P7** ladder-discipline review (weekend).
* **P8** deviation review (weekend): chase violations, non-executed stops, override log.
* Cut List audit: triage tightness check from Cut List history.
* Track record kept from the journal (authoritative for W/L).

## §15. Data Operations (v3.6.5, new)
**§15.1 MotionTrade CSV protocol.** Ranking boards (Top Gainer/Loser, Top Vol/Val/Freq) are exported as CSV, never screenshotted. Columns: Code, Last, Change, Prev, Open, High, Low, Freq, Vol, Val(K), Cap(M). Units: **Vol = lots · Val(K) = thousand rupiah · Cap(M) = million rupiah · Change = % vs previous close** (embedded % sign stripped on parse). Exports contain the full 761-ticker IDX universe, pre-sorted by ranking metric. When midday + EOD snapshots both exist, midday→EOD deltas (freq/vol/value growth into the close) are computed. In-file code screening is preferred over requesting additional screenshots.
**§15.2 File naming & archive.** `YYYY-MM-DD_[slot]_[dataset].csv` — slots: midday / eod; datasets: gainers / volvalfreq. Historical files are referenceable by date.
**§15.3 Daily capture schedule (WIB).**
* **MIDDAY (12:15–13:00):** gainers + volvalfreq CSV · consolidated watchlist image (8 screener results pre-consolidated into one watchlist by owner) · Stockbit foreign activity image (final 13:00) · midday macro image (live Asia indices / FX / commodities, Investing.com) · 1H charts (holdings + shortlist) · 7-day broker summary images (holdings + shortlist).
* **EOD (21:15–21:30):** gainers + volvalfreq CSV · watchlist image · EOD macro image · Investing.com calendar-today image · D charts (holdings + shortlist) · latest broker summary images (holdings + shortlist) · journal screenshot.
* **SUNDAY (12:30):** MACRO WEEKLY archive per §2.
* **DEEP DIVE:** on request only — D/W/M charts + D/W/M broker summaries.
**§15.4 Data completeness gate.** On each data drop, the analyst acknowledges receipt, checks completeness against §15.3, and flags any missing item BEFORE running analysis. No re-runs unless data was actually missing.

## §14. Changelog
* **v3.6.0** — TP%-from-anchor convention; [INS]/[FOR] tags.
* **v3.6.1** — §11.6 barbell block.
* **v3.6.2** — Execution-Gated Carry-Over; contradiction rule formalized.
* **v3.6.3** — Six-command architecture with RUN AIRS MACRO; SHORTLIST union-screening, committee-judgment cap-10, Cut List; MIDDAY active checker (up/downgrades, intraday catches, action firing); DEEP DIVE full 8-step D/W/M (§11.7 4-block retired); permanent format lock; [BND] tag; stop-override protocol.
* **v3.6.5** — Data Operations layer (§15): MotionTrade CSV protocol with locked units, file naming/archive, daily capture schedule, data completeness gate; MACRO DAILY / MACRO WEEKLY variants formalized; Sunday calendar archive rule (analyze-on-match only); Monday Week-Ahead Brief; one-session-per-day protocol (§12); journal screenshot added to EOD inputs; MIDDAY = cards + provisional scores confirmed against full-8-step alternative (cost discipline); shortlist precision clause (never trim for cost). *(Version numbering jumps to v3.6.5 by owner decision.)*
