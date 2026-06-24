
# Final Recommendation: Regression Analysis for Monthly Sales Prediction

## Executive Summary

After evaluating three regression models to predict monthly store sales, **Model 3 (Multiple Linear Regression)** is recommended as the final model. It explains **82.24%** of sales variation with all predictors statistically significant at α = 0.05.

---

## Models Evaluated

| Metric | Model 1 (Footfall) | Model 2 (Marketing Spend) | Model 3 (Multiple Regression) |
|--------|-------------------|--------------------------|-------------------------------|
| Type | Simple Linear | Simple Linear | Multiple Linear |
| R-squared | 0.7363 | 0.1673 | **0.8224** |
| Adjusted R-squared | 0.7355 | 0.1647 | **0.8184** |
| Standard Error | $53,373.74 | $94,846.03 | **$44,223.53** |
| F-statistic | 887.85 | 63.86 | 206.35 |
| F-test p-value | <0.001 | <0.001 | <0.001 |
| All Variables Significant? | Yes | Yes | Yes (all p < 0.05) |
| Recommendation | Not selected | Not selected | **SELECTED** |

---

## Final Model: Multiple Linear Regression (Model 3)

### Regression Equation

```
monthly_sales = 91,266.06
  + 28.9428 × footfall
  + 1.1626 × marketing_spend
  + 2,636.17 × staff_count
  + 3,100.12 × inventory_availability_pct
  + 39,962.03 × type_Airport
  + 17,557.64 × type_HighStreet
  + 28,984.87 × type_Mall
```

### Model Statistics

- **R-squared:** 0.8224 (82.24% of sales variation explained)
- **Adjusted R-squared:** 0.8184
- **Standard Error:** $44,223.53
- **F-statistic:** 206.35 (p < 0.001)
- **Observations:** 320

### Coefficient Details & Significance

| Variable | Coefficient | Std Error | t-Stat | P-value | Significant? |
|----------|------------|-----------|--------|---------|--------------|
| Intercept | $91,266.06 | $43,280.02 | 2.1087 | 0.0358 < 0.05 | Yes ✓ |
| footfall | $28.9428 | $2.5054 | 11.5522 | <0.001 < 0.05 | Yes ✓ |
| marketing_spend | $1.1626 | $0.1281 | 9.0757 | <0.001 < 0.05 | Yes ✓ |
| staff_count | $2,636.17 | $1,270.51 | 2.0749 | 0.0388 < 0.05 | Yes ✓ |
| inventory_availability_pct | $3,100.12 | $464.08 | 6.6802 | <0.001 < 0.05 | Yes ✓ |
| type_Airport | $39,962.03 | $9,467.18 | 4.2211 | <0.001 < 0.05 | Yes ✓ |
| type_HighStreet | $17,557.64 | $6,082.63 | 2.8865 | 0.0042 < 0.05 | Yes ✓ |
| type_Mall | $28,984.87 | $6,746.88 | 4.2960 | <0.001 < 0.05 | Yes ✓ |

---

## Why Model 3 is Recommended

1. **Highest Explanatory Power:** R² = 0.8224, explaining 82.24% of sales variation (vs. 73.6% for Model 1 and 16.7% for Model 2)
2. **Lowest Prediction Error:** Standard Error of $44,223.53 provides the most precise predictions
3. **No Overfitting:** Adjusted R² (0.8184) is very close to R² (0.8224), with a difference of only 0.004
4. **All Predictors Significant:** Every variable passes the significance test at α = 0.05
5. **Multi-Factor Insights:** Captures the effect of store type, staffing, inventory, and marketing — providing actionable levers for business decisions

---

## Key Business Insights

### Strongest Predictors (by t-statistic)

1. **Footfall** (t = 11.55): Each additional visitor adds ~$28.94 to sales — the single most impactful driver
2. **Marketing Spend** (t = 9.08): Each $1 invested in marketing returns ~$1.16 in sales
3. **Inventory Availability** (t = 6.68): Each 1% increase in stock availability adds ~$3,100 to sales

### Store Type Performance (vs. Residential baseline)

- **Airport stores:** Earn ~$39,962 more per month than Residential stores
- **Mall stores:** Earn ~$28,985 more per month than Residential stores
- **High Street stores:** Earn ~$17,558 more per month than Residential stores

### Staffing Impact

- Each additional staff member contributes ~$2,636 to monthly sales

---

## Residual Analysis Summary

| Metric | Value |
|--------|-------|
| Mean Residual | ≈ $0.00 (confirms unbiased model) |
| Std Dev of Residuals | $43,735.63 |
| Mean Absolute Residual | $34,241.38 |
| Max Over-Prediction | -$153,988.30 |
| Max Under-Prediction | $107,655.92 |

---

## Actionable Recommendations

- **Prioritize footfall growth:** Invest in location visibility, signage, and events to drive store traffic — the highest-impact lever
- **Maintain inventory above 90%:** Each percentage point of availability translates to ~$3,100 in additional sales
- **Optimize marketing ROI:** Marketing spend shows positive returns ($1.16 per $1 spent), but should be paired with footfall strategies for maximum impact
- **Expand Airport and Mall formats:** These store types significantly outperform Residential locations
- **Staff appropriately:** Ensure adequate staffing levels, as each additional team member contributes meaningfully to revenue

---

## Limitations & Next Steps

- **Unexplained variance (17.8%):** Factors like seasonality, local competition, and customer demographics may account for remaining variation
- **Consider interaction effects:** Footfall × store type interactions could improve predictions
- **Validate with holdout data:** Test model on new months (e.g., May–June 2025) to confirm generalizability
- **Monitor residual outliers:** Stores with large residuals (e.g., STR-1017, STR-1012) warrant operational review

---

*Analysis based on 320 observations across 80 stores (Jan–Apr 2025), 4 regions, and 4 store types.*
