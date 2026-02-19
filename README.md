# Data Analysis — Anscombe's Quartet

An exploratory analysis and visualisation of **Anscombe's Quartet**, a classic dataset that demonstrates why plotting data is essential and why summary statistics alone can be misleading.

---

## Dataset

**File:** `anscombe_quartet.tsv`
Tab-separated file with 44 rows (11 per group) and 3 columns:

| Column | Description |
|--------|-------------|
| `dataset` | Group label — I, II, III, or IV |
| `x` | x-coordinate |
| `y` | y-coordinate |

---

## What was done

### v1 — `anscombe_analysis.ipynb`

- Loaded the TSV dataset with pandas
- Computed **descriptive statistics** (count, mean, std, min, quartiles, max) for each of the four groups
- Produced a cross-group summary table of means and standard deviations, confirming their near-identical values
- Generated a **2×2 subplot scatter plot** (matplotlib) with:
  - One subplot per group
  - A distinct colour per group
  - A dashed OLS regression line overlaid on each subplot
- Saved the chart as `anscombe_scatter.png`
- All steps documented with inline markdown explanations

### v2 — `anscombe_analysis_v2.ipynb` *(iteration-1)*

- Rebuilt the scatter plot using **Altair** (Vega-Lite based)
- All four groups plotted on a **single combined chart** (no subplots)
- **Regression lines removed**
- Colour scheme uses Altair's `set1` qualitative palette; groups are also encoded by **shape** for accessibility
- Chart is **interactive** (pan & zoom) when viewed in the notebook
- Saved the chart as `anscombe_scatter_v2.png`

---

## Key finding

All four groups share nearly identical summary statistics:

- Mean of x ≈ 9.0, mean of y ≈ 7.5
- Standard deviation of x ≈ 3.32, std of y ≈ 2.03
- Pearson correlation ≈ 0.816

Yet their underlying patterns are completely different:

| Group | Pattern |
|-------|---------|
| I | Well-behaved linear scatter |
| II | Clear quadratic (curved) relationship |
| III | Linear with one extreme outlier |
| IV | All x values identical except one high-leverage point |

> **Always visualise your data — summary statistics alone will mislead you.**

---

## Files

| File | Description |
|------|-------------|
| `anscombe_quartet.tsv` | Source dataset |
| `PLAN.md` | Project plan and iteration goals |
| `anscombe_analysis.ipynb` | v1 notebook (matplotlib, 2×2 subplots) |
| `anscombe_scatter.png` | v1 chart output |
| `anscombe_analysis_v2.ipynb` | v2 notebook (Altair, single plot, iteration-1) |
| `anscombe_scatter_v2.png` | v2 chart output |

---

## Requirements

```
pandas
matplotlib
numpy
altair>=6.0
vl-convert-python
```

Install with:

```bash
pip install pandas matplotlib numpy altair vl-convert-python
```
