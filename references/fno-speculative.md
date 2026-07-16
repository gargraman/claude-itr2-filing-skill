# F&O and Speculative Trading — ITR-3 treatment (AY 2026-27)

> **⚠️ BETA — needs practitioner review before first use**
>
> Turnover computation methodology below reflects the **ICAI Guidance Note on Tax Audit under Sec 44AB (2022 revised edition)** — this is the method almost every mainstream broker (Zerodha, Groww, Upstox, Samco, ICICI Direct) now uses in their Tax P&L. Older CA templates and pre-2022 articles use the earlier method that added option premium separately. If the user's CA uses the older method, that is a defensible position but not the current ICAI standard. Flag divergence and get the CA to sign off.
>
> Sections marked `[NEEDS-CA-REVIEW]` were derived from the Act and mainstream practitioner guidance but were not bit-verified against the AY 2026-27 ITR-3 Instructions PDF.

**When to load this file:** Any current-year F&O trading, intraday equity trading, jobbing, arbitrage, currency derivatives, commodity derivatives. Loading implies **`references/business-income.md`** is also loaded (F&O and speculative are business income → ITR-3).

**Related files:** `references/business-income.md` (Schedule BP/PL/BS mechanics), `references/losses.md §Business/speculative` (Sec 72, 73 c/f rules), `references/capital-gains.md` (for delivery equity, which is CG not business).

---

## 1. Classification — what goes where

| Activity | Head of income | Section basis |
|---|---|---|
| **F&O (equity, index, commodity, currency futures & options)** on a recognised stock exchange | **Non-speculative business** | Sec 43(5) proviso (d) — F&O on recognised exchanges is expressly excluded from "speculative transaction" definition |
| **Intraday equity** — buy and square-off same day on cash market | **Speculative business** | Sec 43(5) — no delivery = speculative |
| **Delivery-based equity** — bought, held ≥ 1 day, sold | **Capital gains** (STCG < 12 mo, LTCG ≥ 12 mo) | Sec 2(14), Sec 45. Covered in `capital-gains.md`. |
| Jobbing / arbitrage in cash equity without delivery | Speculative business | Sec 43(5) |
| Hedging transactions matching genuine underlying delivery position | Excluded from speculative if all conditions of Sec 43(5) proviso (a)/(b)/(c) satisfied | Sec 43(5) proviso |
| **Crypto (VDA)** trading | **Sec 115BBH — 30% flat**, not business, not CG | Sec 115BBH. Covered in `capital-gains.md`, NOT here. |

**Common misclassification traps:**
- Currency derivatives on RBI-approved exchanges (NSE-CD, BSE-CD, MCX-SX) → **non-speculative business** (Sec 43(5) proviso (e) added by FA 2013).
- Commodity derivatives on recognised commodity exchange with CTT paid → **non-speculative business** (Sec 43(5) proviso (e) covers this since FA 2013 and further clarified FA 2018).
- Off-exchange OTC forwards → **speculative** (no recognised exchange).

---

## 2. Why classification matters — CFL and offset rules

| Loss type | Section | Same-year offset | C/f period | C/f offset limited to |
|---|---|---|---|---|
| F&O loss (non-spec business) | Sec 71(2A), Sec 72 | Any head except salary | **8 AYs** | Business income (any business — spec or non-spec) |
| Intraday equity loss (speculative) | Sec 73(1), Sec 73(4) | Only against speculative income (same year) | **4 AYs** | **Speculative income only** |
| Delivery equity STCL | Sec 74 | STCG or LTCG (any) | 8 AYs | STCG or LTCG |
| Delivery equity LTCL | Sec 74 | LTCG only | 8 AYs | LTCG only |

**Practical rule:** If you have both F&O loss (₹3L) and intraday loss (₹50K) in the same year — the ₹3L can offset your consulting income, salary is out; the ₹50K sits in the speculative bucket, dies in 4 years unless you have speculative gains.

**Sec 80 gatekeeper:** All the above c/f losses die if the ITR is not filed by 139(1) due date. For AY 2026-27 non-audit case, **31-July-2026**. For audit case (turnover threshold breach or 44AB(e) trigger), **31-October-2026** with audit report by 30-September-2026.

**Under new regime:** Business loss set-off rules unchanged (Sec 115BAC does not modify Sec 71/72/73). But if opting to file under new regime with business income, **Form 10-IEA must be filed before the ITR** — see `references/regimes.md §Business-income 10-IEA`.

---

## 3. Turnover computation — the ICAI 2022 method

### Current standard (ICAI Guidance Note 2022 revised, para 5.14):

**Turnover = Sum of absolute profit + absolute loss on each trade.**

That's it. Both F&O (futures + options) and speculative — same formula.

**Superseded (pre-2022 method — do NOT use):** Old ICAI guidance added **option premium on sale** as part of turnover in addition to the absolute-difference method. This was widely misapplied to inflate turnover into audit territory. **The 2022 revised guidance removed the premium-addition rule for options.** Every mainstream broker's Tax P&L (Zerodha, Groww, Upstox, Samco, ICICI Direct, Kotak) now uses the |profit| + |loss| method only.

### Worked example — F&O
5 trades in FY 2025-26:

| Trade | Instrument | Realised P/L (₹) | Absolute |
|---|---|---:|---:|
| 1 | NIFTY FUT | +15,000 | 15,000 |
| 2 | BANKNIFTY FUT | −22,000 | 22,000 |
| 3 | NIFTY 25000 CE (sold, bought back) | +8,500 | 8,500 |
| 4 | RELIANCE PE (bought, expired worthless) | −4,200 | 4,200 |
| 5 | HDFCBANK FUT | +6,800 | 6,800 |
| **Net P/L** | | **+4,100** | |
| **Turnover** | | | **56,500** |

Net P/L = ₹4,100 (this goes to Schedule BP Part A as business income).
Turnover = ₹56,500 (this is compared to the Sec 44AB thresholds).

### Worked example — intraday equity (speculative)
Same |profit|+|loss| method. Report as **speculative business** in Schedule BP Part D. Note that some brokers show "speculative turnover" separately in Tax P&L — always trace back to per-trade P/L values.

### Audit implication
Turnover ₹56,500 in the example → far below ₹1 Cr / ₹10 Cr → no Sec 44AB(a) audit. But if the trader had ever declared under 44AD in the past 5 years, and now declares actual profit < 6% of turnover (₹4,100 / ₹56,500 = 7.3% — safe), Sec 44AB(e) does not trigger. If turnover ₹5 Cr with ₹2L profit (0.4%), audit triggers under Sec 44AB(e) if past 44AD election exists.

---

## 4. Reading the broker Tax P&L

Every major Indian broker publishes a per-FY Tax P&L. Structure varies slightly, but every one has:

1. **Realised P&L** — the number that goes to Schedule BP as business income.
2. **Turnover** — computed per ICAI 2022, feeds Sec 44AB threshold check.
3. **Charges** — brokerage, STT, exchange fees, GST on brokerage, SEBI, stamp duty. **Not the same as turnover.** These are direct costs deductible in Schedule PL.
4. **Segment split** — F&O / Intraday / Delivery / Currency / Commodity. Must be preserved when carrying to ITR-3 (non-spec vs spec vs CG).

### Samco specifically (user's broker per `CLAUDE.md`)
Samco's Tax P&L is typically named `Tax_P&L_<PAN>_<FY>.pdf` or `.xlsx`. Includes:
- Cover page with PAN + client ID + FY
- Segment-wise summary (Equity Delivery / Equity Intraday / F&O / Currency / Commodity)
- Per-trade or per-scrip realised P&L
- Turnover as per ICAI method
- Total charges (brokerage + STT + GST + others)

**Cross-check checklist for user (Samco or any broker):**
- [ ] Confirm Tax P&L covers exactly 1-Apr-2025 to 31-Mar-2026 (not CY).
- [ ] Segment classification matches ITR-3 heads (delivery → CG; intraday → speculative BP; F&O → non-spec BP).
- [ ] Turnover method note in the PDF states "ICAI Guidance Note 2022" or equivalent — else confirm with broker support.
- [ ] Charges are net of GST refund (rare for individuals).
- [ ] Bank ledger reconciles to broker ledger — payin/payout during FY matches bank statement transfers.

---

## 5. Where numbers land in ITR-3

For a filer with F&O + intraday + delivery equity:

| Broker line | ITR-3 schedule | Notes |
|---|---|---|
| F&O realised P&L | Schedule BP Part A (via Schedule PL row 61 net profit) | Non-speculative business |
| Intraday realised P&L | Schedule BP Part D (speculation business separate line) | Speculative — separate CFL bucket |
| Delivery equity STCG (< 12 mo) | Schedule CG A1 | STCG @ 20% u/s 111A |
| Delivery equity LTCG (≥ 12 mo) | Schedule CG B4 → Schedule 112A | LTCG @ 12.5% > ₹1.25L threshold |
| Charges (brokerage + STT + GST + SEBI + stamp) | Schedule PL row 45 (or specific expense rows) | Deductible against business income; STT on delivery equity is NOT deductible for CG segment (only rebate available u/s 88E for very specific cases, generally moot) |
| Turnover (per ICAI) | NOT reported in ITR-3 directly | Used only to determine Sec 44AB applicability at Step 1 |
| Bank + broker balance | Schedule BS assets side | Ends-of-year balance |

---

## 6. Presumptive 44AD for F&O — the trap

F&O = business → 44AD is technically available. Trader can declare 6% of turnover as deemed profit (100% digital → 6% rate applies).

**Example:** ₹50L F&O turnover → 6% = ₹3L presumptive profit. If actual realised P&L is ₹4L, declaring ₹3L saves nothing (you're understating; risky if AO checks broker data). If actual realised P&L is ₹1L (loss year), declaring ₹3L means paying tax on ₹3L when reality is ₹1L — worse.

**Where 44AD "helps":** avoids books requirement (Sec 44AA), avoids audit requirement (Sec 44AB), simpler filing. But:

1. **5-year lock-out on opting out** — Sec 44AD(4). If you opt out of 44AD in any of the next 5 years, and income exceeds basic exemption, audit becomes mandatory under Sec 44AB(e) for those years.
2. **No loss claim** — under 44AD you cannot declare a loss; deemed profit is a minimum floor.
3. **Advance tax by 15-March** — one installment only; no quarterly grace.

**Practical guidance:** For most retail F&O traders, DO NOT elect 44AD. The 5-year lock-in is not worth the simplification. Maintain the broker Tax P&L + bank statements as your "books" and file under actual profit/loss. Only elect 44AD if you're a genuinely profitable trader with consistent > 6% net margin and you value the audit-relief above the future flexibility loss.

`[NEEDS-CA-REVIEW]` — some CAs recommend 44AD for very small F&O turnover (< ₹20L) with modest profit, precisely because the 5-year lock is low-stakes at that scale. Judgement call.

---

## 7. Loss set-off worked scenarios

### Scenario A — F&O loss + salary
Salary ₹40L, F&O loss ₹3L (turnover ₹80L, no past 44AD election).
- Sec 71(2A): F&O (non-spec business) loss CANNOT be set off against salary.
- ₹3L carries to Schedule CFL, non-spec business bucket, c/f 8 AYs.
- Must file by 31-July-2026 to preserve c/f (Sec 80).
- Salary of ₹40L taxed in full.

### Scenario B — F&O profit + intraday loss + salary
Salary ₹40L, F&O profit ₹2L, intraday loss ₹50K.
- Intraday loss = speculative; can only offset speculative income → cannot offset F&O profit (non-spec) nor salary.
- ₹50K to Schedule CFL, speculative bucket, c/f 4 AYs.
- F&O profit ₹2L flows to BP → PB-TI → slab tax.
- Salary ₹40L taxed at slab. Total taxable business income = ₹2L.

### Scenario C — F&O loss + delivery LTCG
F&O loss ₹1.5L, delivery equity LTCG ₹5L (₹3.75L taxable after ₹1.25L 112A exemption).
- F&O loss (non-spec business) — under Sec 71 CANNOT offset LTCG per Sec 71(3): "capital loss cannot offset non-capital heads" — but this reads the other way? Let me re-check.
- **Actually Sec 71(2A):** business loss cannot offset SALARY. It CAN offset CG per Sec 71. So F&O loss ₹1.5L → offsets ₹1.5L of the taxable LTCG.
- Remaining LTCG taxable ₹2.25L @ 12.5% = ₹28,125 + cess. F&O loss fully consumed same year.

### Scenario D — c/f from prior years
Prior AY 2023-24 F&O loss ₹4L, current F&O profit ₹1L.
- Sec 72: prior business loss offsets current business profit up to ₹1L. Remaining ₹3L to c/f (still within 8-year window).
- Must have been filed within 139(1) that year and Schedule CFL of that year must be preserved.

---

## 8. Advance tax specifics

- Non-presumptive: standard quarterly (15-Jun 15%, 15-Sep 45%, 15-Dec 75%, 15-Mar 100%).
- Presumptive u/s 44AD: **entire liability by 15-Mar** — Sec 211 proviso.
- Interest u/s 234B (default > 10% of tax unpaid at year end) and 234C (installment shortfall) applies same as any other filer.
- **F&O trader-specific trap:** Q4 profitability spike (e.g., a big January winning trade) — advance tax on Q4 profit is due 15-March, not backdated to Q1/Q2. Sec 234C proviso applies.

---

## 9. Common traps

1. **Treating F&O as capital gains.** Common mistake — reporting F&O P&L in Schedule CG. F&O is business (Sec 43(5)(d)). Wrong reporting → CPC issues 143(1) intimation adjusting head, may deny CFL rights.
2. **Ignoring speculative sub-classification.** Reporting intraday equity together with F&O in one BP line. Loses the 4-year vs 8-year distinction, and if the intraday line is loss-making, you lose the ability to c/f the speculative loss (because it got netted with non-spec).
3. **Turnover with old ICAI method.** Using pre-2022 method (adding option premium) inflates turnover; may trigger unnecessary audit fear. Use current 2022 method.
4. **Missing STT deduction.** STT on delivery equity is NOT deductible against CG (it's added to cost of acquisition for LTCG under 112A; and to consideration for STCG only in some readings). STT on F&O IS deductible as business expense in Schedule PL. Don't cross the wires.
5. **44AD election without understanding lock-in.** One-time convenience → 5-year audit trap. Discouraged for most retail traders.
6. **Sec 44AB threshold confusion.** Turnover ₹50L → below both ₹1Cr and ₹10Cr — no audit. But if the trader declared under 44AD any of past 5 years and now shows loss/low profit → audit under Sec 44AB(e) at ANY turnover if income > basic exemption.
7. **Advance tax on Q4 windfall.** Big January-March F&O profit → 234C shortfall interest. Pay by 15-Mar even if tax not fully computed; adjust in return.
8. **Form 10-IEA missed for new-regime opt-out with business income.** ITR-3 filer opting for new regime does NOT need 10-IEA (new is default). But an ITR-3 filer opting for **old** regime MUST file Form 10-IEA before ITR — and once opted out, can switch back to new only ONCE lifetime. See `regimes.md` for the lifetime restriction detail.
9. **Reconciliation gap between broker Tax P&L and bank statements.** Every payin/payout to/from broker must match bank credit/debit. AIS SFT for high-value trader activity may not always flag F&O but does flag payins > ₹10L; unexplained gaps invite scrutiny.

---

## 10. Sources
- Sec 43(5) Income-tax Act 1961 (speculative transaction definition + provisos for F&O, currency derivatives, commodity derivatives)
- Sec 71, 71(2A), 72, 73, 80 — loss set-off and c/f
- Sec 44AA, 44AB, 44AD — books, audit, presumptive
- Sec 234B, 234C — advance-tax interest
- ICAI **Guidance Note on Tax Audit under Section 44AB** (2022 revised edition) — turnover computation for F&O and speculative
- CBDT Circular 3/2010 (older) — treatment of F&O for computation
- Broker Tax P&L reports — Zerodha Console, Samco, Groww Tax Statement (structural reference)

**Always cross-verify against:**
- Current-year ITR-3 utility from `https://www.incometax.gov.in/iec/foportal/downloads/income-tax-returns`
- AY 2026-27 ITR-3 Instructions PDF
- Broker's own Tax P&L methodology note (each broker publishes this)
