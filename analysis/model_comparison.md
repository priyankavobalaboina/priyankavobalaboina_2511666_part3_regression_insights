
# Model Comparison: Simple vs Multiple Regression

## Overview

Three regression models were built to understand what drives monthly sales across 80 retail stores over 4 months (320 observations). All models use `monthly_sales` as the dependent variable.

## Model Descriptions

### Model 1: Simple Regression (Footfall)
- **Equation:** monthly_sales = 446,410.58 + 35.6780 × footfall
- **Predictor:** footfall (monthly visitor count)
- **Logic:** More visitors should mean more sales opportunities

### Model 2: Simple Regression (Marketing Spend)
- **Equation:** monthly_sales = 560,777.35 + 2.1296 × marketing_spend
- **Predictor:** marketing_spend (monthly marketing budget)
- **Logic:** Higher marketing investment should attract more customers

### Model 3: Multiple Regression (Final Model)
- **Equation:** monthly_sales = 91,266.06 + 28.9428×footfall + 1.1626×marketing_spend + 2,636.17×staff_count + 3,100.12×inventory_availability_pct + 39,962.03×type_Airport + 17,557.64×type_HighStreet + 28,984.87×type_Mall
- **Predictors:** 4 numerical + 3 dummy variables
- **Logic:** Sales are influenced by multiple factors simultaneously

## Comparison Table

| Metric | Model 1 (Footfall) | Model 2 (Marketing) | Model 3 (Multiple) |
|--------|-------------------|---------------------|---------------------|
| **Type** | Simple Linear | Simple Linear | Multiple Linear |
| **Dependent Variable** | monthly_sales | monthly_sales | monthly_sales |
| **Independent Variables** | footfall | marketing_spend | footfall, marketing_spend, staff_count, inventory_availability_pct, type_Airport, type_HighStreet, type_Mall |
| **Number of Predictors** | 1 | 1 | 7 |
| **R-squared** | 0.7363 | 0.1672 | 0.8224 |
| **Adjusted R-squared** | 0.7355 | 0.1646 | 0.8184 |
| **Standard Error** | $53,373.74 | $94,846.03 | $44,223.53 |
| **F-statistic** | 887.85 | 63.86 | 206.35 |
| **Significance F** | <0.001 | <0.001 | <0.001 |
| **All Variables Significant?** | Yes (p<0.001) | Yes (p<0.001) | Yes (all p<0.05) |

## Business Usefulness Assessment

### Model 1 (Footfall Only)
- **Usefulness:** Good — footfall alone explains 73.6% of sales variation
- **Strength:** Simple, easy to understand, strong single predictor
- **Limitation:** Ignores other important factors; cannot guide marketing or staffing decisions

### Model 2 (Marketing Spend Only)
- **Usefulness:** Limited — explains only 16.7% of sales variation
- **Strength:** Confirms marketing has a positive relationship with sales
- **Limitation:** Very weak explanatory power; marketing alone is not enough to predict sales

### Model 3 (Multiple Regression)
- **Usefulness:** Best — explains 82.2% of sales variation with actionable insights
- **Strength:** Identifies multiple levers leadership can pull; lowest prediction error
- **Limitation:** More complex to interpret; does not prove causation

## Significant Variables (Model 3)

| Variable | P-value | Significant? | Direction |
|----------|---------|-------------|-----------|
| footfall | <0.001 | Yes | Positive (+$29 per visitor) |
| marketing_spend | <0.001 | Yes | Positive (+$1.16 per $1 spent) |
| staff_count | 0.0388 | Yes | Positive (+$2,636 per staff) |
| inventory_availability_pct | <0.001 | Yes | Positive (+$3,100 per 1%) |
| type_Airport | <0.001 | Yes | Positive (+$39,962 vs Residential) |
| type_HighStreet | 0.0042 | Yes | Positive (+$17,558 vs Residential) |
| type_Mall | <0.001 | Yes | Positive (+$28,985 vs Residential) |

## Limitations of All Models

1. **Association ≠ Causation** — regression identifies patterns, not cause-and-effect
2. **Omitted variables** — factors like local economy, weather, or competitor actions are not included
3. **Time period** — only 4 months of data; seasonal patterns may not be fully captured
4. **Linearity assumption** — relationships may not be perfectly linear in reality
5. **Residual patterns** — some stores are consistently over/under-predicted, suggesting missing factors

## Final Recommendation

**Model 3 (Multiple Regression) is selected as the final model** because it provides the highest explanatory power (R²=0.8224), the lowest prediction error, and actionable insights across multiple business levers.
