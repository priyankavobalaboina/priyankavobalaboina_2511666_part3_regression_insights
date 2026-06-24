# priyankavobalaboina_2511666_part3_regression_insights

# Part 3: Regression-Based Business Insights & Model Interpretation

## Business Problem Summary

A retail chain leadership team wants to understand what factors drive monthly sales performance across their stores. They are considering business actions such as increasing marketing spend, improving inventory availability, changing discounting strategy, reallocating staff, and prioritizing certain store types or regions. This analysis uses regression to identify which factors appear most strongly associated with monthly sales.

## Dataset Description

- **File:** `business_regression_data.xlsx`
- **Records:** 320 observations (80 stores × 4 months: Jan–Apr 2025)

| Column | Type | Description |
|--------|------|-------------|
| store_id | Categorical | Unique store identifier (STR-1001 to STR-1080) |
| month | Date | Reporting month (2025-01 to 2025-04) |
| region | Categorical | Business region (East, North, South, West) |
| store_type | Categorical | Store format (Mall, High Street, Residential, Airport) |
| marketing_spend | Numerical | Monthly marketing spend ($9,535 to $172,416) |
| footfall | Numerical | Monthly visitor count (971 to 12,870) |
| avg_discount_pct | Numerical | Average discount percentage (0% to 29.2%) |
| staff_count | Numerical | Number of store staff (5 to 31) |
| inventory_availability_pct | Numerical | Product availability percentage (71% to 99%) |
| competitor_distance_km | Numerical | Distance to nearest competitor (0.2 to 22.02 km) |
| holiday_flag | Binary | 1 if holiday effect present, 0 otherwise |
| customer_rating | Numerical | Average customer rating (2.8 to 5.0) |
| monthly_sales | Numerical (DV) | **Dependent variable** ($400,832 to $946,834) |
| monthly_profit | Numerical | Optional secondary metric |

## Dependent and Independent Variables

- **Dependent Variable (Y):** `monthly_sales`
- **Independent Variables (X):**
  - Numerical: `marketing_spend`, `footfall`, `avg_discount_pct`, `staff_count`, `inventory_availability_pct`, `competitor_distance_km`, `customer_rating`
  - Categorical (converted to dummies): `region`, `store_type`
  - Binary: `holiday_flag`
- **Not used in regression:** `store_id` (identifier), `month` (time label), `monthly_profit` (outcome, not predictor)

## Data Cleaning

- **Missing values found:**
  - `competitor_distance_km`: 6 missing → filled with median (3.37 km)
  - `customer_rating`: 8 missing → filled with median (3.90)
- **No outlier removal** was performed to preserve data integrity

## Regression Approach

Three regression models were built:

1. **Simple Regression Model 1:** monthly_sales vs footfall
2. **Simple Regression Model 2:** monthly_sales vs marketing_spend
3. **Multiple Regression Model (Final):** monthly_sales vs footfall + marketing_spend + staff_count + inventory_availability_pct + type_Airport + type_HighStreet + type_Mall

## Dummy Variable Approach

- **Region:** 4 categories → 3 dummy variables created (region_North, region_South, region_West)
  - Reference category: **East** (when all region dummies = 0)
- **Store Type:** 4 categories → 3 dummy variables created (type_Airport, type_HighStreet, type_Mall)
  - Reference category: **Residential** (when all type dummies = 0)
- One category is always dropped to avoid the dummy variable trap (perfect multicollinearity)

## Model Comparison Summary

| Metric | Model 1 (Footfall) | Model 2 (Marketing) | Model 3 (Multiple) |
|--------|-------------------|---------------------|---------------------|
| R-squared | 0.7363 | 0.1672 | 0.8224 |
| Adjusted R² | 0.7355 | 0.1646 | 0.8184 |
| Std Error | $53,374 | $94,846 | $44,224 |
| F-statistic | 887.85 | 63.86 | 206.35 |
| All vars significant? | Yes | Yes | Yes (all p<0.05) |

## Final Model Selected

**Model 3: Multiple Regression** was selected as the final model because:
- Highest R² (0.8224) — explains 82.2% of sales variation
- Lowest standard error ($44,224)
- All variables statistically significant at α = 0.05
- Includes both numerical and categorical predictors for richer business insights

## Business Recommendation

1. **Footfall is the strongest driver** — each additional visitor adds ~$29 to monthly sales
2. **Inventory availability matters significantly** — each 1% improvement adds ~$3,100 to sales
3. **Store type influences performance** — Airport stores outperform Residential by ~$40,000/month
4. **Marketing spend has a positive but modest effect** — $1 spent returns ~$1.16 in sales
5. **Staff count contributes** — each additional staff member adds ~$2,636 to sales

**Recommended actions:** Prioritize footfall-driving initiatives, maintain high inventory availability (>90%), and consider expanding Airport and Mall store formats.

## Assumptions and Limitations

- Regression shows **association, not causation** — we cannot prove that increasing footfall directly causes higher sales
- The model does not account for seasonality beyond the holiday_flag
- External factors (economic conditions, competitor promotions) are not captured
- The dataset covers only 4 months — longer time periods would strengthen conclusions
- Multicollinearity between predictors (e.g., footfall and staff_count) may exist

