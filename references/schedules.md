# ITR-2 Schedules — AY 2026-27 (FY 2025-26)

> **⚠️ Verification banner — read before relying on any specific field**
>
> Every item in this file marked `[SECONDARY-SOURCE]` came from mirror sites (CAalley, TaxGuru, ClearTax, taxgarden, saginfotech) because the research pass could not directly fetch `incometax.gov.in` / `incometaxindia.gov.in` (server returned HTTP 403 to automated fetches). These items are directionally correct but NOT bit-verified against the official gazetted PDF or the live utility.
>
> **Before the user files, do these three cross-checks:**
> 1. Download the currently-released ITR-2 utility (Excel and/or Common Offline) from `https://www.incometax.gov.in/iec/foportal/downloads/income-tax-returns` and confirm the version + release date match what this file says. If not, the utility wins — update this file.
> 2. Open the CBDT ITR-2 Instructions PDF for AY 2026-27 (linked from the same page). Every `[SECONDARY-SOURCE]` item below must be confirmed against that PDF. Where the PDF differs, the PDF wins.
> 3. Open the utility, add all applicable schedules, and confirm field labels match the field-by-field descriptions below.

**Legal basis:** CBDT Notification No. 46/2026 [F.No. 370142/6/2026-TPL], dated 30-March-2026 (G.S.R. 227(E)), substituting Form ITR-2 in Appendix-II of Income-tax Rules 1962. Corrigenda: Notifications 57–63/2026. `[SECONDARY-SOURCE]`

**Utility versions (as reported at time of writing, 12-Jul-2026):** Excel utility v1.1, JSON schema v1.1, Common Offline Utility v1.2.1 (01-Jul-2026), Validation Rules v1.0 dated May-2026. `[SECONDARY-SOURCE]` — always check `https://www.incometax.gov.in/iec/foportal/downloads/income-tax-returns` for the currently released version before generating final JSON.

**Filing deadline:** 31-July-2026 (Sec 139(1), non-audit individual). Belated/revised: 31-Dec-2026 (Sec 139(4)/139(5)).

**Consequences of late filing:**
- Sec 234F fee: ₹1,000 if TI ≤ ₹5L, else ₹5,000
- Sec 234A interest @ 1%/month on unpaid tax
- **Sec 80 bars carry-forward of most losses if return not filed by 139(1) date** — capital losses, business losses, speculation losses cannot be carried forward. House-property loss is the sole exception (Sec 71B allows c/f even in belated returns).
- **New regime forced** — cannot elect Old regime in a belated return

---

## Complete schedule list (order per notified form)

For each schedule below: **Code — Official Name — Purpose — Trigger — Key Fields**.

### 1. Part A — General Information (Part A-GEN)
- **Purpose:** Identity + filing metadata. Personal info, PAN, Aadhaar (full 12-digit mandatory for AY 2026-27; Enrolment ID no longer accepted), residential status flag (ROR/RNOR/NR), filing section (139(1)/139(4)/139(5)/139(8A) updated), regime opt-out flag, employer category, whether return is defective/revised.
- **Trigger:** Always.
- **Key mandatory fields:** PAN, Aadhaar, DOB (DD/MM/YYYY), full name as per PAN, address, PIN, mobile, email, residential status code, Nature of Employment (drop-down: Central Govt / State Govt / Public Sector / Pensioner / Others), whether opting out of new regime u/s 115BAC (Yes/No), filed under section (drop-down).

### 2. Schedule S — Salaries
- **Official name:** Details of Income from Salary
- **Purpose:** Reports gross salary per employer, exemptions u/s 10 (HRA, LTA, gratuity, leave encashment, etc. — only relevant in old regime), profit in lieu u/s 17(3), perquisites u/s 17(2) (RSU perquisite included here), standard deduction u/s 16(ia), professional tax u/s 16(iii), entertainment allowance u/s 16(ii) (govt employees only).
- **Trigger:** Any salary income during FY 2025-26. One row per employer.
- **Key fields per employer:** Employer name, TAN, address, PIN, employer category, gross salary (17(1) + 17(2) + 17(3) breakdown), value of perquisites (with 12BA row for RSU/ESOP perquisite), profits in lieu, allowances not exempt, standard deduction (₹75,000 new / ₹50,000 old for salaried).
- **Source document:** Form 16 Part A (TDS on salary) + Part B (salary breakup) + Form 12BA (perquisites). Cross-check with AIS SFT-018 (salary paid).

### 3. Schedule HP — House Property
- **Official name:** Details of Income from House Property
- **Purpose:** Rental income (let-out) or nil/deemed-nil for self-occupied, municipal tax deduction, 30% standard deduction, Sec 24(b) home-loan interest, arrears/unrealized rent, co-owner apportionment.
- **Trigger:** Own any house property (self-occupied, deemed-let-out, or let-out). Not triggered for the stated user profile unless disclosed.
- **Key AY 2026-27 addition:** Field `1b` for "rent that cannot be realized" — separately reportable. `[SECONDARY-SOURCE]`
- **Under new regime:** House-property loss cannot be set off against salary or any other head; it must be carried forward under Sec 71B (up to 8 years).

### 4. Schedule CG — Capital Gains
- **Official name:** Capital Gains
- **Purpose:** All short-term (A1–A8) and long-term (B1–B10) capital gains, deemed capital gains (C — VDA at C2), exemption deductions u/s 54/54B/54EC/54F etc. (D), rate-bucket set-off (E), accrual timing for advance-tax computation (F).
- **Trigger:** Any transfer of a capital asset during FY 2025-26. For AY 2026-27 the entire FY is post-23-Jul-2024, so all rows carry Finance (No.2) Act 2024 rates.
- **Key sub-rows relevant to typical filer:**
  - **A1** — STT-paid listed equity/equity MF STCG u/s 111A @ 20%
  - **A5** — STCG on unlisted shares / foreign shares (RSU/ESOP held < 24 mo) @ slab
  - **A8** — STCG on immovable property (< 24 mo) @ slab
  - **B4** — LTCG on listed equity/equity MF u/s 112A @ 12.5% (post ₹1.25L threshold) — must be filled via Schedule 112A sub-schedule
  - **B9** — LTCG on unlisted shares / foreign shares (RSU/ESOP held ≥ 24 mo) u/s 112 @ 12.5% (no indexation)
  - **B10** — LTCG on immovable property (≥ 24 mo) u/s 112 @ 12.5% (no index) OR resident individual/HUF election to use 20% with indexation for pre-23-Jul-2024 acquisitions (lower of the two — proviso to Sec 112(1))
  - **C2** — VDA (crypto) transaction-wise under Schedule VDA @ 30% u/s 115BBH
- **Key AY 2026-27 addition:** Buy-back loss row (B8 area) — allowed only if matching deemed dividend disclosed in Schedule OS row 1a(iii) u/s 2(22)(f), effective for buy-backs on/after 01-Oct-2024. `[SECONDARY-SOURCE]` — verified statutorily (Sec 46A + Sec 2(22)(f)) but the exact row number and cross-linking rule in the AY 2026-27 utility is from mirror sites.
- **Load `references/capital-gains.md`** for classification tree, rates, and computation.

#### 4a. Schedule 112A — Scrip-wise LTCG under 112A
- **Purpose:** Per-scrip disclosure of LTCG on listed equity / equity-oriented MF units / business trust units held > 12 months with STT paid. Enables Sec 55(2)(ac) grandfathering (FMV as on 31-Jan-2018) for units acquired on or before 31-Jan-2018.
- **Trigger:** Any single LTCG transaction under Sec 112A. No threshold — the ₹1.25L exemption is applied downstream at tax computation; disclosure is mandatory even for gains below ₹1.25L.
- **Columns per row:** Share/unit acquired on-or-before / after 31-Jan-2018 flag, ISIN, name of share/unit, No. of shares/units, Sale price per unit, Total sale value, Cost of acquisition (actual), FMV per unit on 31-Jan-2018, Total FMV on 31-Jan-2018, Expenditure on transfer, Total deductions, LTCG.
- **Grandfathering formula (Sec 55(2)(ac)):** Cost = **higher of** [actual cost] **OR** [lower of (FMV 31-Jan-2018) and (sale consideration)].
- **Consolidation rule:** Lots acquired after 31-Jan-2018 may be consolidated in a single row (ISIN `INNOTREQUIRD`, name `CONSOLIDATED`, code `1a=AE`) — CBDT optionality from 19-Jul-2019 still valid.

#### 4b. Schedule VDA — Virtual Digital Assets
- **Purpose:** Transaction-wise reporting of VDA (crypto, NFT) gains taxable u/s 115BBH @ 30% (flat, no set-off, no c/f).
- **Trigger:** Any VDA transfer during FY.
- **Columns:** Date of acquisition, Date of transfer, Head (CG or Business), Cost of acquisition (nil if already taxed u/s 56(2)(x) as gift), Consideration received, Income.
- **Sec 194S TDS credit:** claim in Schedule 20C by row-matching against 26AS.

### 5. Schedule OS — Income from Other Sources
- **Official name:** Income from Other Sources
- **Purpose:** Interest (savings, FD, RD, tax-free bonds, IT refund interest), dividends (Indian + foreign — post-DDT abolition FY 2020-21, all dividends slab-taxed), 2(22)(f) buy-back deemed dividend (new row for AY 2026-27), winnings from lottery/games (Sec 115BB), unexplained income (Sec 115BBE), family pension (with std deduction), residual "any other".
- **Trigger:** Any interest, dividend, or other-source income.
- **Key rows:**
  - `1a(i)` — Dividend income other than (ii)/(iii) — Indian and foreign dividends aggregate here
  - `1a(iii)` — **NEW for AY 2026-27** `[SECONDARY-SOURCE]`: Dividend u/s 2(22)(f) — buy-back deemed dividend; only Sec 57(iii) interest expense capped at 20% deductible
  - `1b` — Interest income (savings acct, FD/RD, tax-free bond etc. — with sub-rows by nature)
  - `1c` — Rental income from letting of machinery
  - `1d` — Family pension (with std deduction u/s 57(iia) = lower of ₹25,000 or 1/3rd)
  - `1e` — Winnings (lottery, crossword, races, card games, gambling, online games u/s 115BBJ) — flat 30% no basic exemption
  - `2` — Any other income (VDA line 2e removed to Schedule VDA/CG)
- **Deduction u/s 57:** collection expenses, interest on borrowed capital (dividend income — capped at 20% of dividend), family-pension standard deduction.
- **Cross-check:** AIS SFT-016 (dividend), SFT-016 (interest), SFT-005 (interest > ₹5,000 from cooperative/banking), foreign broker 1042-S/CP-500.

### 6. Schedule CYLA — Current Year Loss Adjustment
- **Official name:** Details of Income after set-off of current year losses
- **Purpose:** Sec 70 (intra-head) and Sec 71 (inter-head) set-off within same FY.
- **Trigger:** Any current-year loss under any head.
- **Rules:**
  - HP loss can offset any head, capped at ₹2,00,000/year (Sec 71(3A))
  - Capital loss cannot offset non-capital heads (Sec 71(3))
  - STCL offsets both STCG and LTCG; LTCL offsets only LTCG (Sec 70(2)/(3))
  - Speculative loss offsets only speculative gain (Sec 73(1))
  - VDA loss cannot offset anything (Sec 115BBH(2))
  - Under **new regime**: HP loss CANNOT offset salary (Sec 115BAC(2)(i)) — forced to Schedule CFL

### 7. Schedule BFLA — Brought Forward Loss Adjustment
- **Official name:** Details of income after set-off of brought forward losses of earlier years
- **Purpose:** Set off losses c/f from earlier AYs against current year's income under same head.
- **Trigger:** Any b/f loss from a prior AY being set off this year.
- **Rules mirror CYLA restrictions.** For b/f STCL, up to 8 AYs from the loss year; LTCL b/f only against LTCG, 8 AYs.

### 8. Schedule CFL — Carry Forward Losses
- **Official name:** Details of Losses to be carried forward to future years
- **Purpose:** Losses remaining after CYLA and BFLA that will be carried to future AYs. Year-wise, head-wise.
- **Trigger:** Any residual loss to c/f.
- **Rules:**
  - Sec 74: capital losses c/f 8 years
  - Sec 71B: HP loss c/f 8 years (allowed even in belated returns)
  - Sec 72: business loss c/f 8 years
  - Sec 73(4): speculative loss c/f 4 years
  - Sec 80 bar: capital/business/speculative losses cannot be c/f unless return filed by Sec 139(1) date
- **Load `references/losses.md`** for full mechanics.

### 9. Schedule VI-A — Deductions under Chapter VI-A
- **Official name:** Deductions under Chapter VI-A
- **Purpose:** 80C, 80CCC, 80CCD(1)/(1B)/(2), 80CCH, 80D, 80DD, 80DDB, 80E, 80EE, 80EEA, 80G (via Schedule 80G), 80GG, 80GGA, 80GGC, 80TTA, 80TTB, 80U, etc.
- **Trigger:** Old regime AND user has any deduction. Under **new regime**, only 80CCD(2) employer NPS (up to 14% of Basic+DA for private-sector employees) and 80CCH(2) Agniveer are allowed — everything else is blocked at portal validation.
- **Load `references/regimes.md`** for exact allowed list per regime.

### 10. Schedule 80G — Donations
- **Official name:** Details of donations entitled for deduction under section 80G
- **Purpose:** Table A — 100% deduction w/o qualifying limit (PM CARES, PMNRF, NDF). Table B — 50% deduction w/o qualifying limit. Table C — 100% with qualifying limit. Table D — 50% with qualifying limit.
- **Trigger:** Old regime + any 80G donation.
- **Mandatory field (AY 2026-27):** ARN (Donation Reference Number) from donee's Form 10BE certificate. Without ARN, portal blocks deduction.
- **Cash cap:** Cash donation > ₹2,000 disallowed (Sec 80G(5D)).

### 11. Schedule 80GGA — Donations for scientific research / rural development
- **Trigger:** Old regime + donation to eligible research institution. Rare.

### 12. Schedule 80GGC — Contributions to political parties
- **Trigger:** Old regime + contribution to registered political party or electoral trust. Must be non-cash.

### 13. Schedule 80DD — Maintenance of disabled dependant
- **Trigger:** Old regime + dependant with disability.
- **AY 2026-27 addition:** Disability category (drop-down) + Form 10-IA acknowledgement number + date now mandatory fields. `[SECONDARY-SOURCE]`

### 14. Schedule 80U — Self disability
- **Trigger:** Old regime + self disability.
- **Same expanded disclosure** as 80DD. `[SECONDARY-SOURCE]`

### 15. Schedule AMT — Alternate Minimum Tax
- **Official name:** Computation of Alternate Minimum Tax payable u/s 115JC
- **Purpose:** AMT @ 18.5% on adjusted total income if regular tax < AMT and ATI > ₹20L.
- **Trigger:** Old regime only + any claim of 80H–80RRB deductions or Sec 10AA (SEZ). Salaried without such claims → NOT applicable.
- **Sec 115JEE(3):** AMT provisions do not apply to a person opting for new regime u/s 115BAC.

### 16. Schedule AMTC — AMT Credit
- **Trigger:** Prior-year AMT paid; credit u/s 115JD carried forward 15 years.

### 17. Schedule SPI — Income of specified persons
- **Official name:** Income of specified persons (spouse, minor child, etc.) includible in taxpayer's income
- **Purpose:** Sec 60–64 clubbing (spouse income from taxpayer's assets, minor child income beyond ₹1,500 exemption per child u/s 10(32)).
- **AY 2026-27 addition:** Nature of clubbed income + applicable clubbing provision now mandatory fields. `[SECONDARY-SOURCE]`
- **Trigger:** Any clubbable income.

### 18. Schedule SI — Special Rate Income
- **Official name:** Income chargeable to tax at special rates
- **Purpose:** Segregates income taxed at special rates from slab-rate income for computation. Auto-populated from CG (111A @ 20%, 112 @ 12.5%, 112A @ 12.5% > ₹1.25L), OS (115BB winnings @ 30%, 115BBH VDA @ 30%, 115BBJ online games @ 30%), etc.
- **Trigger:** Any special-rate income (auto-populates).
- **Critical:** Sec 87A rebate NOT applicable on special-rate income under either regime.

### 19. Schedule EI — Exempt Income
- **Official name:** Details of Exempt Income (Income not to be included in Total Income)
- **Purpose:** Discloses (but does not tax) — agriculture income, PPF interest, tax-free bond interest, insurance maturity u/s 10(10D) (with new-regime caveats), share-of-profit from firm u/s 10(2A), gifts from relatives, DTAA-exempt income, PTI-exempt.
- **Trigger:** Any exempt income received during FY.
- **Note:** If aggregate agricultural income > ₹5,000, must be disclosed here; treated as rate income for partial-integration (Old regime only).

### 20. Schedule PTI — Pass-Through Income
- **Purpose:** Sec 115UA (REIT/InvIT) or Sec 115UB (Cat-I/II AIF) pass-through income. Auto-populated from Form 64B/64C received from the trust/fund.
- **Trigger:** Any REIT/InvIT/AIF distribution received.

### 21. Schedule FSI — Foreign Source Income
- **Official name:** Details of Income from outside India and tax relief
- **Purpose:** Country-by-country breakdown of income accrued outside India for a ROR, along with tax paid outside India and relief claimed under Sec 90/90A/91.
- **Trigger:** ROR + any foreign-source income (foreign dividend, foreign interest, foreign capital gain, foreign salary from prior employment, etc.). RNOR/NR generally do not fill unless specific facts apply.
- **Columns:** Country code, Country name, TIN (or passport number if no TIN), Head of income, Income from outside India (INR), Tax paid outside India (INR), Tax payable on such income under normal Indian provisions, Tax relief (lower of the two, or per DTAA), Relevant Article of DTAA / Section 91.
- **Load `references/foreign-assets.md §2`.**

### 22. Schedule TR — Tax Relief
- **Official name:** Summary of tax relief claimed for taxes paid outside India
- **Purpose:** Country-wise summary aggregating Schedule FSI totals. Must reconcile: Sum of FSI (col v) per country = TR (col b) per country; Sum of FSI (col vii) per country = TR (col c) per country.
- **Trigger:** Any FTC claim.
- **Prerequisite:** **Form 67 must be filed online BEFORE the ITR is uploaded** (or at latest before end of AY). Rule 128(9). Missing Form 67 → CPC disallows FTC in 143(1) intimation.
- **Load `references/foreign-assets.md §4`.**

### 23. Schedule FA — Foreign Assets
- **Official name:** Details of Foreign Assets and Income from any source outside India
- **Purpose:** Disclosure of every foreign asset held any time during the **calendar year** 1-Jan-2025 to 31-Dec-2025 (not FY), for a ROR only.
- **Trigger:** ROR AND any foreign asset held any time during CY 2025 (even $1). NRs and RNORs do not file Schedule FA.
- **Sub-tables:**
  - **A1** — Foreign Depository Accounts (foreign bank accounts)
  - **A2** — Foreign Custodial Accounts (foreign brokerage — Schwab, Fidelity, E*Trade, IB, etc.)
  - **A3** — Foreign Equity and Debt Interest (unsold RSUs/ESPP/ESOPs, foreign shares, foreign bonds)
  - **A4** — Foreign Cash Value Insurance / Annuity Contract
  - **B** — Financial Interest in any Entity (partnership share, LLC interest, etc.)
  - **C** — Immovable Property held outside India
  - **D** — Any Other Capital Asset
  - **E** — Signing Authority in any account (foreign bank/broker) where you are not the owner
  - **F** — Trusts (as trustee, beneficiary, or settlor)
  - **G** — Any Other Income Taxable Outside India not covered above
- **Threshold:** NONE. Every foreign asset must be reported, no matter how small.
- **Penalty for non-disclosure:** ₹10 lakh flat per Sec 42/43 Black Money Act. Post 1-Oct-2024 amendment: exemption for aggregate value of non-immovable-property foreign assets ≤ ₹20 lakh (immovable property never exempt). **Disclosure obligation remains — the exemption is only from penalty.**
- **Currency:** Foreign currency + INR conversion at SBI TT-buying rate on relevant date (peak-date rate for peak balance, 31-Dec rate for closing balance).
- **Load `references/foreign-assets.md §1`.**

### 24. Schedule 5A — Portuguese Civil Code apportionment
- **Purpose:** 50/50 apportionment of non-salary income between spouses governed by Portuguese Civil Code (Goa, Dadra & Nagar Haveli, Daman & Diu) under Sec 5A.
- **Trigger:** Marriage under communhão dos bens regime. Skip otherwise.

### 25. Schedule AL — Assets and Liabilities
- **Official name:** Assets and Liabilities at the end of the year
- **Purpose:** Balance sheet snapshot as on 31-Mar-2026 — immovable property, movable assets (jewellery, vehicles, art, financial assets), corresponding liabilities.
- **Trigger:** Total income > **₹1 crore** for AY 2026-27 `[SECONDARY-SOURCE]` — threshold reportedly raised from ₹50L in AY 2025-26 to ₹1 Cr for AY 2026-27. **VERIFY in the utility before assuming a ₹75L filer can skip this**; if the utility still uses ₹50L, apply the lower threshold.
- **Fields:** Cost of each asset, description, address (for immovable), corresponding liability.

### 26. Schedule "Tax deferred on ESOP" (start-up ESOP tracker)
- **Purpose:** Sec 17(2)(vi) proviso — eligible start-up ESOP tax deferral for 48 months or until sale/quit, whichever earlier.
- **Trigger:** Only if employer is a DPIIT-recognised eligible start-up. Regular listed-company RSUs (Google, Meta, Amazon) — NOT eligible; do not fill.

### 27. Part B-TI — Computation of Total Income
- **Purpose:** Roll-up of all heads → GTI → Chapter VI-A deductions → Total Income → segregation of special-rate vs slab-rate.
- **Trigger:** Always.

### 28. Part B-TTI — Computation of Tax on Total Income
- **Purpose:** Slab tax, surcharge, cess, rebate 87A, AMT liability, TDS/TCS/advance-tax/self-assessment tax credit, refund/tax payable, bank account for refund.
- **Trigger:** Always.
- **Under new regime for AY 2026-27:** Rebate 87A up to ₹60,000 for TI ≤ ₹12L; surcharge slabs 10/15/25% (37% NOT applicable); LTCG/STCG surcharge capped at 15%; cess 4% on tax + surcharge.
- **Under old regime:** Rebate 87A ₹12,500 for TI ≤ ₹5L; surcharge slabs 10/15/25/37%.

### 29. Schedule Bank Accounts
- **Official name:** Details of all Bank Accounts held in India at any time during the previous year
- **Purpose:** All active Indian bank accounts held any time during FY 2025-26 (savings, current). Refund nominee account marked.
- **Trigger:** Always.
- **Fields per account:** IFSC (11 chars), Account No, Bank name, type (Savings/Current), Refund account (Y/N).
- **Note:** Dormant accounts closed > 3 years and inactive foreign accounts (which go to Schedule FA) — not required here.

### 30. Schedule 20 — Tax Payments
Split into four sub-schedules:
- **20A — Advance Tax and Self-Assessment Tax:** BSR code (7 chars), date of deposit (DD/MM/YYYY), Challan serial no. (5 digits), amount. From challan 280.
- **20B — TDS on Salary (Form 16 Part A):** TAN of deductor, name, income under salary, tax deducted. Auto-populated from 26AS.
- **20C — TDS Other than Salary:** TAN, name, section under which TDS deducted (**new column for AY 2026-27** `[SECONDARY-SOURCE]`), gross income, tax deducted. Rows for TDS on interest (194A), dividend (194), rent (194I/194IB), commission (194H), professional fees (194J), securities (194K), 194N cash withdrawal, 194S VDA, etc.
- **20D — TCS:** TAN of collector, tax collected. Includes TCS on LRS remittances (Sec 206C(1G)) — parent may claim minor's LRS TCS via Form 12BAA under Sec 206C(4) amendment. `[SECONDARY-SOURCE]` on the 12BAA cross-claim row.

### 31. Verification
- **Purpose:** Declaration of correctness, signature via Aadhaar OTP / DSC / EVC.
- **Trigger:** Always.
- **AY 2026-27:** Full 12-digit Aadhaar mandatory (Enrolment ID no longer accepted). `[SECONDARY-SOURCE]`
- **E-verification within 30 days of ITR upload** — else return treated as never filed (defective u/s 139(9)).

---

## Filing Order (for schedule-by-schedule walkthrough)

Follow this order in the SKILL.md Step 3 walkthrough:

1. Part A-GEN
2. Schedule S (salary)
3. Schedule OS (interest, dividends)
4. Schedule CG (+ Schedule 112A if applicable + Schedule VDA if applicable)
5. Schedule EI (exempt income disclosure)
6. Schedule VI-A (deductions — old regime only)
7. Schedule 80G / 80GGA / 80GGC (donations — old regime only)
8. Schedule CYLA (current-year loss set-off)
9. Schedule BFLA (brought-forward loss set-off)
10. Schedule CFL (losses to c/f)
11. Schedule SI (special-rate income — auto)
12. Schedule FSI (foreign source income)
13. Schedule TR (tax relief summary)
14. Schedule FA (foreign assets)
15. Schedule AL (only if TI > ₹1 Cr)
16. Part B-TI (total income)
17. Part B-TTI (tax + refund)
18. Schedule 20 Tax Payments (20A/B/C/D)
19. Schedule Bank Accounts
20. Verification

Rationale for order: source-of-income schedules first, then set-off/carry-forward, then deductions, then foreign-income summary, then FA disclosure, then computation, then payments, then bank & verification. Reconcile against AIS/26AS/Form 16 in parallel (Step 4 of SKILL.md workflow).

---

## Appendix — ITR-3 additional schedules (BETA)

> **When to use this appendix:** Only if Step 1 form selection determined ITR-3 (any business or professional income — F&O, intraday, freelance, presumptive, partner in firm, etc.). ITR-3 also includes ALL ITR-2 schedules above (salary, HP, CG, OS, FA, etc.) — this appendix lists the ITR-3-only additions.
>
> **BETA — needs practitioner review.** Field structure below reflects Act + AY 2025-26 utility patterns; cross-check every field against the current AY 2026-27 ITR-3 utility from `https://www.incometax.gov.in/iec/foportal/downloads/income-tax-returns` before generating JSON.

**Related refs:** `references/business-income.md` for Sec 44AA / 44AB / 44AD mechanics and Schedule BP/PL/BS/DEP structure; `references/fno-speculative.md` for F&O and intraday equity turnover and classification.

### ITR-3.1 Schedule BP — Computation of income from Business or Profession
- **Purpose:** Reconciles net profit from Schedule PL (or presumptive computation) to taxable business income via additions (disallowances, dep as per Cos Act) and deductions (dep as per IT Act, Sec 43B paid, etc.). Separate line for speculative business (Part D).
- **Trigger:** Any business or professional income.
- **Key sub-sections:** Part A (from PL), Part B (additions), Part C (deductions), Part D (speculation), Part E (Sec 35AD specified business).
- **Load `references/business-income.md §5`.**

### ITR-3.2 Schedule PL — Profit and Loss Statement
- **Purpose:** Full P&L: revenue, purchases, direct/indirect expenses, depreciation, salaries, interest, other expenses, net profit before tax. `[SECONDARY-SOURCE]` on exact row count (~60 rows).
- **Trigger:** Non-presumptive business/profession where books are maintained (Sec 44AA(2)).
- **F&O-only filer construction:** revenue = realised P&L; direct costs = brokerage + STT + GST + exchange + SEBI + stamp; indirect costs = internet, software, home-office proportion (if defensible). See `references/business-income.md §6`.
- **No-account case:** abbreviated 4-line entry (gross receipts, gross profit, expenses, net profit) if under Sec 44AA(2) proviso thresholds (₹2.5L income AND ₹25L turnover for individual/HUF).

### ITR-3.3 Schedule BS — Balance Sheet
- **Purpose:** Assets, liabilities, capital account snapshot as on 31-Mar-2026.
- **Trigger:** Non-presumptive business where books are maintained.
- **F&O-only filer construction:** bank + broker balance = assets; loans (if any) = liabilities; opening capital + net trading profit − drawings = closing capital. See `references/business-income.md §7`.
- **No-account case:** abbreviated to closing bank/cash + closing debtors/creditors.

### ITR-3.4 Schedule DPM — Depreciation on Plant & Machinery
- **Purpose:** Block-of-assets working for P&M depreciation under IT Act Rule 5 read with Appendix I.
- **Trigger:** Any P&M or computer/software used in business.
- **Rates:** P&M general 15%, computers 40%, motor cars 15%. Additional depreciation 20% (Sec 32(1)(iia)) for new eligible P&M in manufacturing.
- **Typically NA for F&O-only filers** (no P&M in F&O business unless laptop is capitalised).

### ITR-3.5 Schedule DOA — Depreciation on Other Assets
- **Purpose:** Building, furniture, intangibles.
- **Rates:** Buildings residential 5% / non-residential 10%; furniture 10%; intangibles 25%; books (for professionals) 40%.
- **Typically NA for F&O-only filers.**

### ITR-3.6 Schedule DEP — Summary of Depreciation
- **Purpose:** Roll-up of DPM + DOA totals for the year.
- **Trigger:** Any entry in DPM or DOA.

### ITR-3.7 Schedule DCG — Deemed Capital Gains on sale of depreciable assets
- **Purpose:** Sec 50 short-term capital gain on sale of depreciable assets when block WDV goes negative or entire block sold.
- **Trigger:** Only if a depreciable asset was sold during FY.
- **Typically NA for F&O-only filers.**

### ITR-3.8 Schedule ESR — Expenditure on Scientific Research (Sec 35)
- **Purpose:** Deduction for expenditure on scientific research (in-house or contribution to approved institution).
- **Trigger:** Rare for individual filers. Skip unless flagged.

### ITR-3.9 Schedules 44AD / 44ADA / 44AE — Presumptive taxation
- **Purpose:** Simplified computation for eligible presumptive business/profession.
- **Trigger:** Only if presumptive election is made in the current AY.
- **Fields:** Gross turnover (44AD) / gross receipts (44ADA), digital vs cash split, deemed profit (6%/8% for 44AD; 50% for 44ADA), actual profit if higher, aggregate turnover check against ₹3 Cr / ₹75L caps.
- **Warning:** Sec 44AD(4) five-year lock-out on opt-out. See `references/business-income.md §4` and `references/fno-speculative.md §6`.

### ITR-3.10 Schedule ICDS — Income Computation Disclosure Standards
- **Purpose:** Disclosure of adjustments per 10 notified ICDS (I to X) for non-presumptive business income.
- **Trigger:** Mandatory for all non-presumptive business/profession income.
- **Typical individual filer:** most ICDS have nil impact for a service/trading business; disclose as such (zero adjustment) — but the schedule must be filled, not skipped.

### ITR-3.11 Schedule IF — Information on Partnership Firms
- **Purpose:** Details of every partnership firm/LLP in which the taxpayer is a partner — firm name, PAN, share %, capital, remuneration, interest received.
- **Trigger:** Only if partner in a firm/LLP.

### ITR-3 Filing Order (append after ITR-2 filing order above)

For ITR-3, insert these AFTER Schedule OS and BEFORE Schedule CYLA in the walkthrough:

```
5a. Schedule BP (with BP Part D — speculation — as sub-block)
5b. Schedule PL (feeds BP Part A)
5c. Schedule BS
5d. Schedule DPM / DOA / DEP (only if applicable)
5e. Schedule DCG (only if applicable)
5f. Schedule ESR (only if applicable)
5g. Schedule 44AD / 44ADA / 44AE (only if presumptive)
5h. Schedule ICDS (mandatory for non-presumptive)
5i. Schedule IF (only if partner in firm)
```

CYLA now consumes the business-loss line as well as HP/CG losses. CFL now tracks both non-spec business (Sec 72, 8-yr) and speculative (Sec 73(4), 4-yr) buckets.

---

## Schedules NOT applicable to standard resident-individual profile

- Schedule 115AD proviso row (FII only)
- Schedule 5A (Portuguese Civil Code only)
- Schedule PTI (only if REIT/InvIT/AIF distribution received)
- Schedule 80DD/80U (only with disability claim)
- Schedule AMT/AMTC (only in old regime with specific deductions, rarely applies to salaried)
- Schedule "Tax deferred on ESOP" (only for DPIIT-recognised start-up ESOP)
- Schedule 80GGC (only for political party contributions)

---

## Sources

- CBDT Notification 46/2026 dated 30-Mar-2026 (Form ITR-2 substitution)
- CBDT ITR-2 Validation Rules AY 2026-27 v1.0 (May-2026)
- Income Tax Dept: `https://www.incometax.gov.in/iec/foportal/downloads/income-tax-returns`
- `https://www.incometaxindia.gov.in/w/tax-rates` (rates)
- `https://www.incometax.gov.in/iec/foportal/sites/default/files/2026-03/Step by Step Guide FA FSI.pdf`
- `https://www.incometax.gov.in/iec/foportal/ais-faq` (AIS)
- Finance Act 2025 (Budget 2025) — slab, rebate, surcharge for FY 2025-26
