# SKILL: Fall Music Tour P&L Report

## Task
Produce a structured Excel profit and loss report for the 2024 Fall Music Tour (October 2024), as-of December 31, 2024. Output is a `.xlsx` file used by production company executives to evaluate tour performance.

## Reference file
- `Fall Music Tour Ref File.xlsx` — contains income, costs, and tax withholding data from multiple sources (Tour Manager and production company)

---

## Step 1 — Read the reference file completely before anything else

Open `Fall Music Tour Ref File.xlsx` and list:
- Every sheet name and what it contains
- All revenue line items (city, country, amount, currency)
- All expense line items grouped by source (Tour Manager vs production company)
- Any exchange rates provided for non-USD revenue

Do not start calculating until this mapping is written out explicitly.

---

## Step 2 — Output spec

Single sheet Excel workbook structured as:

**Header row**: "2024 Fall Music Tour — Profit & Loss Statement  |  As of 12/31/2024"

**Columns**: Tour Manager | Production Company | Total Combined

**Section 1 — Revenue** (line-by-line by tour stop)
| Column | Content |
|--------|---------|
| City / Country | Each tour stop |
| Gross Revenue (USD) | Original amount converted to USD |
| Withholding Rate | Per country (see rates below) |
| Withholding Tax (USD) | Gross × rate |
| Net Revenue (USD) | Gross − Withholding |

Subtotal: Total Net Revenue

**Section 2 — Expenses** (by category)
- Band and Crew
- Other Tour Costs
- Hotel & Restaurants
- Other Travel Costs
- **Total Expenses**

**Section 3 — Net Income**
`Net Income = Total Net Revenue − Total Expenses`

---

## Step 3 — Apply these rules exactly

### Foreign tax withholding
Apply per-country rates to gross revenue:
- UK: 20%
- France: 15%
- Spain: 24%
- Germany: 15.825%

Formula: `Withholding Tax = Gross Revenue (USD) × Rate`
Formula: `Net Revenue = Gross Revenue (USD) − Withholding Tax`

### Currency conversion
- Convert all non-USD revenue to USD before applying withholding
- Use exchange rates from the reference file
- Show both original currency amount and USD equivalent if reference file provides the rate

### Separation by source
- Identify which revenue and expense items belong to Tour Manager vs production company
- Each section has three columns: Tour Manager | Production Company | Total Combined
- Total Combined = Tour Manager + Production Company for every line

---

## Step 4 — Produce the Excel file with Python

Use `openpyxl` to build the file. Apply:
- Bold header rows
- `"$#,##0.00"` number format on all currency cells
- Column widths adjusted to content
- Report title and "As of 12/31/2024" merged across the top
- No placeholder text in any cell

Save to `output/Fall_Music_Tour_PL_2024.xlsx`

---

## Step 5 — Self-verification checklist

Work through every item. Fix failures before finishing.

**File delivery**
- [ ] File exists at `output/Fall_Music_Tour_PL_2024.xlsx`
- [ ] File opens without error (`openpyxl.load_workbook()` succeeds)

**Structure**
- [ ] Header includes "As of 12/31/2024"
- [ ] Three columns present: Tour Manager | Production Company | Total Combined
- [ ] Revenue section has line-by-line tour stops with city and country
- [ ] All four expense categories present: Band and Crew, Other Tour Costs, Hotel & Restaurants, Other Travel Costs
- [ ] Net Income row is present

**Calculations**
- [ ] Withholding tax calculated at correct rate for each country
- [ ] Net Revenue = Gross Revenue − Withholding Tax for each stop
- [ ] Total Net Revenue = sum of all stop Net Revenue lines
- [ ] Total Expenses = sum of all four expense categories
- [ ] Net Income = Total Net Revenue − Total Expenses
- [ ] Total Combined = Tour Manager + Production Company for every row
- [ ] All USD conversions applied before withholding

**Formatting**
- [ ] All currency cells show `$#,##0.00` format
- [ ] No blank cells in data rows
- [ ] No hardcoded totals — every subtotal sums its components
