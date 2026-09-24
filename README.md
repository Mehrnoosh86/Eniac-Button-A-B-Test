# Eniac Button A/B Test

## Project Overview

This project analyzes an A/B test conducted for Eniac’s homepage. The experiment compared four versions of the main call-to-action button to determine which design generated the strongest user engagement.

The tested versions were:

- **Version A:** White `SHOP NOW`
- **Version B:** Red `SHOP NOW`
- **Version C:** White `SEE DEALS`
- **Version D:** Red `SEE DEALS`

The main business objective was to identify whether button color and wording influenced users’ likelihood of clicking through to the next page.

## Business Question

Which homepage button version should Eniac use to achieve the highest click-through rate?

The primary success metric was the homepage click-through rate (CTR):

```text
CTR = button clicks / homepage visits
```

Additional metrics considered in the project included drop-off rate and homepage-return rate.

## Experiment Design

- Experiment duration: 14 days.
- Number of variants: 4.
- Significance level: `α = 0.05`.
- Statistical power: 80%.
- Minimum detectable effect: 20%.
- Primary KPI: homepage CTR.

### Hypotheses

**Null hypothesis (H0):**

All four button versions have the same CTR. Any observed differences are caused by random variation.

**Alternative hypothesis (HA):**

At least one button version has a different CTR.

## Dataset

The repository contains four CSV files:

- `eniac_a.csv`
- `eniac_b-2.csv`
- `eniac_c-3.csv`
- `eniac_d-4.csv`

Each file contains information about page elements, including:

- Element ID.
- HTML tag name.
- Element name.
- Number of clicks.
- Visibility status.
- Snapshot information, including visits and total page clicks.

The main button click count was extracted from the row containing `SHOP NOW` or `SEE DEALS`. Homepage visits were extracted from the `mySidebar` row.

## Observed Results

| Version | Button design | Visits | Button clicks | CTR |
|---|---|---:|---:|---:|
| A | White `SHOP NOW` | 25,326 | 512 | 2.02% |
| B | Red `SHOP NOW` | 24,747 | 281 | 1.14% |
| C | White `SEE DEALS` | 24,876 | 527 | 2.12% |
| D | Red `SEE DEALS` | 25,233 | 193 | 0.76% |

Based on the observed CTR:

1. Version C had the highest CTR.
2. Version A had the second-highest CTR and was very close to C.
3. Version B performed worse than both white-button variants.
4. Version D had the lowest CTR.

## Statistical Analysis

Because the outcome is categorical (`Click` versus `No-click`) and the experiment compares four categorical versions, a Chi-square test of independence was used.

The contingency table contained:

- Clicks for each version.
- Non-clicks for each version.

Non-clicks were calculated as:

```text
No-clicks = visits - button clicks
```

### Overall Chi-square Test

The overall Chi-square test showed a statistically significant difference between the four button versions.

This means that the observed differences in CTR are unlikely to be explained by random variation alone. However, the overall test only shows that at least one version differs; it does not identify a unique winner.

### Post-hoc Analysis

Six pairwise comparisons were performed:

- A vs B
- A vs C
- A vs D
- B vs C
- B vs D
- C vs D

To control the risk of Type I error, a Bonferroni correction was applied:

```text
Adjusted alpha = 0.05 / 6 = 0.00833
```

Results:

| Comparison | Result |
|---|---|
| A vs B | Significant |
| A vs C | Not significant |
| A vs D | Significant |
| B vs C | Significant |
| B vs D | Significant |
| C vs D | Significant |

## Key Findings

- The button version is associated with users’ click behavior.
- White buttons performed substantially better than red buttons.
- Version C had the highest observed CTR.
- Version C was not statistically better than Version A.
- Versions A and C both performed significantly better than B and D.
- The evidence does not support declaring C the unique winner over A.

## Additional Metrics

The project also considered drop-off rate and homepage-return rate.

Reported drop-off rates:

| Version | Drop-off rate |
|---|---:|
| A | 62% |
| B | Not available |
| C | 71% |
| D | 69% |

A lower drop-off rate is preferable. Additional data for Version B were unavailable, so comparisons using these secondary metrics should be interpreted cautiously.

CTR measures initial engagement only. A higher CTR does not necessarily guarantee more completed purchases or higher revenue.

## Recommendation

If Version A is the current production version, it should be retained for now. Moving from A to C is not supported by a statistically significant CTR improvement.

The recommended next step is a focused follow-up experiment comparing only:

- Version A: White `SHOP NOW`.
- Version C: White `SEE DEALS`.

The follow-up experiment should predefine:

- Primary KPI.
- Significance level.
- Statistical power.
- Minimum detectable effect.
- Experiment duration.
- Secondary conversion metrics.

## Limitations

- The overall Chi-square test does not identify a single winning version.
- Multiple pairwise comparisons require correction for Type I error.
- Differences smaller than the 20% minimum detectable effect may not be detected reliably.
- Drop-off and homepage-return data are incomplete for Version B.
- CTR does not measure completed purchases, revenue, or long-term customer value.
- Results may depend on the specific traffic period and user population included in the experiment.

## Files

| File | Description |
|---|---|
| `Eniac_AB_Testing.ipynb` | Main analysis notebook |
| `eniac_a.csv` | Version A data |
| `eniac_b.csv` | Version B data |
| `eniac_c.csv` | Version C data |
| `eniac_d.csv` | Version D data |
| `Eniac_AB_Testing_Presentation.pptx` | Management presentation |

## Tools and Libraries

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- SciPy
- Jupyter Notebook / Google Colab

## How to Run

1. Open `Eniac_AB_Testing.ipynb` in Jupyter Notebook or Google Colab.
2. Upload or place the four CSV files in the working directory.
3. Run the cells from top to bottom.
4. Review the exploratory analysis, CTR calculations, Chi-square test, and post-hoc comparisons.
5. Confirm that all outputs are reproducible before submitting the project.

## Team

This project was completed collaboratively by **Tim Maximilian Ernst**, **Giovanni Marco Petraroli**, and **Mehrnoosh Mohebi Damabi**. The team worked across data exploration, cleaning, validation, analysis, visualization, interpretation, and recommendations. Each member independently produced analysis outputs before the team compared results and selected the final approach through discussion.

## License

This project is intended for educational purposes.

## Authors

ENIAC Data Analytics Team: Tim Maximilian Ernst, Giovanni Marco Petraroli, Mehrnoosh Mohebi Damabi

_Last updated: September 2026._
