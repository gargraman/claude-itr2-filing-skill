# Output Format Templates — ITR-2 Filing

These are the exact templates the SKILL.md workflow expects. Do not invent alternatives — the user has been told these formats will be used, and consistency across sessions matters.

Each template below has: **When to use**, the **template block**, and **rules for filling**.

---

## Template 1 — Intake Summary (Step 1 output)

**When to use:** End of Step 1 (intake & residency confirmation).

```
## Intake Summary — ITR-2 AY 2026-27 (FY 2025-26)

### CONFIRMED
- Assessment Year: AY 2026-27 (FY 2025-26)
- Residential status: <ROR / RNOR / NR>  [derived from Sec 6 day-count: <days FY 25-26>, prior 4 FY: <days>]
- PAN: <masked, last 4 chars>
- Aadhaar: <masked, last 4 chars>
- Employer(s): <n> [<Company A>, <Company B>...]
- Income sources declared: [Salary, Bank interest, Dividends, Capital gains (equity/foreign RSU/...), Prior-year losses c/f]
- Foreign assets during CY 2025: <YES / NO> [<brief list>]

### NEEDS INPUT
- NEEDS INPUT: <exact item 1>
- NEEDS INPUT: <exact item 2>
- ...

### CANNOT PROCEED IF
- <any hard blocker — e.g., "unable to confirm ROR status without passport day-count">
```

**Rules:**
- Mask PAN/Aadhaar in any output (last 4 digits only).
- One line per confirmed / open item. Do not narrate.
- If any `NEEDS INPUT` is present, STOP after this summary and wait for the user.

---

## Template 2 — Schedule Triage Table (Step 2 output)

**When to use:** End of Step 2 (deciding applicable schedules).

```
## Schedule Triage — AY 2026-27

| # | Schedule | Applicability | Trigger reason |
|---|---|---|---|
| 1 | Part A-GEN | APPLICABLE | Always |
| 2 | Schedule S — Salaries | APPLICABLE | Salary from <n> employer(s) |
| 3 | Schedule HP — House Property | NOT APPLICABLE / APPLICABLE / NEEDS INPUT | <reason> |
| 4 | Schedule CG — Capital Gains | APPLICABLE | Sold <equity/foreign shares/MF/property> during FY |
| 4a | Schedule 112A | APPLICABLE / NA | <any 112A transaction> |
| 4b | Schedule VDA | NA / APPLICABLE | <crypto transactions?> |
| 5 | Schedule OS — Other Sources | APPLICABLE | Bank interest ₹<>, Dividends ₹<> |
| ... | ... | ... | ... |
| 25 | Schedule AL | NEEDS INPUT | Depends on final TI > ₹1 Cr — verify at Step 6 |

### Applicable count: <n>   |   NA count: <n>   |   NEEDS INPUT count: <n>

### Order of walkthrough (Step 3):
1. Schedule S
2. Schedule OS
3. Schedule CG (+ 112A + VDA)
4. ...
```

**Rules:**
- Cite `references/schedules.md §<n>` for each trigger reason.
- Order in the walkthrough follows `references/schedules.md §Filing Order`.
- Any `NEEDS INPUT` in the triage → resolve before Step 3, or explicitly park with a reason.

---

## Template 3 — Per-Schedule Block (Step 3 output — ONE per message)

**When to use:** Each schedule during the schedule-by-schedule walkthrough. **One schedule per message.** Do NOT batch multiple schedules unless the user explicitly asks "continue through all pending" — even then, one block per schedule with visual separation.

```
### Schedule <code> — <Official Name>

**Why required for you**
<one-line trigger, citing the specific fact from intake — e.g., "You received ₹4,20,000 dividend from foreign broker (Schwab statement, 15-Jun-2025) → Schedule OS row 1a(i) + Schedule FSI row for USA">

**Reference:** `references/schedules.md §<n>`

**Documents needed**
- ✅ <document available>
- ⚠️ NEEDS INPUT: <document not yet provided>
- ...

**Portal fields (mandatory)**
| Field | Format constraint | Value |
|---|---|---|
| <Field name 1> | <e.g., DD/MM/YYYY, 12-char alphanumeric, INR whole rupees> | <value or NEEDS INPUT> |
| <Field name 2> | ... | ... |

**Inputs from you**
- CONFIRMED: <input> = <value> [source: <document / row>]
- NEEDS INPUT: <exact ask 1>
- NEEDS INPUT: <exact ask 2>

**Computation**
```
Line 1: <label> = ₹<amount>
Line 2: <label> = ₹<amount>
...
Final: <schedule total> = ₹<amount>
```

**Cross-checks**
- Should match <Form 16 Part B row X / AIS SFT-016 total / 26AS entry #Y>: <expected ₹>
- Reconciled: <YES / MISMATCH — see reconciliation table>

**Next schedule:** <Schedule code> — reply "continue" to proceed, or provide the NEEDS INPUT items above first.
```

**Rules:**
- Every rupee amount rounded to whole INR unless a portal field takes paisa.
- Currency conversion (foreign to INR) always cites the SBI TTBR date + rate.
- Every NEEDS INPUT is on its own line, greppable, with the EXACT ask (not "some more info").
- Do NOT proceed to the next schedule until user replies (either "continue" or provides missing inputs).

---

## Template 4 — AIS/26AS/Form 16 Reconciliation (Step 4 output)

**When to use:** After all income-source schedules (S, OS, CG) are drafted; before regime comparison.

```
## AIS / 26AS / Form 16 Reconciliation

### Table A — TDS Credit Reconciliation (Schedule 20B + 20C vs Form 26AS)
| Source (26AS) | TAN | Deductor | Amount TDS (₹) | Where claimed in ITR-2 | Match |
|---|---|---|---|---|---|
| Form 16 (Salary) | <TAN> | <employer> | <amount> | Schedule 20B row 1 | ✅ |
| 194A (Bank interest) | <TAN> | <bank> | <amount> | Schedule 20C row 1 | ✅ |
| 194 (Dividend) | <TAN> | <company/broker> | <amount> | Schedule 20C row 2 | ✅ / MISMATCH |
| 194S (VDA) | <TAN> | <exchange> | <amount> | Schedule 20C row 3 | ✅ / MISMATCH |
| ... | ... | ... | ... | ... | ... |
| **Total 26AS TDS** | | | ₹<sum> | ₹<sum claimed> | ✅ / MISMATCH ₹<delta> |

### Table B — Income Completeness (AIS SFT vs ITR-2 schedules)
| AIS entry (SFT code) | Nature | Amount (₹) | Where reported in ITR-2 | Match |
|---|---|---|---|---|
| SFT-018 | Salary paid | <> | Schedule S | ✅ |
| SFT-016 | Dividend | <> | Schedule OS row 1a(i) | ✅ / MISMATCH |
| SFT-005 | Interest (cooperative/bank) | <> | Schedule OS row 1b | ✅ |
| SFT-011 | MF transactions | <> | Schedule CG rows | ✅ |
| SFT-012 | Immovable property | <> | Schedule CG B10 | NA / ✅ |
| LRS outward remittance | | <> | Not income — cross-check foreign broker balance |  |
| Foreign remittance received | | <> | Schedule OS row 1a(i) / CG | ✅ / MISMATCH |

### Mismatches — resolve before filing
- **MISMATCH-1:** <exact description>. **Action:** <update ITR / raise AIS Feedback / attach clarifying note>.
- **MISMATCH-2:** ...

### Status
- Total mismatches: <n>
- Blocking mismatches: <n> — **DO NOT PROCEED TO STEP 5 UNTIL RESOLVED**
```

**Rules:**
- MISMATCH is a hard blocker. Do not skip past it. Either update numbers or explicitly document why the mismatch is acceptable (e.g., "AIS shows ₹1L bonus but Form 16 shows ₹95K net after employer correction — employer confirmed via email dd/mm").
- Auto-populated fields (dividend, interest) must still be verified by hand against source docs.

---

## Template 5 — Regime Comparison (Step 5 output)

**When to use:** After all schedules confirmed, before final summary.

```
## Regime Comparison — FY 2025-26

Reference: `references/regimes.md`

| Line | Old Regime (₹) | New Regime (₹) | Notes |
|---|---:|---:|---|
| Gross salary (Schedule S) | <> | <> | Same both |
| Less: Standard deduction u/s 16(ia) | (50,000) | (75,000) | |
| Less: HRA exempt u/s 10(13A) | (<>) | 0 | Old only |
| Less: LTA exempt u/s 10(5) | (<>) | 0 | Old only |
| Less: Prof tax u/s 16(iii) | (<>) | (<>) | Both |
| Net Salary | <> | <> | |
| Interest income (Schedule OS) | <> | <> | Same |
| Dividend income (Schedule OS) | <> | <> | Same |
| STCG @ 20% (Schedule CG A1) | <> | <> | Same, special rate |
| LTCG @ 12.5% (Schedule CG B4, > ₹1.25L) | <> | <> | Same, special rate |
| Other capital gains | <> | <> | |
| **Gross Total Income** | <> | <> | |
| Less: Chapter VI-A (VI-A schedule) | | | |
|   80C | (1,50,000) | 0 | |
|   80CCD(1B) | (50,000) | 0 | |
|   80CCD(2) employer NPS | (<>) | (<>) | Old 10% cap, New 14% cap |
|   80D | (<>) | 0 | |
|   Other (80G, 80TTA, etc.) | (<>) | 0 | |
| **Total Income** | <> | <> | |
| Slab tax on non-special income | <> | <> | Per slab table `regimes.md §1/§2` |
| Tax on STCG @ 20% | <> | <> | |
| Tax on LTCG @ 12.5% (post ₹1.25L) | <> | <> | |
| **Tax before rebate** | <> | <> | |
| Sec 87A rebate | (<>) | (<>) | Old: ₹12.5K if TI ≤ ₹5L; New: up to ₹60K if TI ≤ ₹12L. Not on special-rate. |
| Tax after rebate | <> | <> | |
| Surcharge | <> | <> | Slab per `regimes.md §3`; capped 15% on CG/dividend |
| Health & Ed Cess 4% | <> | <> | |
| **Total tax liability** | **<>** | **<>** | |
| Less: TDS (Sch 20B + 20C) | (<>) | (<>) | Same |
| Less: Advance tax + SA tax (Sch 20A) | (<>) | (<>) | Same |
| Less: TCS (Sch 20D) | (<>) | (<>) | Same |
| **Refund (+) / Payable (−)** | <> | <> | |

### Recommendation: <OLD / NEW> regime
**Delta:** ₹<amount> in favour of <regime>.
**Reason:** <one line — e.g., "New regime wins because 80C + 80D savings under old (~₹52K tax value) < wider slab bands under new (~₹1.2L tax value)">.

### Regime switch mechanics
- <If NEW>: default; leave Part A-GEN checkbox as "No" for opt-out. No Form 10-IEA needed (salaried, no business income).
- <If OLD>: toggle Part A-GEN "opting out of new regime u/s 115BAC" = YES. No Form 10-IEA needed (salaried, no business income). MUST file by 31-Jul-2026 — belated return forces new regime.
```

**Rules:**
- Every negative number in brackets `(₹X)`.
- Rebate 87A does NOT reduce tax on STCG/LTCG special-rate portions. Split calculation cleanly.
- Surcharge cap 15% on CG/dividend income even if base slab is higher.
- If deltas are within ₹5,000, mention that the choice is close and let the user decide.

---

## Template 6 — Final Summary (Step 6 output — the CONFIRMATION GATE)

**When to use:** After regime comparison, before JSON generation. **User must reply `CONFIRMED` before proceeding.**

```
## ITR-2 Final Summary — AY 2026-27 (FY 2025-26)

### A. Taxpayer
- Name: <>
- PAN: <masked>
- Aadhaar linked: YES
- Residential status: <ROR / RNOR>
- Regime elected: <OLD / NEW>

### B. Schedules filled — final numbers
| Schedule | Amount (₹) | Reference |
|---|---:|---|
| Schedule S — Salaries (net) | <> | `schedules.md §2` |
| Schedule HP — House Property | <> or NA | `schedules.md §3` |
| Schedule CG — Capital Gains (aggregate) | <> | `schedules.md §4` |
|   ↳ STCG u/s 111A | <> | |
|   ↳ LTCG u/s 112A (net of ₹1.25L exemption) | <> | |
|   ↳ LTCG u/s 112 (foreign shares/other) | <> | |
|   ↳ VDA gains u/s 115BBH | <> or NA | |
| Schedule OS — Other Sources | <> | `schedules.md §5` |
| Schedule EI — Exempt Income | <> | Disclosure only |
| Schedule CFL — Losses to c/f | <> | `losses.md` |
| Schedule FSI — Foreign Source Income | <> | `foreign-assets.md §2` |
| Schedule TR — Tax Relief claimed | <> | `foreign-assets.md §3` |
| Schedule FA — Foreign Assets count | <n> assets | `foreign-assets.md §1` |
| Schedule AL | NA / <TI > ₹1 Cr row count> | `schedules.md §25` |

### C. Deductions claimed (Chapter VI-A)
| Section | Amount (₹) | Regime | Legal ref |
|---|---:|---|---|
| 80C | <> | OLD | `regimes.md §2` |
| 80CCD(1B) | <> | OLD | ... |
| 80CCD(2) employer NPS | <> | BOTH | ... |
| 80D | <> | OLD | ... |
| 80G (with ARN) | <> | OLD | ... |
| ... | ... | ... | ... |
| **Total VI-A** | **<>** | | |

### D. Tax computation
| Line | Amount (₹) |
|---|---:|
| Total Income (Part B-TI) | <> |
| Tax before rebate | <> |
| Rebate u/s 87A | (<>) |
| Tax after rebate | <> |
| Surcharge | <> |
| Health & Ed Cess 4% | <> |
| **Total tax liability** | **<>** |
| Less: TDS (Salary + Others) | (<>) |
| Less: Advance / Self-Assessment tax | (<>) |
| Less: TCS | (<>) |
| Less: FTC (via Sch TR — Form 67 filed) | (<>) |
| **REFUND (+) / TAX PAYABLE (−)** | **<>** |

### E. Pre-filing checklist
- [ ] Form 67 filed online for FTC claim (Rule 128; reference: `foreign-assets.md §4`) — **Ack no: <>, Date: <>**
- [ ] Form 10-IEA filed for old-regime opt-out (only needed if business/profession income) — NA / Ack no: <>
- [ ] Advance tax and self-assessment tax paid — challans 280 uploaded
- [ ] AIS Feedback submitted for any disputed entries — <n> feedback items
- [ ] All Indian bank accounts listed in Schedule Bank Accounts
- [ ] Refund bank account marked (IFSC + Account No verified)
- [ ] E-verification method decided: <Aadhaar OTP / DSC / EVC>

### F. Documents to preserve for 8 years
- Form 16 (all employers)
- All bank / broker statements (Indian + foreign)
- Foreign broker Jan-Dec 2025 statements (for Schedule FA)
- 1099 series (US withholding) + Form 67 attachments
- Deduction proofs (rent receipts + landlord PAN, insurance receipts, 80G ARN certificates, NPS statements)
- SBI TTBR archive prints for vest/sale/CY-end dates
- Prior year ITR-V + Schedule CFL (for BFLA claim)

### G. Residual issues
- NEEDS INPUT items: **NONE** (must be zero to proceed)
- MISMATCH items: **NONE** (must be zero to proceed)

### H. CONFIRMATION GATE
Reply `CONFIRMED` to authorize final JSON generation for portal upload.
Or reply with any correction — I will revise this summary and re-request confirmation.

**I will NOT generate the upload JSON until you reply with `CONFIRMED` verbatim.**
```

**Rules:**
- If ANY `NEEDS INPUT` or `MISMATCH` remains, do not present this template as-is. Go back and resolve.
- Section H is non-negotiable. Do not shorten, paraphrase, or skip the CONFIRMED gate language.
- If user replies with corrections, revise and re-post the full summary — do not do partial patches.

---

## Template 7 — JSON Generation Output (Step 7 output — only after CONFIRMED)

**When to use:** After user replies with literal `CONFIRMED`.

```
## Final JSON — ITR-2 AY 2026-27

**Schema version used:** ITR-2 JSON schema v1.1 (as reported at time of writing)
**Utility version to validate against:** Common Offline Utility v1.2.1 (01-Jul-2026)
**Download the current utility from:** https://www.incometax.gov.in/iec/foportal/downloads/income-tax-returns

**File:** save the JSON below as `ITR2_<PAN>_AY202627.json`

```json
{
  "ITR": {
    "ITR2": {
      "CreationInfo": { ... },
      "Form_ITR2": { ... },
      "PersonalInfo": { ... },
      "FilingStatus": { ... },
      "ScheduleS": { ... },
      "ScheduleHP": { ... },
      "ScheduleCG": { ... },
      "Schedule112A": [ ... ],
      "ScheduleVDA": [ ... ],
      "ScheduleOS": { ... },
      "ScheduleCYLA": { ... },
      "ScheduleBFLA": { ... },
      "ScheduleCFL": { ... },
      "ScheduleVIA": { ... },
      "Schedule80G": { ... },
      "ScheduleSI": { ... },
      "ScheduleEI": { ... },
      "ScheduleFSI": [ ... ],
      "ScheduleTR1": { ... },
      "ScheduleFA": { ... },
      "PartB_TI": { ... },
      "PartB_TTI": { ... },
      "TaxPayments": { ... },
      "BankAccountDtls": { ... },
      "Verification": { ... }
    }
  }
}
```

### Next steps
1. Save JSON as `ITR2_<PAN>_AY202627.json`
2. Open Common Offline Utility v1.2.1 → Import → JSON → select saved file
3. Utility will validate all schedules → fix any errors flagged
4. Utility will produce a fresh JSON for upload
5. Upload on portal (Services → File Income Tax Return → AY 2026-27 → ITR-2 → Offline)
6. **File Form 67 online BEFORE ITR upload if claiming FTC** (already done per Step 6 checklist)
7. Upload ITR JSON → E-verify within 30 days
8. Download ITR-V acknowledgement → retain for records

### Reminder
- Filing deadline: **31-July-2026** (Sec 139(1))
- Belated deadline: 31-Dec-2026 (with Sec 234F fee + loss c/f forfeiture)
- Retain all supporting documents for **8 years** from end of AY
```

**Rules:**
- Only produce this template AFTER user typed literal `CONFIRMED` (or unambiguous equivalent like "confirmed", "yes proceed", "generate JSON").
- The JSON structure above is a skeleton. Populate every schedule the triage marked APPLICABLE with actual values from Step 3 walkthrough.
- Do NOT populate schemas that aren't in the current utility version — verify against the downloaded utility.
- Do NOT upload to the portal yourself; the user does the upload manually.

---

## Ordering summary

| Step | Template | Output type | Blocks next step? |
|---|---|---|---|
| 1 | Template 1 — Intake Summary | Full page | Yes — need CONFIRMED / NEEDS INPUT resolved |
| 2 | Template 2 — Schedule Triage | Table | Yes — resolve NEEDS INPUT |
| 3 | Template 3 — Per-Schedule Block | One per message | Each schedule waits for user reply |
| 4 | Template 4 — Reconciliation | Full page | Yes — resolve MISMATCH |
| 5 | Template 5 — Regime Comparison | Full page | Recommend regime; then proceed |
| 6 | Template 6 — Final Summary | Full page | **HARD GATE — require `CONFIRMED`** |
| 7 | Template 7 — JSON Generation | JSON + instructions | Terminal — user takes over |

---

## Style notes

- Rupee symbol: `₹` (not `Rs.` or `INR` in output — use ₹).
- Number formatting: Indian lakh/crore convention `12,50,000` not international `1,250,000`. Use commas correctly.
- Rounding: whole rupees in output tables. Portal may accept paisa in specific fields (rare) — flag those.
- Dates: `DD-MMM-YYYY` (e.g., `15-Jun-2025`) in prose; `DD/MM/YYYY` in portal-field format constraint tables.
- Percentages: `20%` not `20 %` or `0.20`.
- Currency conversion: always cite source (SBI TTBR) + date + rate.
- Section references: `Sec 112A` not `112A` alone or `Section 112A of the Income-tax Act, 1961`. Consistent short form.
- Reference file citations: `references/schedules.md §4` — always with the section anchor.
