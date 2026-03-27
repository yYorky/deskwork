# Benchmark Comparison Notes

> Side-by-side qualitative analysis per task. Scored using the GDPval rubric for each task.
> Rubrics sourced from `benchmarks/tasks/*/rubric.md` — **NOT provided during execution** (data integrity preserved).

---

## Task 1: Fall Music Tour P&L

> Status: Complete. All three outputs scored.

### Task summary

Produce a profit and loss report for a client's 2024 Fall Music Tour, covering October 2024 revenue and costs. As-of date: December 31, 2024. Output is a formatted `.xlsx` workbook with a three-column layout (Tour Manager | Production Company | Total Combined). Revenue section shows 7 European tour stops line-by-line with foreign withholding tax applied per country. Expense section rolls up into 4 categories: Band and Crew, Other Tour Costs, Hotel & Restaurant, Other Travel Costs. Closes with Net Income summary. **Total possible: 89 points.**

---

### Rubric Scorecard

| # | Pts | Criterion | Claude Code | ChatGPT 5.4 + Deskwork | ChatGPT 5.4 One-Shot |
|---|-----|-----------|:-----------:|:----------------------:|:--------------------:|
| 1 | +2 | Final deliverable is .xlsx format | ✅ | ✅ | ✅ |
| 2 | +2 | Separate TM, PC, and Total Combined columns | ✅ | ✅ | ✅ |
| 3 | +2 | Revenue table lists City and Country per tour stop | ✅ | ✅ | ✅ |
| 4 | +2 | All revenue in USD; non-USD converted before summarization | ✅ | ✅ | ✅ |
| 5 | +1 | Currency columns use USD formatting | ✅ | ✅ | ✅ |
| 6 | +1 | No duplicate tour-stop rows | ✅ | ✅ | ✅ |
| 7 | +2 | Show 1 — London, UK: Combined Gross = $230,754 | ✅ | ✅ | ✅ |
| 8 | +2 | Show 2 — Paris, France: Combined Gross = $175,880 | ✅ | ✅ | ✅ |
| 9 | +2 | Show 3 — Paris, France: Combined Gross = $168,432 | ✅ | ✅ | ✅ |
| 10 | +2 | Show 4 — Barcelona, Spain: Combined Gross = $125,932 | ✅ | ✅ | ✅ |
| 11 | +2 | Show 5 — Madrid, Spain: Combined Gross = $110,823 | ✅ | ✅ | ✅ |
| 12 | +2 | Show 6 — Munich, Germany: Combined Gross = $99,117 | ✅ | ✅ | ✅ |
| 13 | +2 | Show 7 — Berlin, Germany: Combined Gross = $132,812 | ✅ | ✅ | ✅ |
| 14 | +2 | No revenue attributed to production company | ✅ | ✅ | ✅ |
| 15 | +2 | WHT rates: UK 20%, France 15%, Spain 24%, Germany 15.825% | ✅ | ✅ | ✅ |
| 16 | +2 | WHT Amount = rate × Combined Gross per row | ✅ | ✅ | ✅ |
| 17 | +2 | Net Revenue = Combined Gross − WHT per row | ✅ | ✅ | ✅ |
| 18 | +2 | Total Gross Revenue = $1,043,750 | ✅ | ✅ | ✅ |
| 19 | +2 | Total WHT = $191,322 | ✅ | ✅ | ✅ |
| 20 | +2 | Total Net Revenue = $852,428 | ✅ | ✅ | ✅ |
| 21 | +1 | UK WHT total = $46,151 | ✅ | ❌ | ❌ |
| 22 | +1 | France WHT total = $51,647 | ✅ | ❌ | ❌ |
| 23 | +1 | Spain WHT total = $56,821 | ✅ | ❌ | ❌ |
| 24 | +1 | Germany WHT total = $36,703 | ✅ | ❌ | ❌ |
| 25 | +2 | Expense category: Band and Crew (Fees & Per Diem) | ✅ | ✅ | ✅ |
| 26 | +2 | Expense category: Other Tour Costs | ✅ | ✅ | ✅ |
| 27 | +2 | Expense category: Hotel & Restaurant | ✅ | ✅ | ✅ |
| 28 | +2 | Expense category: Other Travel Costs | ✅ | ✅ | ✅ |
| 29 | +1 | Band and Crew Combined = $106,160 | ✅ | ✅ | ✅ |
| 30 | +1 | Band and Crew TM = $15,160 | ✅ | ✅ | ✅ |
| 31 | +1 | Band and Crew PC = $91,000 | ✅ | ✅ | ✅ |
| 32 | +1 | Other Tour Costs Combined = $136,837 | ❌ | ❌ | ❌ |
| 33 | +1 | Other Tour Costs TM = $136,837 | ❌ | ❌ | ❌ |
| 34 | +1 | Other Tour Costs PC = $0.00 | ❌ | ❌ | ❌ |
| 35 | +1 | Hotel & Restaurant Combined = $126,298 | ✅ | ✅ | ✅ |
| 36 | +1 | Hotel & Restaurant TM = $47,560 | ✅ | ✅ | ✅ |
| 37 | +1 | Hotel & Restaurant PC = $78,738 | ✅ | ✅ | ✅ |
| 38 | +1 | Other Travel Combined = $362,711 | ❌ | ❌ | ❌ |
| 39 | +1 | Other Travel TM = $350,056 | ❌ | ❌ | ❌ |
| 40 | +1 | Other Travel PC = $12,655 | ❌ | ❌ | ❌ |
| 41 | +1 | Other Tour Costs: Agency Commission $114,813 + Insurance $22,024, TM | ✅ | ✅ | ✅ |
| 42 | +1 | Hotel PC by city: London $14,232, Paris $22,296, Barcelona $8,168, Madrid $8,776, Munich $12,040, Berlin $13,226 | ✅ | ✅ | ✅ |
| 43 | +1 | Hotel TM by city: London $8,388, Paris $15,653, Barcelona $5,445, Madrid $5,113, Munich $6,369, Berlin $6,592 | ✅ | ✅ | ✅ |
| 44 | +1 | Other Travel TM: Private Jet $341,000, Transfer Cars $4,237, Other $4,819 | ❌ | ❌ | ❌ |
| 45 | +1 | Other Travel PC: Petty Cash $8,000, Transfer Cards $2,976, Other $1,679 | ❌ | ❌ | ❌ |
| 46 | +1 | Band and Crew: 10 members $91,000, PC | ✅ | ✅ | ✅ |
| 47 | +1 | Band and Crew: Sound Technician $8,256, TM | ✅ | ✅ | ✅ |
| 48 | +1 | Band and Crew: Tour Coordinator $6,904, TM | ✅ | ✅ | ✅ |
| 49 | +2 | Total Combined Expenses = $732,006 | ✅ | ✅ | ✅ |
| 50 | +1 | TM Total Expenses = $549,613 | ✅ | ✅ | ✅ |
| 51 | +1 | PC Total Expenses = $182,393 | ✅ | ✅ | ✅ |
| 52 | +2 | Net Income summary present (TM, PC, Total Combined) | ✅ | ✅ | ✅ |
| 53 | +2 | Total Combined Net Income = $120,423 | ✅ | ✅ | ✅ |
| 54 | +1 | TM Net Income = $302,816 | ✅ | ✅ | ✅ |
| 55 | +1 | PC Net Income = −$182,393 (deficit) | ✅ | ✅ | ✅ |
| 56 | +2 | NI = Total Net Revenue − Total Expenses | ✅ | ✅ | ✅ |
| 57 | +1 | TM NI = TM Net Revenue − TM Expenses | ✅ | ✅ | ✅ |
| 58 | +1 | PC NI = PC Net Revenue − PC Expenses | ✅ | ✅ | ✅ |
| 59 | +5 | Overall formatting and style | ⚠️ 3/5 | ⚠️ 4/5 | ⚠️ 3/5 |

### Final scores

| | Claude Code + SKILL.md | ChatGPT 5.4 Think Deeper + Deskwork | ChatGPT 5.4 Think Deeper One-Shot |
|--|:---:|:---:|:---:|
| **Score** | **79 / 89** | **76 / 89** | **75 / 89** |
| **Pct** | **89%** | **85%** | **84%** |

---

### Claude Code + SKILL.md

**Output**: `benchmarks/03_sonnet-4.6-claude-code/music-tour-pl/output/Fall_Music_Tour_PL_2024.xlsx` (7,438 bytes)
**Sheet structure**: Single sheet "P&L Statement"

**What succeeded**:
- All revenue and expense figures correct; gross, WHT, and net totals reconcile exactly
- WHT applied at correct per-country rates with a dedicated **Withholding Tax Detail** section showing country-level subtotals (UK $46,150.80, France $51,646.80, Spain $56,821.20, Germany $36,702.76) — earning criteria 21–24
- All four expense categories present; Hotel & Restaurant line items by city match exactly
- Band and Crew line items correct
- Net Income formula correct for TM, PC, and Combined
- `$#,##0.00` currency formatting on all numeric cells

**Issues**:
- **Expense miscategorisation — 6 criteria lost (rows 32–34, 38–40, 44–45)**: TM "Other" ($4,819) placed in _Other Tour Costs_ instead of _Other Travel Costs_. PC "Petty Cash" ($8,000) and "Fees" ($1,679) placed in _Other Tour Costs_ instead of _Other Travel Costs_. The rubric expects these in the travel bucket, shifting both subtotals off target.
- **Formatting (3/5)**: `$#,##0.00` applied correctly but no section shading, no bold category rows, and title contains a Unicode encoding artefact ("▒" character).

**Root cause of miscategorisation**: The reference file labels these items ambiguously — "Other" and "Petty Cash / Fees" without a clear travel vs. operating designation. SKILL.md specified output categories but did not include a line-item-to-category mapping, leaving the decision to inference at execution time.

---

### ChatGPT 5.4 Think Deeper + Deskwork

**Output**: `benchmarks/02_gpt-5.4_thinkdeeper-deskwork/music-tour-pl/output/2024_Fall_Music_Tour_PnL_Report_AsOf_2024-12-31.xlsx`
**Sheet structure**: 3 sheets — "P&L Summary", "Revenue Detail", "Expense Mapping"

**What succeeded**:
- Multi-sheet structure is well-organised: summary on one tab, per-stop revenue detail on another, full expense line-item mapping on a third
- All revenue and expense totals reconcile correctly; gross, WHT, and net match exactly
- WHT rates applied correctly by country
- Expense line items correctly mapped to categories (with the same categorisation error as Claude Code — see Issues)
- Hotel & Restaurant by city exact ✅; Band and Crew by member exact ✅
- Net Income section with TM/PC/Combined all correct
- Professional formatting: clean headers, `$#,##0.00` on all cells, executive-ready layout
- Notes section at the bottom explicitly documents WHT rates and category mapping assumptions

**Issues**:
- **Same expense miscategorisation — 6 criteria lost (rows 32–34, 38–40, 44–45)**: The `system_prompt.md` generated in Chat 1 explicitly mapped "Other", "Petty Cash", and "Fees" to _Other Tour Costs_. Chat 2 faithfully executed this — the wrong mapping was codified into the workflow artefact itself.
- **No country-level WHT detail — 4 criteria lost (rows 21–24)**: The P&L Summary shows only a single total WHT row; the Revenue Detail has per-stop WHT but no country subtotals. Claude Code proactively added a WHT Detail section; ChatGPT's system prompt did not specify this, so it was not produced.
- **Formatting (4/5)**: Clean, executive-ready, clear title. Multi-sheet structure is genuinely useful (scorer's note: the rubric appears written with a single-sheet layout in mind, but the extra sheets are an improvement in practice).

---

### ChatGPT 5.4 Think Deeper One-Shot

**Output**: `benchmarks/01_gpt5.4_thinkdeeper-oneshot/music-tour-pl/output/2024_Fall_Music_Tour_PnL_AsOf_2024-12-31.xlsx`
**Sheet structure**: 4 sheets — "P&L Summary", "Revenue Detail", "Expense Detail", "Assumptions"

**What succeeded**:
- All 7 revenue gross figures exact; WHT rates correct by country; Net Revenue per row correct
- All revenue correctly attributed to Tour Manager only (no PC revenue)
- All four expense categories present with correct band and crew, hotel line items by city
- Total expenses, total net revenue, and net income totals correct for TM, PC, and Combined
- Hotel & Restaurant PC and TM city-level figures exact
- Net Income arithmetic correct across all three columns
- Assumptions sheet documents WHT rates separately; Revenue Detail tab has per-stop WHT computation
- 4-sheet structure comparable in quality to Deskwork output

**Issues**:
- **Same expense miscategorisation — same 6 criteria lost (rows 32–34, 38–40, 44–45)**: Exactly the same error as both other methods. TM "Other" ($4,819) placed in _Other Tour Costs_; PC "Petty Cash" ($8,000) and "Fees" ($1,679) placed in _Other Tour Costs_. Root cause is the same source data ambiguity.
- **No country-level WHT subtotals — 4 criteria lost (rows 21–24)**: P&L Summary shows a single WHT total row; Revenue Detail has per-stop WHT amounts but no country subtotals. Consistent with the Deskwork output; both missed the proactive addition that Claude Code made.
- **Formatting (3/5)**: Well-structured multi-sheet output but slightly less polished than the Deskwork version (4/5). No explicit formatting instructions in a one-shot prompt.

**Root cause**: Without a system prompt specifying the exact category mapping, the model inferred "Other" and "Petty Cash/Fees" as operating costs rather than travel costs — the same inference error made by the Deskwork Chat 1 session when building the system prompt. The source data is genuinely ambiguous.

---

### Key comparison

**Outcome**: Claude Code + SKILL.md scored highest (79), with Deskwork second (76) and one-shot third (75). The gap between Deskwork and one-shot is just 1 point.

**Where all three methods failed identically**:
- Expense miscategorisation (criteria 32–34, 38–40, 44–45): All three made the same error on the same 8 criteria, losing the same 8 points. This is source data ambiguity, not a workflow gap.

**Where one-shot matched Deskwork but not Claude Code**:
- Country-level WHT detail (criteria 21–24): Neither one-shot nor Deskwork produced country subtotals. Claude Code proactively added a WHT Detail section earning 4 additional points.

**Where Deskwork had an edge over one-shot**:
- Formatting (4/5 vs. 3/5): One point difference attributable to the Deskwork system prompt guiding output style.

**What this tells us**:
The one-shot and Deskwork outputs are nearly identical in quality on this task. The 1-point gap (75 vs. 76) is entirely attributable to formatting guidance in the system prompt. The core computation, structure, and categorisation errors are shared across all three methods. This suggests that for a relatively well-defined task with clear reference data, the model's baseline capability is sufficient — the Deskwork workflow adds marginal structure but does not fundamentally change the outcome.

---

## Task 2: Aurisic Prepaid Amortization

> Status: Complete. All three outputs scored.

### Task summary

Produce a prepaid amortization workbook for Aurisic covering January–April 2025. Source data: five PDFs — two GL trial balance reports (accounts 1250 and 1251) and three invoice PDFs. Output is a three-tab `.xlsx`: a Prepaid Summary tab with YTD figures and April 30 balances, plus two detail schedules (one per account) showing invoice-level straight-line amortization with monthly remaining balances. All balances must reconcile to the authoritative GL figures. **Total possible: 95 points.**

---

### Rubric Scorecard

| # | Pts | Criterion | Claude Code | ChatGPT 5.4 + Deskwork | ChatGPT 5.4 One-Shot |
|---|-----|-----------|:-----------:|:----------------------:|:--------------------:|
| 1 | +2 | Delivers a single .xlsx workbook | ✅ | ✅ | ✅ |
| 2 | +2 | Sheet titled "Prepaid Summary" | ✅ | ✅ | ✅ |
| 3 | +2 | Sheet name includes account number 1250 | ✅ | ❌ | ✅ |
| 4 | +2 | Sheet name includes account number 1251 | ✅ | ❌ | ✅ |
| 5 | +1 | Prepaid Summary header includes company name Aurisic | ✅ | ✅ | ✅ |
| 6 | +1 | Prepaid Summary states period up to April 30, 2025 | ✅ | ✅ | ✅ |
| 7 | +2 | Summary totals linked by Excel formulas to detail tabs | ❌ | ✅ | ✅ |
| 8 | +2 | 1250 April GL balance = $559,377.61 | ✅ | ✅ | ✅ |
| 9 | +2 | 1251 April GL balance = $369,976.70 | ✅ | ✅ | ✅ |
| 10 | +2 | Total prepaid balance = $929,354.31 | ✅ | ⚠️ 1/2 | ✅ |
| 11 | +2 | YTD amortization shown for each account | ✅ | ✅ | ✅ |
| 12 | +1 | Description-and-amount layout in Summary | ✅ | ✅ | ✅ |
| 13 | +2 | 1250 includes every invoice from all 4 PDF months | ✅ | ✅ | ✅ |
| 14 | +2 | 1250 original amounts match source PDFs | ✅ | ✅ | ✅ |
| 15 | +2 | 1250 amortization period = contract dates or 6-month default | ✅ | ✅ | ✅ |
| 16 | +2 | 1250 monthly expense straight-line over documented term | ✅ | ✅ | ✅ |
| 17 | +1 | 1250 schedule organized by vendor | ✅ | ✅ | ✅ |
| 18 | +2 | 1250 includes: Original Amount, Amort Period, Monthly Expense, Remaining Balance | ✅ | ✅ | ✅ |
| 19 | +1 | 1250 displays Jan, Feb, Mar, Apr 2025 monthly activity | ✅ | ✅ | ✅ |
| 20 | +1 | 1250 amortization only in months within start–end period | ✅ | ✅ | ✅ |
| 21 | +2 | 1250 Beg Balance + Adds − Amort = Ending Balance per line | ✅ | ✅ | ✅ |
| 22 | +2 | 1250 totals: total amort = sum of line amort; total ending = sum of line balances | ✅ | ✅ | ✅ |
| 23 | +2 | 1250 January ending balance = $518,934.86 | ✅ | ✅ | ✅ |
| 24 | +2 | 1250 February ending balance = $426,673.13 | ✅ | ✅ | ✅ |
| 25 | +2 | 1250 March ending balance = $473,655.55 | ✅ | ✅ | ✅ |
| 26 | +2 | 1250 April ending balance = $559,377.61 | ✅ | ✅ | ✅ |
| 27 | +1 | 1250 summary section shows monthly additions | ✅ | ✅ | ✅ |
| 28 | +1 | 1250 summary section shows monthly amortization expense | ✅ | ✅ | ✅ |
| 29 | +1 | 1250 summary section shows ending balances | ✅ | ✅ | ✅ |
| 30 | +2 | 1250 GL Balance and Variance check; all variances = $0.00 | ✅ | ✅ | ✅ |
| 31 | +1 | No negative amortization on 1250 | ✅ | ✅ | ✅ |
| 32 | +1 | 1250 balance does not increase unless documented addition | ✅ | ✅ | ✅ |
| 33 | +2 | 1251 includes every insurance invoice (no omissions) | ✅ | ✅ | ✅ |
| 34 | +2 | 1251 original amounts match source PDF | ✅ | ✅ | ✅ |
| 35 | +2 | 1251 amortization period = policy dates from PDF | ✅ | ✅ | ✅ |
| 36 | +2 | 1251 Good Insurance: 1/1/2025–12/31/2025 straight-line | ✅ | ✅ | ✅ |
| 37 | +2 | 1251 BCBS: monthly billing, amortization starts Feb 2025 | ✅ | ✅ | ✅ |
| 38 | +1 | 1251 displays Jan, Feb, Mar, Apr 2025 monthly activity | ✅ | ✅ | ✅ |
| 39 | +2 | 1251 Beg Balance + Adds − Amort = Ending Balance per line | ✅ | ✅ | ✅ |
| 40 | +2 | 1251 totals reconcile per month | ✅ | ✅ | ✅ |
| 41 | +2 | 1251 January ending balance = $506,657.98 | ✅ | ✅ | ✅ |
| 42 | +2 | 1251 February ending balance = $461,097.55 | ✅ | ✅ | ✅ |
| 43 | +2 | 1251 March ending balance = $415,537.13 | ✅ | ⚠️ 1/2 | ✅ |
| 44 | +2 | 1251 April ending balance = $369,976.70 | ✅ | ⚠️ 1/2 | ✅ |
| 45 | +1 | 1251 schedule organized by vendor | ✅ | ✅ | ✅ |
| 46 | +2 | 1251 includes: Original Amount, Amort Period, Monthly Expense, Remaining Balance | ✅ | ✅ | ✅ |
| 47 | +1 | 1251 summary section shows additions, amortization, and ending balances | ✅ | ✅ | ✅ |
| 48 | +2 | 1251 GL Balance and Variance check; all variances = $0.00 | ✅ | ⚠️ 1/2 | ✅ |
| 49 | +1 | No negative amortization on 1251 | ✅ | ✅ | ✅ |
| 50 | +1 | 1251 balance does not increase unless documented addition | ✅ | ✅ | ✅ |
| 51 | +1 | Expense classification uses COA account numbers | ✅ | ✅ | ✅ |
| 52 | +2 | Schedules show Beg Balance, Additions, Amortization, Ending Balance each month | ✅ | ✅ | ✅ |
| 53 | +1 | Currency formatted as dollars; dates in clear format | ✅ | ✅ | ✅ |
| 54 | +1 | Comments column classifies nature of prepaid | ✅ | ✅ | ✅ |
| 55 | +1 | Each detail tab has 17 columns or equivalent | ✅ | ✅ | ✅ |
| 56 | +5 | Overall formatting and style | ⚠️ 3/5 | ⚠️ 4/5 | ⚠️ 3/5 |

### Final scores

| | Claude Code + SKILL.md | ChatGPT 5.4 Think Deeper + Deskwork | ChatGPT 5.4 Think Deeper One-Shot |
|--|:---:|:---:|:---:|
| **Score** | **91 / 95** | **86 / 95** | **93 / 95** |
| **Pct** | **96%** | **91%** | **98%** |

---

### Claude Code + SKILL.md

**Output**: `benchmarks/03_sonnet-4.6-claude-code/aurisic-amortization/output/Aurisic_Prepaid_Amortization_Apr2025.xlsx` (3 tabs)
**Sheet structure**: Prepaid Summary · Prepaid Expenses #1250 · Prepaid Insurance #1251

**What succeeded**:
- All 8 GL reconciliation checks pass: 1250 and 1251 balances for all four months match targets exactly ($0.00 variance on every month)
- Rounding accumulation handled via a "GL Rounding Adjustment" row that absorbs the 1–5 cent per-month discrepancy that arises from individually rounding 40+ line balances
- All invoice data correctly extracted from 5 PDFs; 6-month default applied to all 1250 invoices (no contract dates on any PDF); BCBS monthly billing treatment correct (each Jan invoice covers Feb, etc.)
- Good Insurance 12-month straight-line applied correctly across 21 invoices
- Sheet names include account numbers 1250/1251 (criteria 3–4) — earned 4 points that ChatGPT Deskwork lost
- Vendor grouping, monthly activity columns (Jan–Apr), summary section with GL reconciliation all present

**Issues**:
- **Formula linking (−2)**: Prepaid Summary totals are Python-computed floats written directly to cells — not Excel formulas referencing the detail tabs. The rubric requires live formula links.
- **Formatting (3/5)**: Professional dark-blue styling, color-coded GL variance rows. However: (a) no per-line monthly expense column in detail tabs (only remaining balance shown), limiting column count to 14 vs. 17; (b) Summary tab uses hardcoded values rather than cross-sheet formulas.

---

### ChatGPT 5.4 Think Deeper + Deskwork

**Output**: `benchmarks/02_gpt-5.4_thinkdeeper-deskwork/aurisic-amortization/output/Aurisic_Prepaid_Amortization_Schedule_through_Apr_2025.xlsx` (3 tabs)
**Sheet structure**: Prepaid Summary · Prepaid Expenses · Prepaid Insurance

**What succeeded**:
- All 1250 GL balances reconcile exactly: $518,934.86 / $426,673.13 / $473,655.55 / $559,377.61 ✓
- 1251 January and February balances reconcile exactly
- Both detail tabs have 19 columns including per-line monthly amortization expense AND remaining balance
- Vendor-alphabetical sort, complete summary sections, correct BCBS and Good Insurance treatment
- Strong formatting (4/5): clean executive layout, 19-column structure, assumption notes in each tab
- **Summary tab uses live Excel cross-tab formulas** — confirmed by direct formula inspection [re-verified 2026-03-27]: Summary cells reference `'Prepaid Expenses'!C56`, `D56`, `E56` (YTD booked, YTD amortization, April ending balance for 1250) and `'Prepaid Insurance'!C41`, `D41`, `E41` (same for 1251). Both YTD amortization AND April ending balances are formula-linked. Full 2/2 credit on criterion 7.

**Issues**:
- **Sheet names missing account numbers (−4)**: Sheet names are "Prepaid Expenses" and "Prepaid Insurance" without "1250"/"1251" — fails criteria 3 and 4. The system_prompt.md specified sheet names but did not include the account numbers in the naming convention.
- **1251 rounding ($0.01 on Mar/Apr) (−4)**: Monthly expense rounding for Good Insurance accumulates a $0.01 discrepancy in March and April ending balances ($415,537.12 vs. $415,537.13; $369,976.69 vs. $369,976.70). This also causes a $0.01 non-zero GL variance in both months (−1 on criterion 48) and a $0.01 error in the April total balance.
- **Total balance shows $929,354.30 (−1)**: The schedule-computed total shows $929,354.30 while the GL column correctly shows $929,354.31 — rubric awards only 1/2 credit.

**Root cause of rounding issue**: ChatGPT applied the same individual-line rounding approach without a GL reconciliation adjustment row. Claude Code explicitly addressed this with a "GL Rounding Adjustment" row — proactively solving a problem that the Deskwork system_prompt did not specify.

---

### ChatGPT 5.4 Think Deeper One-Shot

**Output**: `benchmarks/01_gpt5.4_thinkdeeper-oneshot/aurisic-amortization/output/Aurisic_Prepaid_Amortization_Schedule_Apr2025.xlsx` (3 tabs)
**Sheet structure**: Prepaid Summary · Prepaid Expenses (1250) · Prepaid Insurance (1251)

**What succeeded**:
- **All 8 GL reconciliation checks pass with $0.00 variance** — both 1250 and 1251 across all four months reconcile exactly. This matches Claude Code and exceeds the Deskwork output.
- **Summary tab uses live Excel formulas referencing detail tabs** — confirmed by formula inspection: cells reference `'Prepaid Expenses (1250)'!B6` through `B10` and `'Prepaid Insurance (1251)'!B6` through `B10`. This earns full 2/2 on criterion 7, tying Deskwork (also 2/2) and beating Claude Code (0/2).
- **Sheet names include account numbers** (`Prepaid Expenses (1250)`, `Prepaid Insurance (1251)`) — earning criteria 3–4, which the Deskwork method lost entirely.
- All 1251 balances exact: Jan $506,657.98, Feb $461,097.55, Mar $415,537.13, Apr $369,976.70. No rounding accumulation.
- Total prepaid balance = $929,354.31 exactly (Deskwork showed $929,354.30).
- 19-column detail tabs (A–S) including per-line monthly amortization expense and remaining balance.
- All 1250 invoices from all 4 months included; 6-month default applied; BCBS treatment correct.
- COA account numbers used for expense classification.
- Monthly activity reconciliation section with GL balance check present in both detail tabs.

**Issues**:
- **Formatting (3/5)**: Well-structured three-tab workbook but without explicit formatting guidance from a system prompt, styling is slightly less polished than the Deskwork output (4/5). No executive-style color coding or explicit assumption notes tabs.

**Root cause of success**: Without a system prompt, the model reasoned from the task description and reference files directly. The BCBS modeling (prepaid in advance: Jan invoice covers Feb amortization) was handled correctly. The model also naturally included account numbers in sheet names and wrote cross-tab Excel formulas in the Summary — decisions the Deskwork workflow failed to specify explicitly.

---

### Key comparison

**Outcome**: ChatGPT 5.4 Think Deeper One-Shot scored highest (93/95, 98%), followed by Claude Code (91/95, 96%) and Deskwork (86/95, 91%). **This is the only task where the one-shot outperformed both other methods.**

**Where one-shot had an edge over Deskwork**:
- Formula linking: both One-Shot and Deskwork earn full 2/2 (Claude Code: 0/2) — re-verified by direct formula inspection 2026-03-27
- All 1251 GL variances = $0.00 (Claude Code: same; Deskwork: $0.01 on Mar/Apr)
- Total balance $929,354.31 exact (Deskwork: $929,354.30)
- Sheet names include account numbers (Claude Code: same; Deskwork: missed entirely)

**Where Claude Code had an edge over one-shot**:
- Formatting: Both scored 3/5, so no gap here — both one point below Deskwork's 4/5

**What this tells us**:
The Deskwork workflow made this task harder, not easier. The system_prompt.md omitted two critical specifications: (1) sheet names should include account numbers, and (2) a rounding-adjustment mechanism was needed for 1251. The one-shot, without any scaffolding, produced a more accurate workbook than the Deskwork-guided output. This suggests that for tasks with well-structured reference data and clear reconciliation targets, capable models can reason their way to correct solutions without workflow scaffolding — and poorly specified workflows can actively introduce errors.

> **Re-verification note (2026-03-27)**: Criterion 7 (Summary formula linking) for Deskwork was upgraded from ⚠️ 1/2 to ✅ 2/2 after direct XML inspection of the worksheet confirmed cross-tab formula references covering both YTD amortization and April ending balances for both accounts. Deskwork Task 2 score revised from 85/95 to 86/95.

---

## Task 3: Anti-Financial Crime Audit Sampling

> Status: Complete. All three outputs scored.

### Task summary

Produce an audit sampling workpaper for an Anti-Financial Crime review. Population: 1,516 KRI rows across 4 divisions and 13 sub-divisions. Apply attribute sampling at 90% confidence, 10% tolerable deviation, with finite population correction. Output is a two-tab `.xlsx` ("Sample" and "Sample Size Calculation") showing the full population with QoQ variance scores, sample flags, and mandatory coverage of specific entity/country combinations. **Total possible: 63 points.**

---

### Rubric Scorecard

| # | Pts | Criterion | Claude Code | ChatGPT 5.4 + Deskwork | ChatGPT 5.4 One-Shot |
|---|-----|-----------|:-----------:|:----------------------:|:--------------------:|
| 1 | +2 | File basename is 'Sample' | ✅ | ✅ | ✅ |
| 2 | +2 | Worksheet named exactly 'Sample Size Calculation' | ✅ | ✅ | ✅ |
| 3 | +2 | SSC states confidence 90% and tolerable error 10% | ✅ | ✅ | ✅ |
| 4 | +2 | Population size N = 1516 | ✅ | ✅ | ✅ |
| 5 | +2 | z=1.645, p=0.5, e=0.10, FPC applied; R reported as integer (ceil) | ✅ | ✅ | ✅ |
| 6 | +2 | First worksheet col A–H in Population order with identical headers | ✅ | ✅ | ✅ |
| 7 | +2 | Values in A–H exactly match Population reference | ✅ | ✅ | ✅ |
| 8 | +2 | G=Q3 2024, H=Q2 2024 consistent with Population column positions | ✅ | ✅ | ✅ |
| 9 | +2 | Col I computes QoQ variance = (Q3−Q2)/Q2 for rows where Q2≠0 | ✅ | ❌ | ❌ |
| 10 | +1 | Q2=0, Q3=0: col I = 0 (no change) | ✅ | ✅ | ❌ |
| 11 | +1 | Q2=0, Q3≠0: col I avoids #DIV/0! errors | ✅ | ✅ | ✅ |
| 12 | +1 | No Excel errors in col I | ✅ | ✅ | ✅ |
| 13 | +2 | Col J exists; sampled rows flagged by numeric value 1 | ✅ | ❌ | ❌ |
| 14 | +1 | Non-sampled rows in col J blank or 0 | ✅ | ❌ | ❌ |
| 15 | +2 | Sample count S shown; S ≥ R | ✅ | ❌ | ❌ |
| 16 | +2 | At least one row with \|variance\| ≥ 20% is sampled | ✅ | ✅ | ✅ |
| 17 | +1 | If \|variance\| ≥ 100% rows exist, at least one is sampled | ✅ | ✅ | ✅ |
| 18 | +2 | Sample: Corporate Banking + Corporate Loans + Italy | ✅ | ❌ | ❌ |
| 19 | +2 | Sample: Corporate Banking + Correspondent Banking + Greece | ✅ | ✅ | ✅ |
| 20 | +2 | Sample: Markets + Trading + Luxembourg | ✅ | ✅ | ✅ |
| 21 | +2 | Sample: Corporate Banking + Marine Finance + Brazil | ✅ | ✅ | ✅ |
| 22 | +2 | Sample: Retail Bank + EMEA + UAE | ✅ | ✅ | ✅ |
| 23 | +2 | Sample includes Total Clients metric | ✅ | ✅ | ✅ |
| 24 | +2 | Sample includes HR Clients metric | ✅ | ✅ | ✅ |
| 25 | +1 | If Q2=0 and Q3=0 rows exist, at least one sampled | ✅ | ✅ | ✅ |
| 26 | +1 | If Marine Finance rows exist, at least one sampled | ✅ | ✅ | ✅ |
| 27 | +1 | If Correspondent Banking rows exist, at least one sampled | ✅ | ✅ | ✅ |
| 28 | +1 | If Cayman Islands rows exist, at least one sampled | ✅ | ✅ | ✅ |
| 29 | +1 | If Pakistan rows exist, at least one sampled | ✅ | ✅ | ✅ |
| 30 | +1 | If UAE rows exist, at least one sampled | ✅ | ✅ | ✅ |
| 31 | +2 | All distinct Divisions represented in sample | ✅ | ✅ | ✅ |
| 32 | +2 | All distinct Sub-Divisions represented in sample | ✅ | ✅ | ✅ |
| 33 | +1 | SSC shows arithmetic steps (z, p, e, FPC) reproducibly | ✅ | ✅ | ✅ |
| 34 | +1 | First worksheet includes full population (1516 rows) | ✅ | ❌ | ❌ |
| 35 | +1 | Col J header clearly indicates QoQ variance | ❌ | ✅ | ✅ |
| 36 | +1 | Metrics with \|variance\| ≥ 100% easily identifiable | ❌ | ❌ | ❌ |
| 37 | +1 | First worksheet named 'Sample' | ✅ | ❌ | ❌ |
| 38 | +5 | Overall formatting and style | ⚠️ 4/5 | ⚠️ 3/5 | ⚠️ 3/5 |

### Final scores

| | Claude Code + SKILL.md | ChatGPT 5.4 Think Deeper + Deskwork | ChatGPT 5.4 Think Deeper One-Shot |
|--|:---:|:---:|:---:|
| **Score** | **60 / 63** | **49 / 63** | **48 / 63** |
| **Pct** | **95%** | **78%** | **76%** |

---

### Claude Code + SKILL.md

**Output**: `benchmarks/03_sonnet-4.6-claude-code/afc-audit-sampling/output/Sample.xlsx` (2 tabs)
**Sheet structure**: Sample (1516 rows + header) · Sample Size Calculation

**What succeeded**:
- First sheet named "Sample" exactly; full 1516-row population preserved with original A–H columns ✓
- Col I = "QoQ Variance (Q3 vs Q2)" computing (Q3−Q2)/Q2 as decimal; zero-zero rows return 0; Q2=0,Q3≠0 returns "N/M" (no #DIV/0! errors) ✓
- Col J = "Selected" flag (1 = sampled, blank = not sampled); S=67 ≥ R=66 ✓
- All 5 mandatory entity/country combinations satisfied: Italy (Corporate Bank+Corporate Loans), Greece (Correspondent Banking), Luxembourg (Trading), Brazil (Marine Finance), UAE (Retail Bank+EMEA) ✓
- All 4 Divisions and all 13 Sub-Divisions represented in sample ✓
- All specific country criteria: Pakistan, Cayman Islands, UAE, Total Clients, HR Clients ✓
- Sample Size Calculation tab shows all inputs (z=1.645, p=0.5, e=0.10, N=1516), formula steps, and FPC application ✓

**Issues**:
- **Col J header (−1)**: Header is "Selected" — the rubric requires the column J header to indicate QoQ variance (e.g., "% Var Q3 vs Q2"). In our design, Col I is the variance and Col J is the sample flag, so the header naming is semantically correct but fails this specific rubric criterion.
- **|≥100%| not easily identifiable (−1)**: No conditional formatting or separate flag column marks rows with extreme variance. The script selects them (all are in the sample) but does not visually highlight them.
- **Formatting (4/5)**: Clean structure, but no conditional formatting.

---

### ChatGPT 5.4 Think Deeper + Deskwork

**Output**: `benchmarks/02_gpt-5.4_thinkdeeper-deskwork/afc-audit-sampling/output/Sample.xlsx` (2 tabs)
**Sheet structure**: Selected sample (65 rows) · Sample Size Calculation

**What succeeded**:
- Sample Size Calculation tab complete: N=1516, z=1.645, p=0.5, e=0.10, FPC applied, R=65 ✓
- Greece + Correspondent Banking, Luxembourg + Trading, Brazil + Marine Finance, UAE + Retail Bank correctly sampled ✓
- Total Clients and HR Clients both sampled ✓
- All Divisions and Sub-Divisions covered ✓
- Cayman Islands, Pakistan, UAE, Marine Finance, Correspondent Banking all sampled ✓
- Col J header = "QoQ Variance %" — correctly labelled to indicate QoQ variance (earned criterion 35)
- Formatting (3/5): Selection rationale column (L) explains each row's inclusion reason; well-organized SSC tab with arithmetic steps

**Issues**:
- **Column assignment mismatch (−7)**: GPT-5 placed absolute variance (Q3−Q2) in col I and QoQ percentage variance in col J, with the sample flag in col K. The rubric expects: col I = QoQ%, col J = sample flag. This single structural error costs: criterion 9 (−2, col I is wrong formula), criterion 13 (−2, col J is not the flag), criterion 14 (−1, col J is not blank for non-sampled), criterion 15 (−2, S shown in col K not the expected location).
- **First sheet not named 'Sample' (−1)**: Sheet named "Selected sample" instead of "Sample".
- **First sheet contains only sample rows (−1)**: 65 rows only — rubric expects the full 1516-row population with flags.
- **Italy + Corporate Loans not sampled (−2)**: Mandatory criterion 18. GPT-5 sampled Corporate Bank + Fund Services + Italy instead. The Deskwork system_prompt listed the 5 mandatory combinations but the exact Sub-Division match was missed (Fund Services vs. Corporate Loans).
- **|≥100%| not easily identifiable (−1)**: Same gap as Claude Code.

**Root cause of column mismatch**: The system_prompt.md specified "add a QoQ variance column and a sample selection flag column" but did not specify which column letter each should occupy. GPT-5 inserted two columns before the flag, shifting col J to variance and col K to flag — a defensible interpretation but misaligned with the rubric's col J = flag assumption.

---

### ChatGPT 5.4 Think Deeper One-Shot

**Output**: `benchmarks/01_gpt5.4_thinkdeeper-oneshot/afc-audit-sampling/output/Sample.xlsx` (2 tabs)
**Sheet structure**: Selected Sample (65 rows) · Sample Size Calculation

**What succeeded**:
- Sample Size Calculation tab complete: N=1516, z=1.645, p=0.5, e=0.10, FPC applied, R=65 ✓
- Col A–H headers match population order (No, Division, Sub-Division, Country, Legal Entity, KRIs, Q3 2024 KRI, H2 2024 KRI) ✓
- Col J = "QoQ Variance" text column (earning criterion 35 for clearly labelled header)
- Col K = "Sampled" flag = 1 for all selected rows ✓
- Greece + Correspondent Banking, Luxembourg + Trading, Brazil + Marine Finance, UAE + Retail Bank correctly sampled ✓
- Total Clients and HR Clients both sampled ✓
- All 4 Divisions and all 13 Sub-Divisions covered ✓
- Cayman Islands, Pakistan, UAE, Correspondent Banking all sampled ✓
- At least one Q2=0/Q3=0 row included ✓
- SSC shows full workings (z=1.645, n₀ formula, FPC formula, R=65) ✓
- Coverage review section in SSC documents which criteria were met and which were not in population ✓
- Col I = "Criteria Met" text column avoids #DIV/0! errors (criterion 11) ✓
- No Excel errors in col I (criterion 12) ✓

**Issues**:
- **Col I not QoQ variance (−2)**: Col I = "Criteria Met" explanatory text. The rubric expects QoQ% computation in col I. This is the same structural shift as the Deskwork output but with a different column (I = text rationale vs. I = absolute variance).
- **Criterion 10 lost (−1)**: For Q2=0/Q3=0 rows, col I shows "Zero values in both quarters" (text), not 0. The rubric expects col I = 0 (numeric) for these rows.
- **Col J not sample flag (−2)**: Col J = QoQ Variance % text (e.g., "0.00%", "N/M (Q2=0)", "-100.00%"). The rubric expects col J = numeric sample flag (1 or blank).
- **Col K not blank for non-sampled (−1)**: Since the first sheet contains only sample rows, there are no non-sampled rows to check. Criterion 14 is failed because col J is not the flag column.
- **Sample count S not shown (−2)**: The required count (R=65) is shown in SSC but the actual sample count S is not separately shown and verified as S ≥ R.
- **Italy + Corporate Loans not sampled (−2)**: Sampled Corporate Bank + Fund Services + Italy (rows 704–706) as a proxy. The model noted "CB Cash Italy exact label not present" but did not find Corporate Loans + Italy rows. Same failure as the Deskwork output.
- **First sheet not named 'Sample' (−1)**: Named "Selected Sample" instead of "Sample".
- **Full population not included (−1)**: Sheet contains only the 65 selected rows, not the full 1516-row population with flags. Same structural failure as Deskwork.
- **|≥100%| not easily identifiable (−1)**: No conditional formatting or highlight for extreme variance rows.
- **Formatting (3/5)**: Well-organized with a detailed "Criteria Met" explanatory column and a comprehensive coverage review table in SSC. However, the structural departure from the expected format limits the score.

**Root cause**: Without a system prompt specifying exact column assignments (col I = QoQ%, col J = flag, full population in tab 1), the model produced a sample-only sheet with its own column layout. The "Criteria Met" column (I) is a useful audit trail but occupies the slot the rubric reserved for variance. The same mandatory inclusion gap (Italy + Corporate Loans) appeared in both one-shot and Deskwork, suggesting the "Corporate Loans + Italy" combination is genuinely hard to locate without explicit guidance to search for it.

---

### Key comparison

**Outcome**: Claude Code + SKILL.md scored substantially higher (60 vs. 49 vs. 48). The one-shot and Deskwork are nearly identical (48 vs. 49).

**Where both ChatGPT methods failed vs. Claude Code**:
- Column assignments (criteria 9, 13, 14, 15): −7 to −8 points. Neither method produced col I = QoQ% and col J = numeric flag. Claude Code explicitly specified these columns in SKILL.md.
- First sheet as full population (criterion 34): −1 point. Both ChatGPT outputs show only selected rows.
- First sheet named "Sample" (criterion 37): −1 point. Both ChatGPT outputs use "Selected sample" / "Selected Sample".
- Italy + Corporate Loans (criterion 18): −2 points. Both ChatGPT outputs used Fund Services + Italy as proxy.

**Where one-shot differed from Deskwork**:
- Criterion 10 (zero-zero rows → col I = 0): Deskwork ✅ (absolute variance = 0 for zero rows), one-shot ❌ (col I is text). Net: −1 point vs. Deskwork.
- Criterion 35 (col J header indicates QoQ variance): Both ✅.

**What this tells us**:
For the highest-complexity task, structural specification matters most. Claude Code's SKILL.md explicitly defined column assignments (I = variance, J = flag) and required the full population — earning 12 points that both ChatGPT methods lost. Without that structural scaffolding, both GPT methods independently produced sample-only sheets with column layouts that departed from the rubric. The gap between one-shot and Deskwork is just 1 point (criterion 10), suggesting that even detailed system_prompt.md specifications don't close the structural gap when the rubric's column convention is non-obvious.
