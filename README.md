# claude-itr2-filing-skill

A [Claude Code](https://claude.com/claude-code) / [Claude Agent SDK](https://docs.claude.com/en/api/agent-sdk) **skill** that guides a resident Indian individual through filing **ITR-2/3** for **AY 2026-27 (FY 2025-26)** — schedule by schedule, one at a time, with hard gates against guessed numbers and unconfirmed final JSON.

> **This is not tax advice.** It is a structured assistant that helps you *organise* your own filing. Every number and disclosure remains your responsibility. Have a qualified Chartered Accountant review before you file, especially if you have foreign assets, capital gains, or brought-forward losses.

---

## What it does

Walks a 7-step workflow:

1. **Intake & residency + form selection (ITR-2 vs ITR-3)** — Sec 6 test, PAN/Aadhaar, income & asset inventory, business/professional income screen.
2. **Schedule triage** — which schedules actually apply to you (branches by form).
3. **Per-schedule data collection** — one schedule per message, `NEEDS INPUT:` for anything missing.
4. **AIS/26AS/TIS reconciliation** — flag mismatches before they become notices.
5. **Regime comparison** — Old vs New, with Chapter VI-A availability and 87A rebate. For ITR-3 filers, the Form 10-IEA lifetime switch-back restriction is called out explicitly.
6. **Final calculation summary** — one page, both regimes, all sources.
7. **JSON generation** — only after a literal `CONFIRMED`.

### Scope

Handles:

**ITR-2 (stable):**
- Salary + Form 16 (single or multiple employers)
- Bank interest, dividends
- Prior-year losses (Schedule CYLA / BFLA / CFL)
- Capital gains — Indian equity, mutual funds, foreign shares, RSUs, ESOPs (Schedule 112A grandfathering, Sec 111A / 112 / 112A / 50AA / 115BBH classification)
- Foreign assets for a **Resident and Ordinarily Resident** — Schedule FA (calendar year), FSI, TR, Form 67, DTAA mechanics, Black Money Act awareness

**ITR-3 (BETA — needs practitioner review):**
- All of the above, PLUS:
- Business income — F&O (non-speculative, Sec 43(5)(d)), intraday equity (speculative, Sec 43(5)), freelance / consulting receipts, commission income, partner remuneration
- Turnover computation per ICAI Guidance Note 2022 (|profit| + |loss| method)
- Sec 44AA books requirement checks and Sec 44AB tax audit thresholds (business ₹1 Cr / ₹10 Cr digital; profession ₹50L; 6% profit test / 44AD opt-out audit)
- Presumptive taxation — Sec 44AD (business, 6%/8% deemed), Sec 44ADA (profession, 50% deemed), Sec 44AE (transport) — with explicit 5-year lock-out warnings
- Schedule BP / PL / BS / DPM / DOA / DEP / DCG / ICDS / IF / 44AD-ADA-AE
- Sec 40A(3), 43B, 40(a)(ia) disallowances; depreciation rates per IT Rules Appendix I
- **Form 10-IEA lifetime switch-back restriction** — permanent bar on Old regime after one switch-back is called out at both Step 5 and Step 6

Does **not** cover: ITR-1 (Sahaj), ITR-4 (Sugam — presumptive shortcut for TI ≤ ₹50L, no FA, no CG, one house), ITR-5/6/7, non-resident cases, or trust/HUF/company returns.

### Hard gates baked into the skill

- **Never generates final upload JSON** without an explicit `CONFIRMED` from the user against the full calculation.
- **Never guesses a number.** Missing input → `NEEDS INPUT: <exact ask>` and stops that schedule.
- **Every rate, section, threshold cited must trace to a reference file** in `references/`. Nothing invented from LLM memory — Indian tax rules change every Budget.
- **Verifies utility/schema version** before final JSON (ITR-2 utility v1.1, schema v1.1, Common Offline Utility v1.2.1 as of 30-Jun-2026).
- **Flags carry-forward-loss loss** if filing after 31-July-2026 (Sec 80 bar on belated returns).

---

## Install

### Global (all your Claude Code projects)

```bash
mkdir -p ~/.claude/skills
git clone https://github.com/gargraman/claude-itr2-filing-skill.git ~/.claude/skills/itr2-filing
```

### Per-project (only this repo)

From your project root:

```bash
mkdir -p .claude/skills
git clone https://github.com/gargraman/claude-itr2-filing-skill.git .claude/skills/itr2-filing
```

### Verify

In Claude Code, type `/` — you should see `itr2-filing` in the skills list. Or just say _"help me file my ITR-2"_ and Claude will invoke it automatically.

---

## Layout

```
SKILL.md                       # Entry point + 7-step workflow + hard gates
references/                    # Load-on-demand reference files
├── schedules.md              # All ITR-2 schedules + ITR-3 appendix, purpose, trigger rule, fields
├── regimes.md                # Old vs New — slabs, std ded, 87A, surcharge, Form 10-IEA lifetime bar
├── capital-gains.md          # Sec 111A/112A/112/50AA/115BBH, Schedule 112A grandfathering
├── foreign-assets.md         # Schedule FA, FSI, TR, Form 67, DTAA, Black Money Act
├── losses.md                 # CYLA/BFLA/CFL, Sec 70/71/72/73/74, 8-yr / 4-yr c/f, Sec 80 bar
├── documents-checklist.md    # What to gather before starting (incl. ITR-3 broker P&L, books)
├── business-income.md        # [ITR-3 BETA] Schedule BP/PL/BS, 44AA books, 44AB audit, 44AD/ADA/AE
├── fno-speculative.md        # [ITR-3 BETA] Sec 43(5) classification, ICAI 2022 turnover, broker Tax P&L
├── tax-savings.md            # Legit deductions/elections/timing levers, regime-tagged; incl. business-income levers
└── output-format.md          # Exact templates for Form Selection (T0), Intake (T1), Triage (T2), Per-Schedule (T3, T3B for ITR-3), Recon (T4), Regime (T5), Final Summary (T6), JSON (T7)
```

Only the reference file whose topic is active gets loaded — keeps context clean. ITR-3 files (`business-income.md`, `fno-speculative.md`) load only if Step 1 form selection determines ITR-3 is applicable.

---

## Version scope

- **AY 2026-27 / FY 2025-26** filing.
- Reference cut-off for tax rules: **30-June-2026**.
- Utility/schema versions (verified against `incometax.gov.in` downloads page on **17-July-2026**):
  - **ITR-2** — Excel utility v1.1 (30-Jun-2026), JSON schema v1.1 (30-Jun-2026)
  - **ITR-3** — Excel utility v1.1 (30-Jun-2026), JSON schema v1.1 (30-Jun-2026)
  - **Common Offline Utility** (ITR 1/2/3/4) v1.2.1 (01-Jul-2026)
  - Notification 46/2026
  - Re-verify before generating JSON if today is materially later than the verification date above — utility bumps mid-season are routine.
- Filing due dates:
  - **Non-audit individual (ITR-2, or ITR-3 without Sec 44AB audit): 31-July-2026** — **this deadline has now passed; such filers are in the belated/revised window only, until 31-Dec-2026 (see below), which forfeits loss carry-forward and forces the New regime.**
  - Audit case (ITR-3 with Sec 44AB audit): **31-October-2026**, with Form 3CB+3CD due **30-September-2026**.
  - Belated/revised: **31-December-2026** regardless of category — but a belated return **forfeits carry-forward of capital, business, and speculation losses (Sec 80)** and **forces New regime**.

**BETA warning for ITR-3:** `business-income.md` and `fno-speculative.md`, plus every ITR-3-specific block in the other reference files (schedules.md appendix, output-format.md Template 3B, tax-savings.md §5B), were drafted from the Income-tax Act 1961, Finance Act 2025, ICAI Guidance Note 2022, and mainstream practitioner sources — but have **not** been bit-verified against the live AY 2026-27 ITR-3 utility, Instructions PDF, or reviewed by a practising CA. Sections marked `[NEEDS-CA-REVIEW]` in those files require CA sign-off. For any ITR-3 filing produced via this skill, treat the final calculation as a draft for CA review, not a signed opinion.

If you're filing for a different AY, this skill is not for you — Indian tax rules change every Budget and the references would be stale.

---

## Contributing

PRs welcome, especially:

- Updates for the next AY (rate changes, new schedule fields, utility version bumps).
- Additional legitimate tax-saving levers for `tax-savings.md`.
- Corrections to any section/rate citation — please include the source (incometax.gov.in circular, Finance Act, or reputable practitioner site).

Open an issue first for anything that changes the 7-step workflow or the hard gates.

---

## License

MIT — see [LICENSE](LICENSE).

---

## Disclaimer

Not affiliated with the Income Tax Department of India or Anthropic. Use at your own risk. The author accepts no liability for filing errors, penalties, notices, or missed disclosures. **When in doubt, consult a Chartered Accountant.**
