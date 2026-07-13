# Foreign Assets & Income — Schedules FA, FSI, TR + Form 67 (AY 2026-27)

**Applicability:** ROR (Resident and Ordinarily Resident) only. RNOR and NR do NOT file Schedule FA. RNOR files FSI/TR only for foreign income that IS taxable in India (business controlled from India, profession set up in India — Sec 5(1)(c) proviso).

---

## 1. Schedule FA — Foreign Assets disclosure

### 1a. Reporting period — CALENDAR YEAR, not FY

**For AY 2026-27, the reporting window is 1-Jan-2025 to 31-Dec-2025** (calendar year 2025). This is a common trap — the rest of the ITR uses FY 2025-26 (1-Apr-2025 to 31-Mar-2026), but Schedule FA alone uses CY 2025.

Basis: since AY 2020-21, "relevant accounting period" for Schedule FA = calendar year ending 31-Dec of the year immediately preceding the FY of filing. (For AY 2026-27, filing FY = 2026-27, previous CY = 2025.)

### 1b. Sub-tables

**A1 — Foreign Depository Accounts (foreign bank accounts)**
Per account: Country + Country Code, Name of financial institution, Address, ZIP, Account number, Status (Owner / Beneficial owner / Beneficiary), Account opening date, **Peak balance during the period** (in foreign currency + INR), **Closing balance on 31-Dec-2025** (foreign currency + INR), Gross interest paid/credited during the period.

**A2 — Foreign Custodial Accounts (foreign brokerages: E*Trade, Schwab, Fidelity, IB, Shareworks, Robinhood, etc.)**
Same columns as A1. One row per broker account. The broker cash-sweep is sometimes A1, sometimes A2 — practical approach: if the broker holds cash separately in an FDIC-insured sweep account, disclose that portion as A1 and the securities portion as A2. If integrated (single account), disclose the whole as A2.

**A3 — Foreign Equity and Debt Interest (unsold RSUs, ESPP shares held, direct-purchase foreign stocks, foreign bonds)**
Per holding: Country, Name of entity, Address of entity, Nature of entity (listed company / LLC / etc.), Date of acquisition (vest date for RSU, purchase date for direct buys), **Initial value** (cost = FMV_vest × shares × SBI TTBR on vest date), **Peak value during CY 2025** (peak price × shares × SBI TTBR on peak date), **Closing value on 31-Dec-2025** (closing price × shares × SBI TTBR on 31-Dec), Total gross amount paid/credited (dividends), Total gross proceeds from sale/redemption during CY 2025.

- Consolidation: A3 is generally per-lot. If you have 20 RSU vests over 4 years, you have 20 rows (though ITAT practice tolerates aggregation by grant if the initial value column is documented — no formal CBDT sanction).

**A4 — Foreign Cash Value Insurance / Annuity Contract**
Per contract: Country, Institution, Policy number, Date, Cash surrender value at year-end.

**B — Financial Interest in any Entity**
Beneficial interest, partnership / LLC / trust interest without direct account. Per entity: Country, Name, Nature of interest, Date acquired, Total investment cost, Income from such interest during CY 2025, Nature of income.

**C — Immovable Property held outside India**
Per property: Country, Address, Ownership status, Date acquired, Total investment cost, Income derived (rent) during CY 2025.

**D — Any Other Capital Asset**
Anything not fitting A1–C: foreign art, jewellery held abroad, non-financial collectibles, crypto held on foreign custodial exchanges (Coinbase, Kraken — arguably A2 if custodial, D if self-custody wallet).

**E — Signing Authority in any account**
Foreign bank/broker where you are not the beneficial owner but have signing authority (rare for individuals — e.g., signatory on employer's foreign account).

**F — Trusts (settlor / beneficiary / trustee)**
Foreign trusts. Rare.

**G — Any other income derived from a source outside India not disclosed above**
Catch-all — foreign consulting income, royalties, etc.

### 1c. Threshold — NONE for individuals

**Every foreign asset must be reported, regardless of value.** A $1 dormant broker account is reportable. There is no de-minimis.

### 1d. Penalty — Black Money Act 2015

- **Sec 42:** Failure to furnish return with foreign assets (ROR duty) → **₹10 lakh** flat penalty.
- **Sec 43:** Furnishing inaccurate/incomplete FA particulars in a filed return → **₹10 lakh** flat penalty.
- **Sec 41:** Tax @ 30% + penalty @ 300% of tax on undisclosed foreign income/assets.
- **Sec 50/51:** Prosecution — rigorous imprisonment 6 months to 7 years + fine.

**Amendment effective 1-Oct-2024** (Finance (No.2) Act 2024): Sec 42/43 penalty relief where aggregate value of foreign asset(s) other than immovable property does not exceed **₹20 lakh**. Immovable property has no such relief.

**Key distinction:** The ₹20L threshold is **penalty relief only** — the disclosure obligation itself is unchanged (still no threshold). If you have a $50 broker account and don't disclose, the ₹10L penalty may be waived but you have still committed a Sec 42/43 default.

**Enforcement:** CBDT NUDGE campaigns (Nov 2024, Nov 2025) using CRS / FATCA / AEOI data from foreign tax authorities. First campaign disclosed ₹29,208 Cr of previously-undisclosed foreign assets across 24,678 taxpayers. Assume the department has the data.

### 1e. Currency conversion — Rule 115

- Balances (peak, closing) — SBI **TT-buying rate** on the specified date.
- Income (dividend, interest) — SBI **TT-buying rate on the last day of the month immediately preceding the month in which the income accrued** (Rule 115).
- **Historical rates:** RBI reference-rate archive `https://www.rbi.org.in/scripts/ReferenceRateArchive.aspx` OR SBI TTBR archive via SBI corporate site.

### 1f. Where common items go

| Item | Sub-table |
|---|---|
| US brokerage (Schwab, E*Trade) — the account itself | A2 |
| Cash sweep inside brokerage | A2 (or A1 if separately identifiable and FDIC-insured) |
| Vested unsold RSU / ESPP shares in that brokerage | A3 (per lot) |
| Foreign checking / savings account | A1 |
| Direct-purchase Apple/Tesla shares via foreign broker | A3 |
| Crypto on Coinbase / Kraken / Binance (foreign) | A2 (custodial) OR D (if self-custody wallet abroad — rare) |
| Foreign whole-life insurance / annuity | A4 |
| Foreign private company shares / LLC interest | B |
| Foreign apartment / house | C |
| Foreign gold in vault abroad | D |
| Signatory on employer's overseas account | E |

---

## 2. Schedule FSI — Foreign Source Income

**Purpose:** Country-wise breakdown of income accrued outside India for ROR, with tax paid outside India and relief claimed.

**Trigger:** ROR + any foreign-source income (foreign dividend, foreign interest, foreign salary, foreign rent, foreign CG on which foreign tax was paid).

**Row per (country, head of income):**
| Field | Notes |
|---|---|
| Country Code | ISO 3-letter (USA=840, UK=826 — CBDT uses numeric ISO 3166) |
| Country Name | Auto from code |
| Taxpayer Identification Number (TIN) in foreign country | SSN / ITIN / EIN. If none, passport number. |
| Head of income under which foreign income is taxable in India | Salary / HP / Business / CG / OS |
| Income from outside India (INR) | Grossed up in INR using Rule 115 |
| Tax paid outside India (INR) | Foreign tax paid on this slice, converted to INR |
| Tax payable on such income under normal Indian provisions | Indian tax on this slice, calculated marginally |
| Tax relief available in India | Lower of (i) foreign tax paid or (ii) Indian tax on this slice — DTAA method depends on Article (usually "ordinary credit" for India-US Art 25(2)(a)) |
| Relevant Article of DTAA | e.g., India-US Art 10 (dividend), Art 11 (interest), Art 25 (relief) |
| Applicable section for relief | Sec 90 (with-DTAA country), Sec 90A (specified associations), Sec 91 (no-DTAA country) |

**Key mechanics:**
- **Dividend from US-listed stock (e.g., AAPL held via Schwab):** US withholds **25%** under India-US DTAA Art 10(2)(b) portfolio rate (post W-8BEN; default 30% for NRA without treaty). Grossed-up dividend goes in Schedule OS row 1a(i). FSI row: income = grossed-up INR dividend, foreign tax = 25% × dividend in INR, Indian tax = slab × dividend, relief = min. DTAA Art 10.
- **Interest from foreign bank:** Similar treatment — but US bank deposit interest paid to NRA is **exempt from US tax** (IRC §871(i)(2)(A)) → no foreign tax withheld → no FTC → full amount slab-taxed in India. Only reported in Schedule OS and Schedule FA A1. No FSI entry needed.
- **Capital gain on US stock sale:** US does **NOT** tax NRA on stock-sale gains → no US withholding → no FTC. Only reported in Schedule CG (row B9 or A5) and Schedule FA A3 (if any lot still unsold at CY-end). NO FSI entry needed.
- **Foreign salary during a portion of FY (was NR then became R):** if foreign salary earned during period when R status hadn't triggered, it's outside Indian tax net entirely (unless received in India). If earned as ROR — full India tax + FTC via FSI.

---

## 3. Schedule TR — Summary of Tax Relief

**Purpose:** Country-wise summary aggregating Schedule FSI.

**Row per country:**
| Field | Notes |
|---|---|
| Country code + name | Same as FSI |
| Taxpayer Identification Number | Same as FSI |
| Total taxes paid outside India (₹) | Sum of Schedule FSI col v for this country |
| Total tax relief available (₹) | Sum of Schedule FSI col vii for this country |
| Section under which relief claimed | 90 / 90A / 91 |

**Portal validation:** Sums must reconcile with Schedule FSI totals. If they don't, portal shows a warning (not a hard block, but CPC will use FSI numbers).

**Also disclose:** Whether tax paid outside India was refunded during FY (if yes, that becomes income in the year of refund under Sec 155).

---

## 4. Form 67 — MANDATORY before ITR to claim FTC

**Legal basis:** Rule 128(9), as substituted by CBDT Notification 100/2022 dated 18-Aug-2022 (retrospective 1-Apr-2022).

**Text (Rule 128(9)):**
> "Form No. 67 … shall be furnished on or before the end of the assessment year relevant to the previous year in which the income … has been offered to tax or assessed to tax in India and the return for such assessment year has been furnished within the time specified under sub-section (1) or sub-section (4) of section 139."

**For FY 2025-26 (AY 2026-27):**
- File Form 67 online on the portal (Services → Statutory Forms → File Now → Form 67).
- Deadline: **on or before 31-Mar-2027** (end of AY), provided ITR is filed by then under 139(1) or 139(4).
- **Practical:** file Form 67 on the SAME DAY as ITR (or a day earlier). CPC's automated 143(1) processing routinely disallows FTC if Form 67 is filed after ITR upload — recovery requires rectification u/s 154 or appeal.

**Form 67 structure:**
- **Part A:** Country, source of income, income (INR), tax paid outside India (INR + foreign currency), tax relief claimed, DTAA article.
- **Part B:** Subsequent refund of foreign tax (report in the year of refund).
- **Verification** — DSC or EVC.
- **Attachments (Rule 128(8)):**
  - Certificate from foreign tax authority OR
  - Certificate from person deducting foreign tax OR
  - Self-signed statement + acknowledgement of foreign tax payment (Form 1042-S for US, W-2 for US employment, foreign tax return, foreign bank tax statement).

**Case law:** Madras HC (Duraiswamy Kumaraswamy, WP 5834/2022, 6-Oct-2023) and multiple ITAT benches held Rule 128(9) directory, not mandatory — Rules cannot override the Act/DTAA. But the taxpayer must litigate to recover; file on time.

---

## 5. RSU / ESOP flow — end-to-end with tax numbers

Example: 100 Google RSUs vest on 15-May-2025. Google stock closes at $170 that day; SBI TTBR = ₹84/USD. Employer withholds 22 shares to fund TDS.

### Vest (FY 2025-26)
- **Perquisite u/s 17(2)(vi):** 100 × $170 × ₹84 = **₹14,28,000**
- Reported in Schedule S (auto from Form 16 Part B + Form 12BA)
- TDS: 22 shares × $170 × ₹84 = ₹3,14,160 (employer deposits under Sec 192; appears in Form 16 Part A)
- 78 shares net (worth ₹11,13,840) delivered to broker account
- **Schedule FA A3 entry (for CY 2025 disclosure):** Google Inc. — cost ₹14,28,000 (78 shares actually × cost basis ₹14,28,000 / 100 × 78 = ₹11,13,840, but strict reading is initial value of what YOU received = 78 shares × FMV_vest × TTBR = ₹11,13,840; some practitioners report full 100 × FMV but the 22 sold-to-cover are gone by end of vest day so 78 is defensible). Peak/closing values as per CY 2025 price moves.

### Sale — Case 1: Sold on 20-Aug-2025 at $180 (holding < 24 months)
- Sale value: 78 × $180 × ₹85 (TTBR that day) = ₹11,93,400
- Cost (Sec 49(2AA)): 78 × $170 × ₹84 = ₹11,13,840
- **STCG at slab:** ₹79,560 (Schedule CG row A5)
- US tax on sale: NIL (§865(a)) → no FTC, no FSI/TR/Form 67 needed for this
- Schedule FA A3 row for CY 2025: gross proceeds from sale column = ₹11,93,400

### Sale — Case 2: Sold on 20-Aug-2027 at $200 (holding > 24 months)
- Sale value: 78 × $200 × ₹87 = ₹13,57,200
- Cost (Sec 49(2AA)): 78 × $170 × ₹84 = ₹11,13,840
- **LTCG u/s 112 @ 12.5% no-index:** ₹2,43,360 gain → tax = ₹30,420 + surcharge (if any, capped 15%) + cess
- Schedule CG row B9

### Dividend from Google (unusual — Alphabet started paying dividends in 2024)
- Say $50 dividend paid on 15-Jun-2025; US withholds 25% = $12.50; net credited $37.50
- Grossed-up dividend: $50 × ₹84 = ₹4,200 → Schedule OS row 1a(i)
- Schedule FSI: Country USA, TIN (your SSN/ITIN), Head IFOS, Income ₹4,200, Tax paid outside ₹1,050 (25%), Indian tax on this slice (slab), Relief min. DTAA Art 10.
- Schedule TR: Country USA, Total paid ₹1,050, Total relief min.
- Form 67 filed with 1099-DIV or broker's tax summary attached.

---

## 6. DTAA key articles — India-US (most common)

| Income type | Article | Rate cap in source country |
|---|---|---|
| Dividend (portfolio) | Art 10(2)(b) | 25% (with W-8BEN) |
| Dividend (direct — ≥10% ownership) | Art 10(2)(a) | 15% |
| Interest (general) | Art 11(2)(b) | 15% (but US bank deposit exempt under IRC §871(i)(2)(A)) |
| Royalties / FTS | Art 12(2)(b) | 15% |
| Capital gains on shares | Art 13(6) | Contracting state may tax per domestic law → India taxes gain by residence; US doesn't tax NRA on stock sale → no double tax |
| Relief method | Art 25(2)(a) | Ordinary credit — India gives credit for US tax paid, capped at Indian tax on that slice |

Other DTAAs — UK Art 24, Singapore Art 25, UAE Art 24 (no personal income tax → no FTC issue). Check specific DTAA at `https://www.incometaxindia.gov.in/pages/international-taxation/dtaa.aspx`.

---

## 7. Residential status (Sec 6) — determination for FY 2025-26

### Sec 6(1) — Basic conditions:
- **(a) ≥ 182 days** in India during FY 2025-26, OR
- **(b) ≥ 60 days** in FY 2025-26 AND ≥ 365 days in preceding 4 FYs.

### Sec 6(1) Explanation 1 — carve-outs:
- **(a) Indian citizen leaving for employment abroad OR as crew member of Indian ship** → 60-day trigger becomes 182-day.
- **(b) Indian citizen or PIO visiting India** → 60-day trigger becomes 182-day, WITH proviso:
- **Proviso (FA 2020) — 120-day rule:** if the visiting Indian citizen / PIO has "total income other than income from foreign sources" > ₹15 lakh in the PY, 60-day trigger becomes 120-day (not 182). If in India 120-181 days, becomes RNOR.

### Sec 6(1A) — Deemed residency (FA 2020):
Indian citizen with total income (other than foreign source) > ₹15 lakh, **not liable to tax in any other country/territory by reason of domicile, residence, or similar criterion** → deemed resident (specifically RNOR, per Sec 6(6)(d)).

### Sec 6(6) — ROR vs RNOR:
You are **RNOR** if ANY of:
- (a) NR in 9 out of 10 preceding PYs, OR
- (b) In India ≤ 729 days during 7 preceding PYs, OR
- (c) Caught by 120-day proviso (visiting citizen/PIO staying 120-181 days), OR
- (d) Deemed resident under Sec 6(1A).

Otherwise, if not NR and not RNOR → **ROR**.

### Sec 5 — Scope of income:
| Status | Global income | Indian income | Foreign income from business controlled from India / profession set up in India |
|---|---|---|---|
| ROR | Yes | Yes | Yes |
| RNOR | Only Indian-sourced | Yes | Yes (limited) |
| NR | Only Indian-sourced | Yes | No |

**Schedule FA is filed by ROR only** (fourth proviso to Sec 139(1)).

### Practical: A typical Indian tech employee who moved back from US 3+ years ago and has spent 300+ days/year in India since → ROR. Confirm with day count for FY 2025-26 AND 4 preceding FYs before assuming.

---

## 8. Documents required — foreign assets / income

- **Foreign broker account statements** for CY 2025 (Jan-Dec) — Schwab/E*Trade/Fidelity year-end statement, monthly statements to compute peak.
- **Foreign broker 1099 series** for FY 2025-26 US income — 1099-DIV (dividends), 1099-INT (interest), 1099-B (sales), 1042-S (foreign investor withholding).
- **Vest reports** from RSU platform (Shareworks, E*Trade, Schwab EAC) — grant, vest, sell-to-cover, remaining shares.
- **Foreign bank statements** (Chase, BOA, HSBC, Wise, etc.) for CY 2025.
- **W-8BEN copy** filed with broker (to prove DTAA rate election).
- **US tax return** (Form 1040 / 1040-NR) if applicable, to reconcile FTC claim.
- **SBI TTBR archive** — dates of vest, dates of sale, 31-Jan/28-Feb/…/31-Dec of CY 2025 (for peak and closing balances).
- **Form 67 workings** — country, income, foreign tax, relief.
- **Passport travel history** — for residency day-count.

---

## Sources

- Black Money (Undisclosed Foreign Income and Assets) Act 2015 — Sec 41/42/43/50/51
- Finance (No.2) Act 2024 — amendment to BMA Sec 42/43 (₹20L de-minimis w.e.f. 1-Oct-2024)
- Rule 115 (currency conversion)
- Rule 128 (Foreign Tax Credit); CBDT Notification 100/2022 (Rule 128(9) substitution)
- CBDT Step-by-Step Guide FA/FSI (March 2026 version)
- India-US DTAA text; India-UK, India-Singapore, etc. at incometaxindia.gov.in/pages/international-taxation
- Sec 6 (residential status), Sec 5 (scope of income)
- Sec 17(2)(vi), Rule 3(8) (ESOP perquisite), Sec 49(2AA) (cost step-up)
- PIB PRID 2073820 (16-Nov-2024), PIB PRID 2195261 (27-Nov-2025) — CBDT NUDGE campaign results
