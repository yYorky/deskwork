# Claude Code Session — aurisic-amortization

> Documents the exact context provided to Claude Code for this benchmark run.

## Context provided
- SKILL.md: `benchmarks/claude-code/SKILL.md`
- Task prompt: `benchmarks/tasks/aurisic-amortization/prompt.md`
- Reference files: `benchmarks/tasks/aurisic-amortization/reference-files/`
  - `Aurisic GL 1250.pdf` — GL trial balance for Account #1250 (Prepaid Expenses), Jan–Apr 2025
  - `Aurisic GL 1251.pdf` — GL trial balance for Account #1251 (Prepaid Insurance), Jan–Apr 2025
  - `Aurisic Invoices (1250) Jan 2025.pdf` — 24 vendor invoices received January 2025
  - `Aurisic Invoices (1250) Feb-Apr 2025.pdf` — 17 vendor invoices received February–April 2025
  - `Aurisic Invoices (1251) Jan-Apr 2025.pdf` — Good Insurance (21 invoices) + BCBS (4 monthly invoices)

## What was NOT provided
- Gold-standard deliverable (data integrity)
- GDPval marking rubric (data integrity)

## Session notes

Claude Code read all 5 PDF reference files using pdfminer (only PDF library available in the conda env).
Extracted all 41 invoices for Account #1250 and 25 invoices for Account #1251.

**Key decisions made during execution:**

1. **6-month default rule (Account #1250)**: No contract dates were printed on any vendor invoice. Applied the 6-month straight-line amortization default as specified in the task (invoices received in month M amortize over months M through M+5).

2. **Good Insurance — 12-month straight-line**: 21 invoices, all covering the policy period January 1 – December 31, 2025. Total premium $546,725.14 amortized equally over 12 months ($45,560.43/month).

3. **BCBS — monthly billing treatment**: 4 invoices received Jan–Apr 2025 at $5,493.27 each. Each invoice is received one month before coverage begins (Jan invoice → Feb coverage). Balance = invoice amount in month received; $0 in all subsequent months (expensed in following month).

4. **GL rounding adjustment**: Individually rounded per-line balances summed to 1–5 cents off the authoritative GL targets per month. A "GL Rounding Adjustment" row was added to each schedule to absorb the discrepancy, ensuring all 8 month-end balances reconcile exactly to GL targets (all variances $0.00).

**GL Reconciliation (Self-Verification):**
| Account | Jan | Feb | Mar | Apr |
|---------|-----|-----|-----|-----|
| 1250 Target | $518,934.86 | $426,673.13 | $473,655.55 | $559,377.61 |
| 1250 Result | PASS | PASS | PASS | PASS |
| 1251 Target | $506,657.98 | $461,097.55 | $415,537.13 | $369,976.70 |
| 1251 Result | PASS | PASS | PASS | PASS |

**Output**: `benchmarks/claude-code/aurisic-amortization/output/Aurisic_Prepaid_Amortization_Apr2025.xlsx`
- Tab 1: Prepaid Summary (account-level YTD amortization and Apr 30 balances)
- Tab 2: Prepaid Expenses #1250 (invoice-level schedule with monthly balances Jan–Apr)
- Tab 3: Prepaid Insurance #1251 (invoice-level schedule with monthly balances Jan–Apr)

**Build script**: `benchmarks/claude-code/aurisic-amortization/build_amortization.py`
