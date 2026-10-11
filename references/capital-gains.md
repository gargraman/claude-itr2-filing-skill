# Capital Gains — Classification & Computation for AY 2026-27 (FY 2025-26)

**Legal anchor:** Finance (No.2) Act 2024 rewrote capital-gains code effective 23-July-2024. FY 2025-26 is the first FULL year at post-Budget rates — no dual-rate split within FY 2025-26.

**Split-row treatment in AY 2026-27 Schedule CG:** Secondary sources conflict — some say the pre/post-23-Jul-2024 split rows are retained (nil for the pre-side in a genuine AY 2026-27 filing), others say they're consolidated away. `[SECONDARY-SOURCE]` — **open the actual utility before mapping numbers**; if split rows are present, put all FY 2025-26 gains in the post-23-Jul row.

---

## 1. Rate summary table (FY 2025-26)

| Asset class | Holding period cut-off (STCG↔LTCG) | STCG section / rate | LTCG section / rate |
|---|---|---|---|
| Listed equity share / equity-oriented MF unit / business trust unit (STT paid) | 12 months | **Sec 111A @ 20%** | **Sec 112A @ 12.5% on gains > ₹1.25L/year** |
| Unlisted equity share (Indian) | 24 months | Slab | **Sec 112 @ 12.5% (no indexation)** |
| **Foreign shares / RSUs / ESOPs / ESPP (any foreign exchange listing)** | **24 months** | **Slab** (Sec 111A NOT applicable — no STT on Indian recognised exchange) | **Sec 112 @ 12.5% (no indexation, no forex adjustment for residents)** |
| Immovable property (land/building) | 24 months | Slab | **Sec 112 @ 12.5% no-index OR 20% with-index (lower) — pre-23-Jul-2024 acquisitions, RESIDENT INDIVIDUAL / HUF ONLY** |
| Gold, jewellery, silver, unlisted bonds/debentures | 24 months | Slab | **Sec 112 @ 12.5% (no indexation)** |
| Listed bonds / debentures / securities (recognised Indian exchange, non-equity) | **12 months** | Slab | **Sec 112 @ 12.5% (no indexation)** |
| Debt mutual fund units acquired on/after 1-Apr-2023 | N/A — always STCG | **Sec 50AA — always STCG at slab regardless of holding period** | N/A |
| Debt mutual fund units acquired before 1-Apr-2023 | 24 months | Slab | Sec 112 @ 12.5% (no indexation post-23-Jul-2024) |
| Cryptocurrency / VDA | N/A | **Sec 115BBH @ 30% flat, no set-off, no c/f** | Same |
| Zero-coupon bonds (listed) | 12 months | Slab | Sec 112 @ 12.5% (no indexation) |

**Surcharge on capital gains:** Capped at **15%** for STCG u/s 111A, LTCG u/s 112, LTCG u/s 112A, and dividend income — even if base surcharge slab is 25% under new regime. Cess 4% on tax + surcharge.

**Sec 87A rebate does NOT apply** to income taxed at special rates (111A / 112 / 112A / 115BB / 115BBH). Rebate is only on slab-rate portion.

---

## 2. Decision tree for classifying a sale

```
Was it a Virtual Digital Asset (crypto/NFT)?
├── YES → Schedule VDA @ 30% u/s 115BBH. STOP.
└── NO
    │
    ├── Was it a debt mutual fund unit acquired on/after 1-Apr-2023?
    │   ├── YES → Sec 50AA. Always STCG at slab. Schedule CG row A2 (other STCG at slab).
    │   └── NO
    │       │
    │       ├── Is it a listed equity share / equity-oriented MF unit / business trust unit WITH STT paid on both sides (or STT on transfer for MF/BT)?
    │       │   ├── YES
    │       │   │   ├── Holding ≤ 12 months → Sec 111A @ 20%. Schedule CG row A1.
    │       │   │   └── Holding > 12 months → Sec 112A @ 12.5% > ₹1.25L. Schedule CG row B4 + Schedule 112A per-scrip.
    │       │   └── NO — no STT, or foreign-listed, or unlisted, or debt asset
    │       │       │
    │       │       ├── Is it a foreign-listed share / RSU / ESOP / ESPP / foreign bond?
    │       │       │   ├── Holding ≤ 24 months → STCG at slab. Schedule CG row A5.
    │       │       │   └── Holding > 24 months → Sec 112 @ 12.5% no-index. Schedule CG row B9.
    │       │       │       + Schedule FA A3 disclosure (unsold lots).
    │       │       │       + Schedule FSI/TR/Form 67 ONLY if foreign tax withheld on sale (US does NOT withhold on NRA stock sale — usually no FTC on the CG itself).
    │       │       │
    │       │       ├── Is it Indian unlisted equity share?
    │       │       │   ├── Holding ≤ 24 months → slab STCG. Schedule CG row A5.
    │       │       │   └── Holding > 24 months → Sec 112 @ 12.5% no-index. Schedule CG row B9.
    │       │       │
    │       │       ├── Is it immovable property (land or building)?
    │       │       │   ├── Holding ≤ 24 months → slab STCG. Schedule CG row A8.
    │       │       │   └── Holding > 24 months → Sec 112.
    │       │       │       └── Acquired before 23-Jul-2024 AND you are resident Individual/HUF?
    │       │       │           ├── YES → Choose lower of [12.5% no-index] and [20% with-index]. Schedule CG row B10 with the election flag.
    │       │       │           └── NO → 12.5% no-index only.
    │       │       │
    │       │       └── Everything else (gold, jewellery, art, pre-Apr-2023 debt MF, unlisted debt) → 24-month cut-off; STCG slab / LTCG 12.5% no-index. Schedule CG rows A6/A7 (STCG) or B5-B8 (LTCG).
```

---

## 3. Grandfathering for Sec 112A (listed equity / equity MF)

**Applicable ONLY to units/shares acquired on or before 31-Jan-2018.** Purpose: shield pre-Budget-2018 gains from the 10% (now 12.5%) LTCG tax.

**Formula (Sec 55(2)(ac)):**
```
Cost of acquisition = HIGHER OF
    (i)  Actual cost of acquisition
    (ii) LOWER OF
         (A) FMV per unit on 31-Jan-2018 × units
         (B) Full value of consideration (sale price)
```

**Practical implication:** If you bought a share pre-1-Feb-2018 at ₹100 and its 31-Jan-2018 close was ₹500, and you sold it at ₹800 — cost = max(100, min(500, 800)) = ₹500. LTCG = ₹300 (not ₹700).

**FMV source:** For listed equity, the highest quoted price on 31-Jan-2018 on the exchange where it is principally listed. For equity-oriented MF units — NAV as on 31-Jan-2018 published by AMC. Retrieve from BSE/NSE historical or from fund house.

**In Schedule 112A:**
- Row-level flag: acquired on-or-before 31-Jan-2018 (`1a=EQ` code) vs after (`1a=EA` code).
- Post-31-Jan-2018 lots may be consolidated in one row (`ISIN=INNOTREQUIRD`, `name=CONSOLIDATED`, `code=AE`) — CBDT optionality from 19-Jul-2019.
- Pre-31-Jan-2018 lots MUST be per-scrip / per-lot; cannot be consolidated.

---

## 4. RSU / ESOP / ESPP flow — Indian tax perspective

> **Caveat before you read §4:** Two treatments below are **industry practice, not on-point CBDT circular** — they are widely applied and have not (yet) been challenged at scale, but a scrutiny officer could take a different view:
> 1. **Foreign-listed shares (NYSE/NASDAQ/LSE) classified as "unlisted" for Indian CG.** Follows from SCRA §2(f) definition of "recognised stock exchange" being India-only, and is the settled position across Big-4 advisories and ITAT reads (Cairn UK Holdings, Legatum Ventures). No CBDT circular.
> 2. **RSU perquisite FMV = foreign-exchange vest-day close × SBI TTBR**, instead of the SEBI Cat-I merchant-banker valuation strictly required by Rule 3(8)(iii) for shares not listed on an Indian recognised exchange. Every US MNC employer uses the vest-day-close method in Form 12BA; scrutiny risk on this is real but uncrystallised.
>
> If the user is a HNI, near an audit trigger, or wants a conservative filing — flag both to them and consider obtaining the Rule 3(8)(iii) valuation for material vests.

### 4a. Vesting (Sec 17(2)(vi) — Perquisite)

- **Taxable event:** Vest date for RSU (nil strike); Exercise date for stock option.
- **Perquisite value = (FMV on vest/exercise date − amount paid) × shares.** For plain RSU, exercise price = 0, so full FMV = perquisite.
- **FMV rule (Rule 3(8)(iii)):** for shares NOT listed on an Indian recognised stock exchange (RSE per SCRA), strict reading requires **SEBI Cat-I Merchant Banker valuation** dated not more than 180 days before the vest.
- **Industry practice** (Google/Meta/Amazon/most MNCs): use foreign-exchange closing price on vest date × SBI TT-buying rate on vest date × shares. This is a **technical non-compliance with Rule 3(8)(iii) that has been widely tolerated**; there is no CBDT circular sanctioning it. Employer typically reports this value in Form 12BA. If your employer used this method, use the same in the return.
- **Where reported:** Schedule S (salary) — auto-flows from Form 16 Part B / Form 12BA. Perquisite value is treated as taxable salary and slab-taxed.
- **TDS on perquisite:** Employer withholds TDS u/s 192 on the perquisite. Some employers sell shares to fund TDS (mandatory withholding); others require the employee to remit cash. Cross-check TDS in Form 16 Part A.

### 4b. Sale of vested shares (Sec 45)

- **Cost of acquisition = FMV taxed as perquisite** on vest date (Sec 49(2AA)). This is the "step-up" — you don't pay CG tax on the perquisite portion twice.
- **Holding period = from date of allotment (vest date)** — per Explanation 1(hb) to Sec 2(42A). NOT from grant date.
- **Classification: UNLISTED for Indian tax** (foreign exchange listing ≠ Indian recognised exchange under SCRA). So Sec 112A does not apply.
- **Rate:**
  - Holding < 24 months → STCG at slab (Schedule CG row A5)
  - Holding ≥ 24 months → LTCG @ 12.5% no-index (Schedule CG row B9)
- **No forex adjustment for residents** (only NR/RNOR get first proviso to Sec 48 benefit). Convert cost (perquisite FMV date × SBI TTBR that day) and sale (sale date × SBI TTBR that day) to INR separately; difference = INR gain, then apply 12.5%.
- **No indexation.**
- **Withholding by foreign broker:** For sale of shares, **US does NOT tax non-resident aliens on stock-sale gains** (IRC §865(a)) — so typically NO US tax withheld on the sale itself. Therefore no FTC claim, no Form 67 needed for the gain. **Dividends** and **interest** DO get withheld — separate flow.

### 4c. ESPP specific

- Two taxable events: (1) purchase (discount to FMV is perquisite), (2) sale (CG).
- Purchase-date FMV → perquisite → included in Form 16.
- Sale → cost = FMV at purchase; holding from purchase date; same 24-month/12.5% no-index rule.

---

## 5. Section 112A specifics for Schedule 112A

- **Threshold — reporting:** NONE. Every 112A transaction reported. The ₹1.25L exemption is applied downstream in tax computation (Part B-TTI).
- **Threshold — tax:** ₹1,25,000 exempt per taxpayer per FY (aggregate, not per scrip). Balance @ 12.5%.
- **Excess above ₹1.25L flows to Schedule SI** (special-rate income).
- **Sec 87A rebate NOT available** on this LTCG (marginal relief also does not save it).
- **Loss under 112A** → LTCL, offset only against other LTCG (Sec 70(3)), c/f 8 years (Sec 74).

---

## 6. Loss set-off and carry-forward for capital gains

- **Sec 70(2):** STCL → set off against STCG and LTCG (same year).
- **Sec 70(3):** LTCL → set off against LTCG only (same year). Cannot offset STCG.
- **Sec 71(3):** Capital losses cannot offset non-capital heads (salary, HP, IFOS, business).
- **Sec 74(1):** Unabsorbed STCL c/f 8 AYs — set off against STCG or LTCG in future years. Unabsorbed LTCL c/f 8 AYs — set off against LTCG only in future years.
- **Sec 80 gatekeeper:** Loss c/f REQUIRES return filed by Sec 139(1) due date (31-Jul-2026 for AY 2026-27, non-audit). Belated return under 139(4) → **capital losses cannot be c/f** (though current-year set-off still allowed).
- **Sec 115BBH VDA:** NO set-off intra-VDA, NO set-off inter-source, NO carry-forward. VDA losses die at year-end.
- **Speculative loss (intraday cash equity):** Sec 73(1) — only against speculative profit; c/f 4 years (Sec 73(4)).

---

## 7. Documents required for Schedule CG

| Asset class | Documents |
|---|---|
| Listed equity / equity MF (Indian) | Broker/RTA Capital Gains statement for FY 2025-26 (contract-note-level). ISIN, date of acquisition, cost, date of sale, sale price, STT paid confirmation. Zerodha/Groww/ICICI Direct produce these as PDF/CSV. |
| Listed equity acquired pre-1-Feb-2018 | FMV as on 31-Jan-2018 for grandfathering. Broker's CG statement usually applies this. If not, source from BSE/NSE bhavcopy. |
| Foreign shares / RSU / ESOP / ESPP | Broker statement (E*Trade/Schwab/Fidelity/Shareworks) — 1099-B, transaction history CSV, vest/exercise reports, tax lots. FMV on vest date (perquisite date). Foreign broker gain-loss report per lot. SBI TT-buying rate on vest date and sale date (from RBI archive or SBI website). |
| Unlisted equity (Indian) | Sale agreement, share certificate, valuation report (Rule 11UA if related party), buyer PAN + payment trail. |
| Immovable property | Sale deed (buyer), original purchase deed (cost), stamp duty valuation certificate (Sec 50C), TDS certificate u/s 194IA (1% by buyer if consideration ≥ ₹50L), Form 26QB payment. Indexation cost table (CII notification) if electing 20% with-index for pre-23-Jul-2024 property. |
| Debt MF / bond | Fund/broker CG statement with acquisition date flag (pre/post 1-Apr-2023) for Sec 50AA classification. |
| VDA / crypto | Exchange statement (WazirX/CoinDCX/etc.) — per-transaction; date, coin, quantity, buy/sell price, INR value. Sec 194S TDS certificate (1% on transfer > ₹10K/₹50K). |

---

## 8. Common traps

1. **RSU perquisite double-counting.** The perquisite is taxed in Schedule S at vest. On sale, cost must include this perquisite value; else you'd pay tax twice on the same amount. Cross-check by hand for every vest lot sold in FY.
2. **Foreign share LTCG classified as 112A by mistake.** 112A requires STT on Indian exchange. NASDAQ/NYSE has no STT. Foreign shares go to Sec 112 → row B9, NOT B4.
3. **Missing FMV on 31-Jan-2018 for pre-2018 listed equity.** Without this, grandfathering fails and full pre-2018 gain becomes taxable.
4. **Debt MF misclassified as LTCG.** Any unit acquired on/after 1-Apr-2023 → Sec 50AA, always STCG at slab. Even if held 10 years.
5. **VDA loss set off against VDA gain.** Not allowed. Each VDA loss dies alone.
6. **Buy-back post 01-Oct-2024 treated as CG.** No — Finance (No.2) Act 2024 made buy-back proceeds a deemed dividend u/s 2(22)(f) in the shareholder's hands, taxable in Schedule OS. Cost of acquisition is a capital loss in Schedule CG row B8, allowed only if the deemed dividend is disclosed in Schedule OS row 1a(iii).
7. **Selling shares just before 12/24-month mark.** Confirm holding period exactly — day of purchase excluded, day of sale included (Sec 2(42A) computation), or as per exchange convention. A day short of 12 months on listed equity moves you from 12.5% to 20% (a 60% jump in tax on the gain).
8. **Belated return but material CG loss.** Filing 1 day after 31-Jul-2026 → capital losses die. Advance-pay tax and file on time even if some inputs are incomplete; revise later under 139(5) with better numbers.
9. **Not filing Form 67 before ITR for foreign dividend FTC.** CPC's automated 143(1) disallows FTC; recovery requires rectification / appeal. File Form 67 same day as ITR (or a day earlier), not weeks later.
10. **Real-estate sale — forgetting the pre/post-23-Jul-2024 election.** Property acquired before 23-Jul-2024 by resident individual/HUF → run BOTH computations (12.5% no-index AND 20% with-index using CII table) and pick the lower. Election is at the row level in Schedule CG B10.

---

## Sources

- Finance (No.2) Act 2024 — Sec 29 (111A), 30 (112), 31 (112A), 3(b) (2(42A) holding periods)
- Sec 55(2)(ac) — grandfathering
- Sec 50AA — Specified MF perpetual STCG
- Sec 115BBH — VDA
- Sec 17(2)(vi) — ESOP perquisite; Sec 49(2AA) — cost step-up
- Rule 3(8) — perquisite FMV determination
- CBDT FAQ 24-Jul-2024 on Finance (No.2) Act 2024
- CBDT Notification 46/2026 — ITR-2 AY 2026-27 (schema, split-row treatment)
