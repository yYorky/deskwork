# SKILL: AFC Audit Sampling Workpaper

## Task
Perform audit sample selection on Anti-Financial Crime Risk Metrics for Q2 and Q3 2024. Produce a new Excel workbook titled "Sample" containing the selected sample and the sample size calculation workings.

## Reference file
- `Population v2.xlsx` — AFC Risk Metrics for Q2 and Q3 2024 (the full population to sample from)

---

## Step 1 — Read the Population file completely before doing anything else

Open `Population v2.xlsx` and map:
- All column headers (especially columns H, I, J, K)
- Total number of rows (population size N)
- The fields available: entity name, division, sub-division, metric code, country, Q2 value (col H), Q3 value (col I)
- Any existing values in columns J or K

Do not begin calculations until the population structure is fully documented.

---

## Step 2 — Sample size calculation (Tab 2 of output)

Use the **attribute sampling formula** at 90% confidence, 10% tolerable error rate:

```
n = (Z² × p × (1 - p)) / E²
```
Where:
- Z = 1.645 (one-tailed) or 1.960 (two-tailed at 90% confidence) — use Z = 1.645 for attribute sampling
- p = 0.5 (maximum variability / most conservative estimate)
- E = 0.10 (tolerable error rate)

```
n = (1.645² × 0.5 × 0.5) / 0.10²
  = (2.706 × 0.25) / 0.01
  = 0.6765 / 0.01
  = 67.65 → round up to 68
```

Show all workings in Tab 2. Label each variable clearly.

*Note: Apply finite population correction if population size N < 10× sample size:*
`n_adjusted = n / (1 + (n-1)/N)`

---

## Step 3 — Variance analysis (column J in Population sheet)

For every row in the Population, calculate quarter-on-quarter variance in column J:

```
If Q2 = 0 and Q3 = 0: J = "0%"
If Q2 = 0 and Q3 ≠ 0: J = "N/M" (not meaningful — new metric)
Otherwise: J = (Q3 - Q2) / |Q2|  [expressed as percentage]
```

---

## Step 4 — Sample selection (column K in Population sheet)

Mark selected rows with `1` in column K. Unselected rows leave column K blank.

Apply these selection criteria. Every selected row must satisfy **at least one** criterion. Every criterion below must be satisfied by **at least one** selected row.

| Criterion | Selection rule |
|-----------|---------------|
| High variance | QoQ variance > 20% — prioritise rows with exceptionally large % changes |
| Flagged entities | Include rows for: CB Cash Italy, CB Correspondent Banking Greece, IB Debt Markets Luxembourg, CB Trade Finance Brazil, PB EMEA UAE |
| High-risk metrics | Include metrics A1 and C1 |
| Zero-zero rows | Include rows where both Q2 and Q3 = 0 |
| Business lines | Include rows from Trade Finance and Correspondent Banking businesses |
| Jurisdictions | Include rows from Cayman Islands, Pakistan, and UAE |
| Coverage | Ensure at least one row from every distinct Division and sub-Division |

Total selected rows should be ≥ calculated sample size (from Step 2). If mandatory criteria alone exceed the sample size, include all mandatory items.

---

## Step 5 — Produce the output workbook

Save to `output/Sample.xlsx`

**Tab 1 — Sample**
Copy all selected rows from the Population sheet (where K = 1), in original order.
Include all original columns plus column J (variance) and column K (= 1 for all rows in this tab).

**Tab 2 — Sample Size Calculation**
Show all workings from Step 2:
- Confidence level, Z-value, tolerable error rate, p-value
- Formula applied
- Raw sample size, any finite population correction, final sample size
- Population size N

---

## Step 6 — Self-verification checklist

**File delivery**
- [ ] File exists at `output/Sample.xlsx`
- [ ] File opens without error

**Structure**
- [ ] Two tabs: "Sample" and "Sample Size Calculation"
- [ ] Tab 1 contains only selected rows (K = 1), all columns present including J and K
- [ ] Tab 2 shows all formula workings with labelled variables

**Sample size calculation**
- [ ] Confidence level = 90%, tolerable error rate = 10%
- [ ] Z-value correctly applied
- [ ] Final sample size stated and justified
- [ ] Finite population correction applied if applicable

**Variance analysis**
- [ ] Column J calculated for every row in the Population
- [ ] Zero/zero rows flagged appropriately
- [ ] New metrics (Q2=0, Q3≠0) flagged as N/M

**Sample selection — criterion coverage (every box must be checked)**
- [ ] At least one row with QoQ variance > 20% — including highest-variance rows
- [ ] CB Cash Italy present
- [ ] CB Correspondent Banking Greece present
- [ ] IB Debt Markets Luxembourg present
- [ ] CB Trade Finance Brazil present
- [ ] PB EMEA UAE present
- [ ] Metric A1 present
- [ ] Metric C1 present
- [ ] At least one zero-zero row present
- [ ] At least one Trade Finance row present
- [ ] At least one Correspondent Banking row present
- [ ] At least one Cayman Islands row present
- [ ] At least one Pakistan row present
- [ ] At least one UAE row present
- [ ] All Divisions represented
- [ ] All sub-Divisions represented
- [ ] Total selected rows ≥ calculated sample size
