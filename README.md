# claude-itr2-filing-skill

A [Claude Code](https://claude.com/claude-code) / [Claude Agent SDK](https://docs.claude.com/en/api/agent-sdk) **skill** that guides a resident Indian individual through filing **ITR-2** for **AY 2026-27 (FY 2025-26)** — schedule by schedule, one at a time, with hard gates against guessed numbers and unconfirmed final JSON.

> **This is not tax advice.** It is a structured assistant that helps you *organise* your own filing. Every number and disclosure remains your responsibility. Have a qualified Chartered Accountant review before you file, especially if you have foreign assets, capital gains, or brought-forward losses.

---

## What it does

Walks a 7-step workflow:

1. **Intake & residency** — Sec 6 test, PAN/Aadhaar, income & asset inventory.
2. **Schedule triage** — which ITR-2 schedules actually apply to you.
3. **Per-schedule data collection** — one schedule per message, `NEEDS INPUT:` for anything missing.
4. **AIS/26AS/TIS reconciliation** — flag mismatches before they become notices.
5. **Regime comparison** — Old vs New, with Chapter VI-A availability and 87A rebate.
6. **Final calculation summary** — one page, both regimes, all sources.
7. **JSON generation** — only after a literal `CONFIRMED`.

### Scope

Handles:

- Salary + Form 16 (single or multiple employers)
- Bank interest, dividends
- Prior-year losses (Schedule CYLA / BFLA / CFL)
- Capital gains — Indian equity, mutual funds, foreign shares, RSUs, ESOPs (Schedule 112A grandfathering, Sec 111A / 112 / 112A / 50AA / 115BBH classification)
- Foreign assets for a **Resident and Ordinarily Resident** — Schedule FA (calendar year), FSI, TR, Form 67, DTAA mechanics, Black Money Act awareness

Does **not** cover: ITR-1/3/4, business/professional income, presumptive taxation, non-resident cases, or trust/HUF/company returns.

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
├── schedules.md              # All ITR-2 schedules, purpose, trigger rule, fields
├── regimes.md                # Old vs New — slabs, standard deduction, 87A, surcharge
├── capital-gains.md          # Sec 111A/112A/112/50AA/115BBH, Schedule 112A grandfathering
├── foreign-assets.md         # Schedule FA, FSI, TR, Form 67, DTAA, Black Money Act
├── losses.md                 # CYLA/BFLA/CFL, Sec 70/71/74/73, 8-yr c/f, Sec 80 bar
├── documents-checklist.md    # What to gather before starting
├── tax-savings.md            # Legit deductions/elections/timing levers, regime-tagged
└── output-format.md          # Exact templates for each step's output
```

Only the reference file whose topic is active gets loaded — keeps context clean.

---

## Version scope

- **AY 2026-27 / FY 2025-26** filing.
- Reference cut-off: **30-June-2026**.
- Utility/schema versions cited: ITR-2 Excel v1.1, JSON schema v1.1, Common Offline Utility v1.2.1 (01-Jul-2026), Notification 46/2026.
- Filing due date: **31-July-2026** (non-audit individual). Belated/revised: **31-December-2026**.

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
