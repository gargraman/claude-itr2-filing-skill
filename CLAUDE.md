# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repo is

This is **not an application** — it is a [Claude Agent Skill](https://docs.claude.com/en/api/agent-sdk): a package of prose instructions (`SKILL.md` + `references/*.md`) that guides a resident Indian individual through filing **ITR-2 / ITR-3** for **AY 2026-27 (FY 2025-26)**. There is no code, no build system, no dependencies, no tests. "Editing this repo" means editing tax-domain markdown, and the correctness bar is factual/legal accuracy against Indian tax law — not a passing test suite.

There are no build, lint, or test commands. Validation is manual: re-read the changed reference against its cited source (incometax.gov.in circular, Finance Act 2025, ICAI Guidance Note), and check cross-references between files still line up (see "Invariants" below).

## Architecture

The whole skill runs on **progressive disclosure**, and that constraint drives every structural decision:

- **`SKILL.md`** is the only file loaded up-front. It holds the YAML frontmatter (`name`, `description` — the `description` is what triggers the skill, so it enumerates every keyword a user might type), the **hard gates**, the **load-on-demand table**, and the **7-step workflow**. It must stay small; it delegates all tax detail to `references/`.
- **`references/*.md`** are loaded *only when their topic becomes active* during the workflow. SKILL.md's load-on-demand table (the "When to load" column) is the contract: each reference is pulled in at a specific step or on a specific trigger, never preloaded. When adding or renaming a reference, update that table in the same change.

The 7 steps are sequential and gated — Intake+form-selection → Schedule triage → Per-schedule walkthrough → AIS/26AS reconciliation → Regime comparison → Final summary (the CONFIRMED gate) → JSON generation. Output at every step is governed by `references/output-format.md`, which defines numbered templates (Template 0–7); the workflow steps reference those templates by number rather than improvising layout.

### ITR-2 (stable) vs ITR-3 (BETA) — the central branch

Form selection in Step 1 forks the entire flow. ITR-2 content is considered verified; **ITR-3 content is BETA** and must carry that status. The ITR-3-specific references (`business-income.md`, `fno-speculative.md`) load *only* when Step 1 selects ITR-3, and ITR-3 additions inside otherwise-shared files (the `schedules.md` appendix, `output-format.md` Template 3B, `tax-savings.md` §5B) are explicitly sectioned off. Sections needing practitioner verification are tagged `[NEEDS-CA-REVIEW]`. Do not silently promote ITR-3 content to "stable" or merge it into the ITR-2 path.

### Reference files

| File | Domain |
|---|---|
| `schedules.md` | All ITR-2 schedules + ITR-3 appendix; filing order, trigger rules, portal fields |
| `regimes.md` | Old vs New slabs, 87A, surcharge, Form 10-IEA lifetime switch-back bar |
| `capital-gains.md` | Sec 111A/112A/112/50AA/115BBH, Schedule 112A grandfathering (NOT F&O/intraday) |
| `foreign-assets.md` | Schedule FA (calendar year), FSI, TR, Form 67, DTAA, Black Money Act, ROR test |
| `losses.md` | CYLA/BFLA/CFL, Sec 70–74, c/f periods, Sec 80 belated-return bar |
| `documents-checklist.md` | Intake document list (incl. ITR-3 broker P&L, books) |
| `business-income.md` | [ITR-3 BETA] Schedule BP/PL/BS, 44AA/44AB, 44AD/ADA/AE presumptive |
| `fno-speculative.md` | [ITR-3 BETA] Sec 43(5) classification, ICAI 2022 turnover, broker Tax P&L |
| `tax-savings.md` | Legit deductions/elections/timing levers, regime-tagged |
| `output-format.md` | Exact output templates 0–7 (incl. 3B for ITR-3) |

## Invariants to preserve when editing

These are load-bearing. Breaking one corrupts the skill's behaviour, not just its prose:

- **Every rate/section/threshold must trace to a reference file.** The skill forbids inventing numbers from LLM memory (Indian tax rules change every Budget). If you add a claim, add it to a reference with its source — don't leave it only in SKILL.md.
- **The hard gates in SKILL.md are the skill's guardrails** — no final JSON without a literal `CONFIRMED`, never guess a number (`NEEDS INPUT:` instead), verify utility/schema version before JSON. Don't weaken these when editing.
- **This is AY-2026-27-specific.** The reference cut-off (30-Jun-2026), utility/schema versions (ITR-2 v1.1 etc.), due dates (31-Jul / 31-Oct / 31-Dec 2026), and slab/rebate figures are all pinned to this assessment year. A change for a different AY is a different skill, not an edit.
- **Cross-file consistency.** Dates, version numbers, due-date rules, and the load-on-demand table appear in both `SKILL.md` and `README.md` (and sometimes a reference). Change them in lockstep. The `description` frontmatter in `SKILL.md` is the trigger surface — if scope changes, update the keyword list there too.

## Response conventions the skill enforces

When acting *as* this skill (not editing it): one schedule per message, cite the reference section for every number, mark open items as `NEEDS INPUT: <exact ask>` on their own line, refuse evasion (planning is fine), and never emit final JSON pre-CONFIRMED.
