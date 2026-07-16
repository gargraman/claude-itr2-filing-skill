# Business & Professional Income — ITR-3 core mechanics (AY 2026-27)

> **⚠️ BETA — needs practitioner review before first use**
>
> This file was drafted for the ITR-3 expansion of the skill. Every threshold and section citation below is sourced from Income-tax Act 1961 (as amended by Finance Act 2025) and CBDT circulars, but has not been bit-verified against the AY 2026-27 ITR-3 utility, Instructions PDF, or reviewed by a practising CA. Before generating final JSON for a user filing ITR-3, cross-check:
> 1. ITR-3 utility field labels against `https://www.incometax.gov.in/iec/foportal/downloads/income-tax-returns`
> 2. AY 2026-27 ITR-3 Instructions PDF (from CBDT)
> 3. Where this file marks `[NEEDS-CA-REVIEW]`, flag to the user and get a CA to sign off

**When to load this file:** Any current-year business or professional income — including F&O, intraday, freelance / consulting receipts, partner remuneration from a firm, commission income treated as business, or converted crypto-day-trading. Loading also implies **`references/fno-speculative.md`** if the source is F&O or intraday equity.

**Related files:** `references/fno-speculative.md` (F&O turnover mechanics), `references/schedules.md §ITR-3` (schedule structure), `references/losses.md §Business/speculative` (Sec 72, 73 c/f rules), `references/regimes.md §Business-income 10-IEA` (regime opt-out lifetime restriction).

---

## 1. When ITR-3 is required (form selection)

You must file **ITR-3** (not ITR-2) if the taxpayer has **any** of:

- Business income (Sec 28) — trading, F&O, retail, wholesale, manufacturing
- Professional income (Sec 44AA(1) specified professions or otherwise) — freelance, consulting, medical, legal, architect, engineer, accountant, tech consulting
- Speculative income — intraday equity, jobbing, arbitrage
- Partner's remuneration / interest / share of loss from a partnership firm (share of profit is exempt u/s 10(2A) but must be disclosed in Schedule EI and Schedule IF)
- Commission or brokerage income treated as business
- Presumptive income under Sec 44AD / 44ADA / 44AE **AND** any other income that would put the return outside ITR-4 (foreign assets, CG, more than one house, foreign income — anything that disqualifies ITR-4)

ITR-4 (Sugam) is only available to residents with **presumptive** business/profession income who ALSO have no foreign asset, no capital gains beyond one specific 112A LTCG carve-out (added FY 2024-25), one house, and total income ≤ ₹50L. If any ITR-2-only condition applies (foreign assets, CG on immovable/RSU, ROR foreign income), the presumptive filer is pushed to **ITR-3**.

**Practical form-selection tree:**
```
Has any business/profession income? ──── NO ──→ ITR-2 (see rest of skill)
       │
       YES
       │
       ├── Only presumptive 44AD/44ADA/44AE AND meets all ITR-4 conditions? ──→ ITR-4
       │   (skill does NOT cover ITR-4 currently — flag to user)
       │
       └── Otherwise ──→ ITR-3
```

---

## 2. Books of Accounts — Sec 44AA

**Two categories:**

### Specified professions (Sec 44AA(1))
Legal, medical, engineering, architectural, accountancy, technical consultancy, interior decoration, film artist, authorised representative, company secretary, information technology (added by CBDT Notification 4/2001).

**Rule:** Must maintain **prescribed books** (Rule 6F: cash book, journal, ledger, carbon copies of bills > ₹25, original bills for expenses > ₹50, plus for medical: daily case register + inventory of drugs) if gross receipts > **₹1,50,000** in any of the 3 preceding PYs (or the current PY if profession is new).

### Other businesses / non-specified professions (Sec 44AA(2))
**Rule:** Must maintain **such books as will enable AO to compute total income** if:
- Income from business/profession > **₹1,20,000**, OR
- Turnover/gross receipts > **₹10,00,000** in any of 3 preceding PYs (or current PY if new)

For individuals / HUFs the thresholds are relaxed to **₹2,50,000 income** and **₹25,00,000 turnover** (Sec 44AA(2) proviso).

### Consequence of not maintaining
Sec 271A penalty: ₹25,000. Sec 44AB audit may also become mandatory if the taxpayer opts out of presumptive under 44AD/ADA and income > basic exemption — see §3.

### For F&O traders specifically
F&O is a **non-speculative business**. Sec 44AA thresholds apply. Most F&O filers exceed ₹25L turnover (turnover per ICAI Guidance = |profit| + |loss| — see `fno-speculative.md §3`) → books mandatory. In practice, the broker's Tax P&L + ledger + bank statements substitute for formal books — this is accepted for personal filers with no CA-attested books, but Sec 271A risk remains if AO is strict. `[NEEDS-CA-REVIEW]`

---

## 3. Tax Audit — Sec 44AB

Mandatory audit by a CA (Form 3CB + Form 3CD, or 3CA + 3CD for entities audited under other law) filed **1 month before ITR due date** — for AY 2026-27, audit report due **30-September-2026**, ITR due **31-October-2026** (audit case) instead of 31-July-2026.

### Thresholds

| Category | Threshold | Notes |
|---|---|---|
| **Business** — turnover > ₹1 Cr | Sec 44AB(a) | Standard rule |
| **Business** — turnover > ₹10 Cr | Sec 44AB(a) proviso | If aggregate cash receipts AND aggregate cash payments each ≤ 5% of respective totals. F&O is 100% digital → **₹10 Cr threshold** applies. |
| **Profession** — gross receipts > ₹50 lakh | Sec 44AB(b) | |
| **Profession** — gross receipts > ₹75 lakh | Sec 44AB(b) proviso | If cash receipts ≤ 5% of total receipts (added FA 2023). |
| **44AD business** declaring profit < 6% (digital) / 8% (cash) | Sec 44AB(e) | Only if income > basic exemption AND taxpayer opted 44AD in any of past 5 years and now declaring lower. |
| **44ADA profession** declaring profit < 50% | Sec 44AB(d) | Similar mechanics. |
| **44AE** (transport) declaring lower than deemed | Sec 44AB(c) | |

### Practical F&O read
F&O turnover as computed under ICAI method almost never exceeds ₹10 Cr for an individual retail trader unless doing hundreds of crores in notional exposure. But if the trader **has any loss** and had ever opted for 44AD in past 5 years, Sec 44AB(e) can force audit even at ₹5L turnover.

**Sec 271B penalty for non-audit:** 0.5% of turnover or ₹1.5L, whichever less.

---

## 4. Presumptive Taxation

### Sec 44AD — small business
- **Eligible:** Resident individual / HUF / firm (not LLP), gross turnover ≤ **₹3 Cr** for FY 2025-26 (raised from ₹2 Cr by FA 2023 provided cash receipts ≤ 5% of turnover; else ₹2 Cr).
- **Deemed profit:** 8% of turnover, or **6% for digital/bank turnover**. Higher declaration allowed.
- **Excluded:** Commission/brokerage business, agency, professionals under 44AA(1), person carrying on profession under 44ADA.
- **Availability for F&O:** F&O is a business, not a profession, so 44AD is technically available. But:
  - Once you opt out (declare actual profit lower than deemed), you're **locked out for 5 years** (Sec 44AD(4)) and if income > basic exemption during those 5 years, mandatory audit under Sec 44AB(e).
  - For F&O traders whose profitability swings year-to-year, this 5-year lock is a real risk. Opt for 44AD only if reasonably confident of consistent 6% profit — else stick to actual books.

### Sec 44ADA — specified professions
- **Eligible:** Resident individual / HUF / firm (not LLP) in a Sec 44AA(1) specified profession, gross receipts ≤ **₹75 lakh** for FY 2025-26 (raised from ₹50L by FA 2023 provided cash receipts ≤ 5% of turnover; else ₹50L).
- **Deemed profit:** 50% of receipts. Higher declaration allowed.
- **Same 5-year lock-out** applies (Sec 44ADA(4) — verify wording; via 44AB(d)). `[NEEDS-CA-REVIEW]`
- **Attractive for:** consultants, freelance software engineers, doctors, lawyers with genuinely > 50% effective margin.

### Sec 44AE — transport
- Rare for individual filers unless owning ≤ 10 goods vehicles.
- Deemed profit: ₹1,000 per ton per month for heavy vehicles > 12MT gross weight; ₹7,500/month for others.

### Books & audit exemption under presumptive
If income declared per presumptive scheme:
- Sec 44AA books requirement waived (Sec 44AD(5) / 44ADA(4)).
- Sec 44AB audit waived (unless the lock-out audit under §3 kicks in).

### Advance tax under presumptive
- **44AD:** entire advance tax payable in ONE installment by **15-March** (Sec 211 proviso).
- **44ADA:** entire advance tax payable in ONE installment by **15-March**.
- Non-presumptive business/profession: standard 15-Jun / 15-Sep / 15-Dec / 15-Mar quarterly schedule.

---

## 5. Schedule BP — Computation of income from Business or Profession

Applies to non-presumptive filers (presumptive filers use Schedule BP condensed rows via 44AD/ADA/AE sections). Structure `[NEEDS-CA-REVIEW]` — verify layout against utility:

- **Part A** — Profit from Profit & Loss (auto-linked to Schedule PL row 61)
- **Part B** — Additions to profit
  - Depreciation as per Companies Act debited to PL — added back
  - Sec 40 disallowances (interest, salary to partner beyond limits, TDS defaults)
  - Sec 43B disallowances (statutory dues unpaid by due date)
  - Sec 40A(3) — cash payments > ₹10,000 (₹35,000 for transporters) disallowed
  - Personal expenses debited
  - Any other disallowance
- **Part C** — Deductions from profit
  - Depreciation as per Income-tax Act (Schedule DEP total)
  - Sec 32(1)(iia) additional depreciation on new plant (20% on eligible)
  - Sec 35 scientific research
  - Sec 35AD investment-linked deductions (specified business)
  - Sec 43B items paid before due date of filing — allow
  - Any other deduction
- **Part D** — Speculation business — separate P&L line for intraday, jobbing (see `fno-speculative.md`)
- **Part E** — Specified business u/s 35AD (rare for retail filer)
- **Final:** Net income under head Business/Profession — flows to Part B-TI

---

## 6. Schedule PL — Profit & Loss Statement

Fully-fledged P&L with ~60 rows: revenue, purchases, direct costs, indirect costs, depreciation, interest, salaries, other expenses, net profit.

**For F&O-only filers with no separate books:** construct P&L from broker Tax P&L + bank statements:
- **Revenue:** F&O realised P/L (net gain) — NOT turnover. Turnover is a separate concept only for audit threshold.
- **Direct costs:** brokerage, STT, exchange charges, GST on brokerage, SEBI charges, stamp duty
- **Indirect costs:** internet, software subscription, home office proportion (defensible only if used exclusively), demat account AMC
- **Interest:** loan interest if borrowed to trade (rare — margin funding interest is direct cost)
- **Depreciation:** on laptop / trading rig if capitalised
- **Net profit:** revenue − all costs → Schedule BP Part A

**Cross-check:** Sum of P&L net profit + additions − deductions in Schedule BP should equal actual taxable business income.

---

## 7. Schedule BS — Balance Sheet

Assets = Liabilities + Capital. Required if books maintained (non-presumptive). Skeleton:

**Assets:**
- Fixed assets (net of accumulated depreciation) — furniture, computers, vehicles, immovable property used for business
- Investments — non-trading (personal shares, MFs held separately go to Schedule AL, not BS)
- Current assets — bank balances, receivables, cash, inventory (if any)
- Loans and advances given

**Liabilities:**
- Secured loans (bank OD, term loan)
- Unsecured loans (family, friends)
- Current liabilities — payables, statutory dues
- Provisions

**Capital account:** Opening capital + net profit − drawings = closing capital.

**For F&O-only filers:** BS is mostly bank balance + broker credit balance = total assets; opening capital + trading P&L − drawings = closing capital. Broker margin held ≠ your asset; it is a receivable from broker (current asset). `[NEEDS-CA-REVIEW]` on whether trading margin is asset or memoized.

---

## 8. "No account case" — abbreviated PL/BS

If Sec 44AA books requirement DOES NOT apply (income < ₹2.5L AND turnover < ₹25L for individual), ITR-3 offers a **No account case** section with only 4 lines: gross receipts, gross profit, expenses, net profit + closing bank/cash and closing debtor/creditor. Most F&O filers exceed the threshold and cannot use this.

---

## 9. Depreciation — Schedule DPM / DOA / DEP

Not typically applicable to F&O-only filers (no plant or building used for business). Applies to:
- Manufacturers with plant & machinery
- Traders with warehouse, vehicles
- Professionals with clinic/office equipment above ₹10K

**Block-of-assets concept (Sec 43(6)):** all assets with same depreciation rate form one block; WDV = opening WDV + additions − sale consideration; depreciation = WDV × rate.

**Key rates (Income-tax Rules Appendix I):**
| Block | Rate |
|---|---|
| Buildings — residential | 5% |
| Buildings — non-residential | 10% |
| Furniture & fittings | 10% |
| Plant & machinery (general) | 15% |
| Computers & computer software | **40%** |
| Motor cars (non-commercial) | 15% |
| Books (for professionals) | 40% |
| Intangibles (know-how, patents, copyrights, licences, franchises) | 25% |

**Additional depreciation (Sec 32(1)(iia)):** 20% extra in year of purchase for **new** plant & machinery in manufacturing / production business (excludes office equipment, furniture, ships, aircraft, vehicles). Half-rate (10%) if used < 180 days in first year.

**Schedule DPM** = P&M depreciation working. **Schedule DOA** = Other Assets. **Schedule DEP** = summary.

---

## 10. Schedule DCG — Deemed Capital Gains on sale of depreciable assets

Sec 50: if sale of depreciable asset causes block WDV to go negative, or entire block sold, the difference is deemed **short-term capital gain** regardless of holding period. Reported in Schedule DCG and then flowed to Schedule CG as STCG at slab rate.

**Not typically triggered for F&O-only filer.**

---

## 11. Disallowances (added back to profit)

Every disallowance reduces the deduction claim by adding back the disallowed expense to income.

| Section | What is disallowed | When |
|---|---|---|
| Sec 40A(3) | Cash payment for expense > ₹10,000 (₹35,000 for transporters) to single person in single day | Any business expense paid in cash above limit |
| Sec 40(a)(ia) | 30% of specified expense on which TDS not deducted or not deposited by due date | Interest, rent, commission, professional fees, contractor |
| Sec 40(a)(iii) | 100% of salary paid outside India / to non-resident without TDS | |
| Sec 43B | Statutory dues (GST, PF, ESI, gratuity, bonus, leave encashment, interest to banks/PSFI) if not paid by due date of filing u/s 139(1) | Statutory + certain interest |
| Sec 43B(h) | Payment to Micro/Small enterprise beyond 45 days (or 15 days if no written agreement) | Added FA 2023, effective AY 2024-25 |
| Sec 36(1)(iii) | Interest on capital borrowed for personal use (proportional disallow) | |
| Sec 37(1) | Personal expenses, capital expenses, illegal payments (bribes, freebies to doctors u/s 37(1) Expl. 1 & 3) | |

**For F&O filers:** typically only Sec 40A(3) matters — pay all brokerage/subscription in bank, never cash. Sec 43B irrelevant if no statutory dues. Sec 43B(h) irrelevant if no MSME vendors.

---

## 12. Chapter VI-A cross-references for ITR-3 filer

- **80JJAA** (employer deduction for new employees) — only if hiring workforce; irrelevant for solo traders.
- **80-IA / 80-IB / 80-IC / 80-ID / 80-IE** (area-based/industry-based deductions) — rare for individuals; if claimed, AMT under Sec 115JC likely triggers.
- **Other Chapter VI-A (80C, 80D, etc.)** — same as ITR-2 filer, see `references/regimes.md`.
- **80CCD(2)** employer NPS — if the ITR-3 filer receives salary too (separate employer), still available.

---

## 13. Sources
- Income-tax Act 1961: Secs 28-44DB (business income); 44AA (books); 44AB (audit); 44AD/44ADA/44AE (presumptive); 40A(3), 43B, 40(a) (disallowances); 32 (depreciation); 50 (deemed CG); 71(2A), 72, 73 (loss set-off / c/f).
- Finance Act 2025 (as passed) — no material changes to 44AA/44AB thresholds for FY 2025-26; 44AD/44ADA thresholds ₹3 Cr / ₹75L unchanged since FA 2023.
- CBDT Notification prescribing ITR-3 for AY 2026-27 (verify notification number from `https://www.incometax.gov.in`).
- ICAI Guidance Note on Tax Audit under Sec 44AB (2022 revised edition) — for turnover computation, especially F&O.
- Rule 6F — books of accounts for specified professions.
- Rule 128 — Foreign Tax Credit (same as ITR-2).

**Always verify:** ITR-3 utility field labels + AY 2026-27 Instructions PDF from `https://www.incometax.gov.in/iec/foportal/downloads/income-tax-returns`.
