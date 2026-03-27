# SKILL: Aurisic April Month-End Financial Package

## Task
Produce `Aurisic_Financials_4-25-1.xlsx` — the April 2025 month-end financial package for Aurisic. The March workbook (`Aurisic_Financials_3-25-1.xlsx`) is the template. Update every tab from **Tab 3a onward** with April data. Tabs 1, 2, 2a, and 3 are reserved for the CFO — do not include them.

## Reference files (in `reference-files/`)

| File | Purpose |
|------|---------|
| `Aurisic_Financials_3-25-1.xlsx` | March template — copy structure, tab order, formatting |
| `Aurisic_Final_TB_4-25-1.txt` | April trial balance (system dump) → drives Tab 3a |
| `Aurisic_Prepaid_Expenses_4-25-1.xlsx` | Prepaid expense detail → Tab 7 |
| `PPD1250-1.xlsx` | Prepaid Expenses schedule #1250 → Tab 7 |
| `PPD1251-1.xlsx` | Prepaid Insurance schedule #1251 → Tab 8 |
| `Prof_Fee_Dump-1.xlsx` | Professional fees detail → Tab 9 |
| `Legal_Dump-1.xlsx` | Legal/audit expense detail → Tab 10 |
| `Good Insurance Co - Loan.xlsx` | Loan I amortization → Tab 11a |
| `Good Insurance Co - Loan II.xlsx` | Loan II amortization → Tab 11b |
| `Outstanding_CKs_4-30-25-1.xlsx` | Outstanding checks → Tab 5 (bank recon) |
| `AR_Accrual-1.xlsx` | A/R accruals → Tab 13 |
| `Payroll-1.xlsx` | Payroll accrual detail → Tab 14 |
| `Aurisic_Corp_Payrolls_April_2025-1.xlsx` | April payroll register → Tab 14 |
| `AccrBonus-1.xlsx` | Bonus accrual → Tab 14 or new tab |
| `Rebates-1.xlsx` | Vendor rebates → Tab 15 |
| `Accr2011-1.xlsx` | New accrual schedule (account #2011) → new tab |
| `AccrMisc-1.xlsx` | Misc accrual schedule → new tab |

> **Note**: The task prompt references `AP_TB-1.xlsx` but this file is not present in the reference files. Derive AP Trade balances (Tab 12) from the trial balance (`Aurisic_Final_TB_4-25-1.txt`, account #2000).

---

## Step 1 — Read all reference files before doing anything else

### 1a. Read the March template
Open `Aurisic_Financials_3-25-1.xlsx` and record:
- **All sheet names in order** (Tab 0 = TOC, then Tab 3a onward)
- For each sheet: column headers, row structure, and any date labels (3-31-25, March, etc.) that will need updating

### 1b. Parse the April trial balance
Open `Aurisic_Final_TB_4-25-1.txt` and record:
- Column structure (Div # | Acct # | Account Name | MTD Amt | YTD Amt | code)
- All account numbers present
- Divisions (expect 0010 and 0012)

### 1c. Read each supporting schedule
For each source file, note:
- Sheet names and column headers
- Row structure and whether it mirrors the March template or is a fresh data dump

Do not build any output until this mapping is written out explicitly.

---

## Step 2 — Output spec

**Filename**: `output/Aurisic_Financials_4-25-1.xlsx`

**Tab order**:
| Tab | Name | Source |
|-----|------|--------|
| 0 | Table of Contents | Update from March TOC |
| 3a | #3a) TB convert 4-30-25 | `Aurisic_Final_TB_4-25-1.txt` |
| 4 | #4) Cash Availability Status | TB (cash accounts) |
| 5 | #5) Bank recon 4-30-25 | `Outstanding_CKs_4-30-25-1.xlsx` + TB |
| 6 | #6) Aurisic Funding Sources | `Good Insurance Co - Loan.xlsx/II` |
| 7 | #7) PPD Exps #1250 | `PPD1250-1.xlsx` + `Aurisic_Prepaid_Expenses_4-25-1.xlsx` |
| 8 | #8) PPD Ins #1251 | `PPD1251-1.xlsx` |
| 9 | #9) Prof Fees Accrual #2404 | `Prof_Fee_Dump-1.xlsx` |
| 10 | #10) Legal Audit Expense #6200 | `Legal_Dump-1.xlsx` |
| 11a | #11a) Interest Accruals I | `Good Insurance Co - Loan.xlsx` |
| 11b | #11b) Interest Accruals II | `Good Insurance Co - Loan II.xlsx` |
| 12 | #12) AP Trade #2000 | TB account #2000 |
| 13 | #13) AR Accruals #1101 | `AR_Accrual-1.xlsx` |
| 14 | #14) Payroll Accrual #2200 | `Payroll-1.xlsx` + `Aurisic_Corp_Payrolls_April_2025-1.xlsx` + `AccrBonus-1.xlsx` |
| 15 | #15) Vendor Rebates #2005 | `Rebates-1.xlsx` |
| New | New tabs from Accr2011, AccrMisc | `Accr2011-1.xlsx`, `AccrMisc-1.xlsx` |

**Tabs 1, 2, 2a, 3 — DO NOT include. These are reserved for the CFO.**

---

## Step 3 — Tab-by-tab update rules

### Tab 0: Table of Contents
- Update all date references: `3-31-25` → `4-30-25`, `March` → `April`, `3-25` → `4-25`
- Add rows for any new tabs (Accr2011, AccrMisc) with their tab numbers and descriptions
- Update status/comments column to reflect April data

### Tab 3a: TB Convert (4-30-25)
- Source: `Aurisic_Final_TB_4-25-1.txt`
- Parse the text file: columns are Div # | Acct # | Account Name | MTD Amt | YTD Amt | code
- Load all rows preserving the Div/Acct/Name/MTD/YTD/code structure
- Update tab name from `#3a) TB convert 3-31-25` → `#3a) TB convert 4-30-25`
- Update any header date from 3/31/2025 → 4/30/2025

### Tab 4: Cash Availability Status
- Extract cash account balances from the April TB (accounts in the 1020–1030 range)
- Update all amounts and date references to April

### Tab 5: Bank Recon (4-30-25)
- Source: `Outstanding_CKs_4-30-25-1.xlsx`
- Structure: bank balance per statement → add deposits in transit → subtract outstanding checks → adjusted balance
- Outstanding checks come from `Outstanding_CKs_4-30-25-1.xlsx`
- GL balance per TB should equal adjusted book balance
- Update tab name: `#5) Bank recon 3-31-25` → `#5) Bank recon 4-30-25`

### Tab 6: Aurisic Funding Sources
- Source: `Good Insurance Co - Loan.xlsx` and `Good Insurance Co - Loan II.xlsx`
- Update loan balances, interest accrual, and payment schedule to April

### Tab 7: PPD Exps #1250
- Source: `PPD1250-1.xlsx` (primary) and `Aurisic_Prepaid_Expenses_4-25-1.xlsx`
- Copy the April schedule as-is if the source file mirrors the March tab structure
- If the source is a raw data dump, reconstruct the tab using the March format with April data
- Format: Vendor | Debit Adds | Credit w/o's | Balance

### Tab 8: PPD Ins #1251
- Source: `PPD1251-1.xlsx`
- Same approach as Tab 7

### Tab 9: Prof Fees Accrual #2404
- Source: `Prof_Fee_Dump-1.xlsx`
- Update with April professional fee accruals

### Tab 10: Legal Audit Expense #6200
- Source: `Legal_Dump-1.xlsx`
- Update with April legal/audit expense detail

### Tabs 11a & 11b: Interest Accruals I and II
- Source: `Good Insurance Co - Loan.xlsx` (11a) and `Good Insurance Co - Loan II.xlsx` (11b)
- Update outstanding balance, April interest accrual, and cumulative YTD interest

### Tab 12: AP Trade #2000
- Source: April TB (account #2000)
- **Note**: `AP_TB-1.xlsx` referenced in the prompt is not available — use the TB balance directly
- List vendor balances as available; if only the summary total is in the TB, record total AP balance per TB

### Tab 13: AR Accruals #1101
- Source: `AR_Accrual-1.xlsx`
- Copy April A/R accrual detail (Reference | Amount format)

### Tab 14: Payroll Accrual #2200
- Source: `Payroll-1.xlsx`, `Aurisic_Corp_Payrolls_April_2025-1.xlsx`, `AccrBonus-1.xlsx`
- Include regular payroll accrual, corporate payroll entries, and bonus accrual
- If `AccrBonus-1.xlsx` matches the structure of the existing payroll tab, add bonus as a line item
- If it is a separate schedule, consider adding as a sub-section or note at the bottom

### Tab 15: Vendor Rebates #2005
- Source: `Rebates-1.xlsx`
- Update with April vendor rebate detail

### New tabs (Accr2011, AccrMisc)
- Source: `Accr2011-1.xlsx`, `AccrMisc-1.xlsx`
- Add each as a new tab at the end of the workbook, after Tab 15
- Name them consistently with the existing convention (e.g., `#16) Accr Exps #2011`, `#17) Misc Accrual`)
- Add both to the TOC in Tab 0

---

## Step 4 — Flag discrepancies clearly

If any of the following occur, add a visible note (yellow cell fill, bold text "FLAG:") in the relevant tab:
- A source file balance does not reconcile to the TB
- A referenced file is missing (`AP_TB-1.xlsx` — note this in Tab 12)
- Data is inconsistent between two source files
- Any amount that looks incorrect relative to March figures

---

## Step 5 — Produce the Excel file with Python

Use `openpyxl` to build the workbook. Guidelines:
- Copy the March template sheet by sheet as the base, then update values
- Preserve column widths, bold headers, and number formats from the March file
- Apply `"$#,##0.00"` to all currency cells
- Apply `"MM/DD/YYYY"` to all date cells
- Rename any tab containing `3-31-25` or `3-25` to the April equivalent
- All totals must use Excel SUM formulas, not hardcoded values

Save to `output/Aurisic_Financials_4-25-1.xlsx`

---

## Step 6 — Self-verification checklist

**File delivery**
- [ ] File exists at `output/Aurisic_Financials_4-25-1.xlsx`
- [ ] File opens without error (`openpyxl.load_workbook()` succeeds)

**Tab structure**
- [ ] Tabs 1, 2, 2a, 3 are NOT present (CFO-only)
- [ ] Tab 0 (TOC) is present and updated for April
- [ ] All tabs 3a through 15 are present
- [ ] New tabs (Accr2011, AccrMisc) added at the end
- [ ] TOC references all tabs including new ones
- [ ] No tab still contains `3-31-25` or `3-25` in its name

**Date references**
- [ ] All in-cell date labels updated to April (4/30/2025, April 2025, 4-25)
- [ ] No March dates remaining in headers or titles

**Trial balance (Tab 3a)**
- [ ] All rows from `Aurisic_Final_TB_4-25-1.txt` are loaded
- [ ] Div #, Acct #, MTD Amt, YTD Amt columns are populated
- [ ] Both divisions (0010, 0012) present if applicable

**Bank recon (Tab 5)**
- [ ] Outstanding checks list sourced from `Outstanding_CKs_4-30-25-1.xlsx`
- [ ] Adjusted book balance reconciles to GL cash account per TB

**Prepaid schedules (Tabs 7 & 8)**
- [ ] Tab 7 uses April prepaid expense data
- [ ] Tab 8 uses April prepaid insurance data

**Flagged items**
- [ ] Missing `AP_TB-1.xlsx` noted in Tab 12
- [ ] Any other reconciliation issues flagged with "FLAG:" labels

**Formatting**
- [ ] Currency cells formatted `$#,##0.00`
- [ ] No placeholder text in any data cell
- [ ] Column widths match March template
