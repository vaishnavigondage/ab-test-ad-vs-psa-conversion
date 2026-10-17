# A/B Test Analysis: Ad vs PSA Conversion

Analysis of a marketing A/B test to find out whether showing ads increases conversion compared with a public service announcement (PSA) control, using a two-proportion z-test and a confidence interval for the lift.

## Business question
Do users shown the ad convert at a higher rate than users shown a PSA, and is the difference real or noise?

## Data
- Public dataset: Marketing A/B Testing on Kaggle ([add link])
- 588,101 users: 564,577 in the ad (test) group and 23,524 in the PSA (control) group
- Columns used: test group, converted (yes/no), total ads, most ads day, most ads hour
- Data quality: no duplicate user IDs, no missing values

## Method
- **Metric:** conversion rate (share of users who converted)
- **H₀:** conversion rate is the same in both groups
- **H₁:** conversion rates differ
- **Test:** two-proportion z-test, with a 95% confidence interval for the difference in rates
- **Tools:** Python, Pandas, NumPy, SciPy

## Results

| Group | Users | Converted | Conversion rate |
|---|---|---|---|
| Ad (test) | 564,577 | 14,423 | 2.55% |
| PSA (control) | 23,524 | 420 | 1.79% |

- **Lift:** +0.77 percentage points (+43% relative)
- **95% CI for the difference:** 0.60 to 0.94 percentage points
- **z = 7.37, p < 0.001:** reject H₀

## Recommendation
The ad group converts significantly more than the PSA group. Rolling the ad out makes sense **if** the value of the extra conversions outweighs the cost of running the ad. That cost data isn't in this dataset.

## Limitations
- The control is a PSA, so this measures ad vs a neutral message, not ad vs no ad.
- I can't verify how users were randomized, and there are no pre-experiment covariates to check group balance.
- The groups are very uneven in size (about 96% / 4%).
- No sample-size or power analysis was planned in advance.
- Day-of-week and hour patterns are observational, since neither was randomized. They are correlations, not causal effects.

## How to run
1. Download `marketing_AB.csv` from the Kaggle link above and place it in this folder.
2. Open `ab_test_analysis.ipynb` and run all cells.

```
pip install pandas numpy scipy matplotlib seaborn
```

## Files
- `ab_test_analysis.ipynb`: full analysis
- `README.md`: this file
