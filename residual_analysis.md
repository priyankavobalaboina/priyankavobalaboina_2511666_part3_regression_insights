
# Residual Analysis

## What Are Residuals?

A residual is the difference between the actual observed value and the value predicted by our regression model:

**Residual = Actual Sales − Predicted Sales**

- **Positive residual:** The store performed BETTER than the model predicted (under-predicted)
- **Negative residual:** The store performed WORSE than the model predicted (over-predicted)

## Model Used

Multiple Regression Model (Model 3):
```
monthly_sales = 91,266.06 + 28.9428×footfall + 1.1626×marketing_spend 
                + 2,636.17×staff_count + 3,100.12×inventory_availability_pct 
                + 39,962.03×type_Airport + 17,557.64×type_HighStreet + 28,984.87×type_Mall
```

## Top 5 Largest Positive Residuals (Under-Predicted Stores)

These stores performed significantly BETTER than the model expected:

| # | Store ID | Region | Store Type | Actual Sales | Predicted Sales | Residual |
|---|----------|--------|------------|-------------|-----------------|----------|
| 1 | STR-1030 | West | Residential | $820,519.04 | $712,863.12 | +$107,655.92 |
| 2 | STR-1073 | East | Residential | $813,316.71 | $710,743.06 | +$102,573.65 |
| 3 | STR-1028 | East | Mall | $713,611.16 | $615,096.53 | +$98,514.63 |
| 4 | STR-1032 | South | High Street | $914,544.17 | $820,285.03 | +$94,259.14 |
| 5 | STR-1026 | East | Mall | $625,514.04 | $531,605.80 | +$93,908.24 |

### Business Interpretation (Positive Residuals)
These stores are **outperforming** what their measurable characteristics would suggest. Possible reasons:
- Exceptional store management or staff quality not captured in the data
- Strong local brand loyalty or community engagement
- Favorable micro-location factors (e.g., near transit hub, popular anchor tenant)
- Effective local promotions or partnerships not reflected in overall marketing spend
- These stores may represent **best practices** worth studying and replicating

## Top 5 Largest Negative Residuals (Over-Predicted Stores)

These stores performed significantly WORSE than the model expected:

| # | Store ID | Region | Store Type | Actual Sales | Predicted Sales | Residual |
|---|----------|--------|------------|-------------|-----------------|----------|
| 1 | STR-1017 | West | High Street | $685,379.08 | $839,367.38 | −$153,988.30 |
| 2 | STR-1012 | West | Residential | $595,467.60 | $719,855.23 | −$124,387.63 |
| 3 | STR-1023 | South | Mall | $627,171.90 | $742,440.87 | −$115,268.97 |
| 4 | STR-1007 | West | Mall | $800,451.94 | $904,299.21 | −$103,847.27 |
| 5 | STR-1001 | East | Residential | $658,920.30 | $760,358.83 | −$101,438.53 |

### Business Interpretation (Negative Residuals)
These stores are **underperforming** relative to their potential. Possible reasons:
- Operational issues (poor layout, inadequate customer service, stock management problems)
- Strong local competition not fully captured by competitor_distance_km alone
- Unfavorable local conditions (construction, parking issues, declining neighborhood)
- Staff turnover or training gaps reducing conversion rates
- These stores may need **management attention or intervention**

## Patterns Observed

1. **West region appears in 3 of 5 negative residuals** — suggesting the model may slightly over-predict for some West region stores, or there are West-specific challenges not captured
2. **Residential and Mall stores appear in both lists** — no single store type is systematically over/under-predicted
3. **The largest negative residual ($153,988) is bigger than the largest positive ($107,656)** — a few stores are significantly underperforming their potential

## Does the Model Systematically Over-Predict or Under-Predict?

- The mean residual is approximately $0 (by design in OLS regression)
- However, individual stores show large deviations in both directions
- The model appears to slightly struggle with stores that have **high footfall but lower-than-expected conversion** (negative residuals)
- Stores with **strong local factors** (community loyalty, exceptional management) tend to be under-predicted

## Recommendations Based on Residual Analysis

1. **Investigate STR-1017 (West, High Street)** — largest underperformer with $154K gap; may need operational review
2. **Study STR-1030 (West, Residential)** — top outperformer; identify what makes this store successful despite similar inputs
3. **Consider adding variables** like staff experience, store age, or local competition intensity to reduce residual size
4. **Use residuals for performance benchmarking** — stores with large negative residuals may benefit from targeted improvement programs
