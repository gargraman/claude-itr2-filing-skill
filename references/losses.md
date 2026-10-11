# Losses — Set-off, Carry-forward, and CYLA / BFLA / CFL Mechanics (AY 2026-27)

**Sections involved:** 70 (intra-head), 71 (inter-head), 72 (business loss c/f), 73 (speculation), 74 (capital loss c/f), 71B (HP loss c/f), 80 (Sec 139(1) filing gatekeeper), 115BBH(2) (VDA no-set-off), 115BAC(2)(i) (new-regime HP-loss restriction).

---

## 1. Same-year set-off (Sec 70 → Sec 71 → Schedule CYLA)

**Sec 70 — intra-head set-off (loss vs income within same head, same year):**
- Speculation loss → only against speculation profit (Sec 73(1)).
- STCL → against STCG AND LTCG (Sec 70(2)).
- LTCL → against LTCG only (Sec 70(3)).
- No intra-head bar for HP or OS.

**Sec 71 — inter-head set-off (loss remaining after Sec 70, applied to other heads):**
- **HP loss** — can offset any head (salary/business/OS/CG at slab), but **CAPPED at ₹2,00,000/year** (Sec 71(3A)). Balance c/f.
- **Business loss (non-speculation)** — can offset any head EXCEPT salary (Sec 71(2A)).
- **Capital loss** — CANNOT offset any non-capital head (Sec 71(3)). Only intra-head.
- **Speculation loss** — CANNOT offset any other head (Sec 73(1)).
- **Loss under IFOS** (rare — e.g., from horse-race owning, not gambling winnings) — can offset any head.

**New regime restriction (Sec 115BAC(2)(i)):** HP loss cannot be set off against salary or any other head under new regime. Forced to Schedule CFL for c/f under Sec 71B.

**VDA loss (Sec 115BBH(2)):** Cannot offset any income, including other VDA gains. Loss simply dies at year-end. No CYLA row, no CFL row for VDA loss.

---

## 2. Brought-forward loss set-off (Sec 72/74/71B/73 → Schedule BFLA)

Set off b/f losses from prior AYs against current year income of same head (with cross-head allowance for HP loss).

- **HP loss b/f (Sec 71B):** set off **only against current-year House Property income** in the 8 succeeding AYs. (The inter-head route and the ₹2L cap under Sec 71(3A) apply only to a *current-year* HP loss — not to a brought-forward HP loss.)
- **Business loss b/f (Sec 72):** offset against current-year business income only. Non-speculative → any business; speculative → speculative only (Sec 73(2)).
- **Speculation loss b/f (Sec 73(2)):** speculative income only.
- **STCL b/f (Sec 74):** against STCG or LTCG (current-year).
- **LTCL b/f (Sec 74):** against LTCG only (current-year).
- **Unabsorbed depreciation (Sec 32(2)):** perpetual c/f, any head except salary. Not typical for salaried ITR-2 filer.

---

## 3. Carry-forward periods (→ Schedule CFL)

| Loss type | Section | C/f period | Set off against (in future years) |
|---|---|---|---|
| HP loss | 71B | 8 AYs | HP income (per stricter reading); c/f survives even in belated return |
| Non-speculation business loss | 72 | 8 AYs | Business income |
| Speculation loss | 73(4) | **4 AYs** | Speculative business only |
| Loss from specified business (Sec 35AD) | 73A | Indefinite | Same specified business |
| STCL | 74 | 8 AYs | STCG or LTCG |
| LTCL | 74 | 8 AYs | LTCG only |
| Loss owning race horses | 74A | 4 AYs | Race-horse income |
| Unabsorbed depreciation | 32(2) | Indefinite | Any head except salary |
| VDA loss | 115BBH(2) | **NIL — cannot c/f** | — |

**Order in Schedule CFL:** year-wise (earliest first) so oldest losses are consumed first / expire first.

---

## 4. Sec 80 — Gatekeeper for carry-forward

**Sec 80:** No loss shall be carried forward under Sec 72(1), 73(2), 73A(2), 74(1), 74(3) or 74A(3) unless the return has been furnished within the time allowed under Sec 139(1).

**Practical consequence:** File belated (after 31-Jul-2026 for AY 2026-27 non-audit individual) → **capital loss, business loss, speculation loss cannot be carried forward**. Current-year set-off under Sec 70/71 is still allowed, but any unabsorbed portion dies.

**Exception:** **HP loss (Sec 71B)** is NOT listed in Sec 80's bar list — c/f is preserved even in belated return.

**Practical filing rule:** If you have any material capital loss to c/f, file by 31-Jul-2026 without fail. Better to file with approximate numbers on time (advance-pay estimated tax) and revise under Sec 139(5) later (revision available until 31-Dec-2026) than file belated and lose the loss.

---

## 5. Schedule CYLA — Current Year Loss Adjustment

Auto-computed once inputs are entered. **Rows = the head the loss originates in; columns = the head of income that can absorb it** (same year, after intra-head Sec 70 set-off). ✓ = allowed, ✗ = barred.

| Loss originates ↓ / absorbed by → | Salary | HP | Business (non-spec) | Speculation | STCG | LTCG | IFOS |
|---|---|---|---|---|---|---|---|
| **HP loss** | ✓¹ | — | ✓¹ | ✓¹ | ✓¹ | ✓¹ | ✓¹ |
| **Business loss (non-spec)** | ✗ (Sec 71(2A)) | ✓ | — | ✓ | ✓ | ✓ | ✓ |
| **Speculation loss** | ✗ | ✗ | ✗ | ✓ | ✗ | ✗ | ✗ |
| **STCL** | ✗ | ✗ | ✗ | ✗ | ✓ | ✓ | ✗ |
| **LTCL** | ✗ | ✗ | ✗ | ✗ | ✗ (Sec 70(3)) | ✓ | ✗ |
| **IFOS loss** | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | — |
| **VDA loss** | ✗ | ✗ | ✗ | ✗ | ✗ | ✗ | ✗ |

**¹ HP loss:** inter-head set-off is capped at **₹2,00,000 aggregate per year** (Sec 71(3A)); any balance carries forward. Under the **new regime** (Sec 115BAC(2)(i)) HP loss cannot be set off against any other head at all — it goes straight to Schedule CFL.

**Notes:**
- There is no "Salary loss" row — a loss cannot arise under the salary head.
- **Capital losses (STCL/LTCL) are intra-head only (Sec 71(3))** — they never reach salary, HP, business, or IFOS. STCL absorbs STCG then LTCG (Sec 70(2)); LTCL absorbs LTCG only (Sec 70(3)).
- **Only a business loss is barred from salary** (Sec 71(2A)); an IFOS or HP loss may offset salary.
- **VDA loss (Sec 115BBH(2))** absorbs nothing — not even other VDA gains — and does not carry forward.

## 6. Schedule BFLA — Brought Forward Loss Adjustment

Similar grid, plus year-wise:
- Row per (AY, loss head, unabsorbed amount b/f).
- Column: current-year income head against which set-off applied.

## 7. Schedule CFL — Carry Forward Losses

Year-wise, head-wise remaining balance to c/f to future AYs. Must be filled even if current-year set-off wiped all b/f (to close out the ledger).

**Age-out check:** Sec 74/72/71B c/f is 8 AYs immediately succeeding the AY of loss. For AY 2026-27:
- AY 2018-19 loss → available AY 2019-20 through AY 2026-27 (8th and final year — LAST CHANCE to absorb).
- AY 2017-18 loss or earlier → **out** for AY 2026-27.
Speculative loss c/f is only 4 AYs — for AY 2026-27, AY 2022-23 is 4th and final year; AY 2021-22 or earlier is out.

---

## 8. Documents needed for prior-year loss claim

For each prior-year loss being carried forward:
- **ITR-V / acknowledgement** of the AY in which loss was originally reported.
- Confirmation that original return was filed **within Sec 139(1) due date** (so Sec 80 wasn't triggered). Check the "date of filing" on the acknowledgement.
- Copy of Schedule CFL from that AY showing loss going out.
- If loss was revised in a subsequent revised return, latest revised acknowledgement + Schedule CFL.

**NEEDS INPUT if missing any of the above** — you cannot claim a c/f loss without the original ITR-V.

---

## 9. Common traps

1. **Belated return kills capital losses.** If you have ₹5L LTCL that would have offset next year's ₹5L LTCG saving ₹62,500 tax — filing 1 day late kills it. Non-negotiable deadline.
2. **VDA loss not carried forward.** ₹2L VDA loss in FY 2024-25 does NOT offset ₹2L VDA gain in FY 2025-26. Each year stands alone.
3. **HP loss under new regime.** ₹3L home-loan interest on let-out property → HP loss of ₹1L (after rent - 30% std ded - interest). Under new regime, cannot offset ₹40L salary; goes straight to CFL for 8-year c/f. Under old regime, offsets salary up to ₹2L.
4. **Speculation vs non-speculation confusion.** Intraday cash equity = speculation (Sec 43(5)). F&O = NON-speculation business (specific carve-out proviso to Sec 43(5)(d)). Different c/f rules — 4 vs 8 years. Different set-off eligibility too: F&O loss can offset any head except salary (Sec 71(2A)); intraday loss can ONLY offset speculative income. **Both losses require ITR-3, not ITR-2.** See `references/fno-speculative.md §2` and `references/business-income.md`.
5. **LTCL age-out check.** AY 2018-19 LTCL is in its 8th and FINAL year for AY 2026-27 — absorb this year or lose it. AY 2017-18 LTCL or earlier is already expired.
6. **Sec 80 exception for HP loss.** Losing capital-loss c/f in belated return is well-known; that HP loss survives is often overlooked. Confirm both if user is filing belated.
7. **STCG absorbs STCL first, then LTCL absorbs LTCG.** Order matters: use Sec 70(2) to absorb STCL against STCG first (both slab-rate benefits maxed), then any remaining STCL against LTCG (also useful — 20%/12.5% savings), then LTCL against LTCG only. Optimize order in the CG computation.

---

## Sources
- Sec 70, 71, 71B, 72, 73, 74, 74A, 80 — Income-tax Act 1961
- Sec 115BBH — VDA no set-off, no c/f
- Sec 115BAC(2)(i) — new-regime HP loss restriction
- ITR-2 AY 2026-27 Instructions PDF (once published) — CFL year-age-out
