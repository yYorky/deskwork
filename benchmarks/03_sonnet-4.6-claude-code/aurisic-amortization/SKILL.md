# SKILL: Aurisic Prepaid Amortization Schedule

## Task
Produce a 3-tab Excel workbook containing a prepaid expense and insurance amortization schedule for Aurisic, covering January–April 2025. All schedules must reconcile to the GL balances provided in the task prompt.

## Reference files
- `COA.xlsx` — Chart of accounts (account numbers and names)
- `Aurisic_Prepaid_Insurance.pdf` — Insurance invoices
- `Aurisic_Prepaid_Expenses_Jan25.pdf` — January prepaid expense invoices
- `Aurisic_Prepaid_Expenses_Feb25.pdf` — February prepaid expense invoices
- `Aurisic_Prepaid_Expenses_Mar25.pdf` — March prepaid expense invoices
- `Aurisic_Prepaid_Expenses_Apr25.pdf` — April prepaid expense invoices

---

## Step 1 — Read all 6 reference files before doing anything else

**COA.xlsx**: Note account numbers for Prepaid Expenses and Prepaid Insurance (expect #1250 and #1251).

**Each monthly PDF**: Extract for every invoice:
- Vendor name
- Invoice date
- Invoice amount
- Amortization period (if stated)

**Insurance PDF**: Extract for each policy:
- Insurer name
- Policy period (start date, end date)
- Total premium amount
- Payment schedule (monthly, annual, etc.)

Write out a complete invoice register before building any schedules.

---

## Step 2 — Output spec (3-tab workbook)

Save to `output/Aurisic_Prepaid_Amortization_Apr2025.xlsx`

### Tab 1 — Prepaid Summary
Header: "Aurisic | Prepaid Expenses & Insurance Summary | As of 4/30/2025"

| Row | Content |
|-----|---------|
| Prepaid Expenses (1250) | YTD additions, YTD amortization, ending balance |
| Prepaid Insurance (1251) | YTD additions, YTD amortization, ending balance |
| Total | Combined totals |

Pull all figures from the detail tabs — no hardcoded values in this tab.

### Tab 2 — Prepaid Expenses (Account #1250)
One row per invoice. Columns:
- Vendor | Invoice Date | Original Amount | Amortization Period (months) | Monthly Expense | Jan | Feb | Mar | Apr | Ending Balance

Bottom section: monthly activity summary (total additions, total amortization, ending balance by month).

Reconcile ending balance each month to the GL:
- Jan: $518,934.86
- Feb: $426,673.13
- Mar: $473,655.55
- Apr: $559,377.61

### Tab 3 — Prepaid Insurance (Account #1251)
Same structure as Tab 2.

Special rules:
- **Good Insurance**: 1/1/2025–12/31/2025 (12-month straight-line)
- **BCBS**: 2/1/2025–1/31/2026 monthly billing, first payment due 1/15/2025; each month = one month's premium

Reconcile ending balance each month to the GL:
- Jan: $506,657.98
- Feb: $461,097.55
- Mar: $415,537.13
- Apr: $369,976.70

---

## Step 3 — Apply these amortization rules exactly

### Default rule (Prepaid Expenses)
If no amortization period is specified on an invoice: **6 months starting in the month of the invoice date**.

Monthly expense = Invoice amount ÷ amortization period (straight-line, equal monthly amounts).

### Balance carried forward
Opening balance each month = prior month ending balance + new invoices received − amortization for the month.

### Reconciliation target
Every month-end balance in Tabs 2 and 3 must match the GL balances listed above. If they don't match, find and fix the discrepancy before finishing.

---

## Step 4 — Produce the Excel file with Python

Use `openpyxl` or `pandas`. Apply:
- Bold headers and column labels
- `"$#,##0.00"` number format on all currency cells
- Date columns in `MM/DD/YYYY` format
- Column widths adjusted to content
- Account numbers (#1250, #1251) visible in tab headers and sheet titles

---

## Step 5 — Self-verification checklist

**File delivery**
- [ ] File exists at `output/Aurisic_Prepaid_Amortization_Apr2025.xlsx`
- [ ] File opens without error

**Structure**
- [ ] Three tabs present: Prepaid Summary, Prepaid Expenses, Prepaid Insurance
- [ ] Header on each tab includes company name and reporting period
- [ ] Account numbers (#1250, #1251) present on correct tabs

**Calculations — Prepaid Expenses (1250)**
- [ ] Jan ending balance = $518,934.86
- [ ] Feb ending balance = $426,673.13
- [ ] Mar ending balance = $473,655.55
- [ ] Apr ending balance = $559,377.61
- [ ] Monthly expense = Invoice amount ÷ period (straight-line)
- [ ] Default 6-month period applied to invoices without a stated period

**Calculations — Prepaid Insurance (1251)**
- [ ] Jan ending balance = $506,657.98
- [ ] Feb ending balance = $461,097.55
- [ ] Mar ending balance = $415,537.13
- [ ] Apr ending balance = $369,976.70
- [ ] Good Insurance amortized over 12 months (1/1–12/31/2025)
- [ ] BCBS treated as monthly billing (each payment = one month's expense)

**Summary tab**
- [ ] All totals pulled from detail tabs, not hardcoded
- [ ] YTD totals match sum of Jan–Apr in detail tabs

**Formatting**
- [ ] No placeholder values in any cell
- [ ] All currency cells formatted as `$#,##0.00`
