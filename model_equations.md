
# Model Equations

## Simple Regression Equations

### Model 1: Monthly Sales vs Footfall

```
monthly_sales = 446,410.58 + 35.6780 × footfall
```

**Coefficient Explanation:**
- **Intercept (446,410.58):** When footfall is zero (hypothetically no visitors), the baseline predicted sales would be $446,411. This is a mathematical anchor point — in reality, a store with zero visitors would have zero sales.
- **Footfall coefficient (35.6780):** For every one additional visitor to the store in a month, monthly sales increase by approximately $35.68 on average, holding nothing else constant.

**R-squared:** 0.7363 — Footfall alone explains 73.6% of the variation in monthly sales.

---

### Model 2: Monthly Sales vs Marketing Spend

```
monthly_sales = 560,777.35 + 2.1296 × marketing_spend
```

**Coefficient Explanation:**
- **Intercept (560,777.35):** When marketing spend is zero, the predicted baseline sales would be $560,777. This suggests stores generate substantial sales even without marketing (from walk-ins, repeat customers, etc.).
- **Marketing spend coefficient (2.1296):** For every additional $1 spent on marketing, monthly sales increase by approximately $2.13 on average.

**R-squared:** 0.1672 — Marketing spend alone explains only 16.7% of sales variation. It is statistically significant but a weak standalone predictor.

---

## Multiple Regression Equation (Final Model)

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

## Explanation of Each Coefficient

| Variable | Coefficient | Business Meaning |
|----------|-------------|-----------------|
| **Intercept** | 91,266.06 | Predicted sales for a Residential store in the East region with all numerical predictors at zero. This is a mathematical baseline. |
| **footfall** | +28.9428 | Each additional monthly visitor adds ~$29 to sales, holding other factors constant. This is the strongest numerical predictor. |
| **marketing_spend** | +1.1626 | Each additional $1 in marketing spend is associated with ~$1.16 increase in sales. The return is modest when other factors are controlled. |
| **staff_count** | +2,636.17 | Each additional staff member is associated with ~$2,636 more in monthly sales. More staff may improve customer service and conversion. |
| **inventory_availability_pct** | +3,100.12 | Each 1 percentage point increase in product availability adds ~$3,100 to sales. Keeping shelves stocked matters significantly. |
| **type_Airport** | +39,962.03 | Airport stores earn ~$39,962 MORE per month than Residential stores (reference), all else being equal. |
| **type_HighStreet** | +17,557.64 | High Street stores earn ~$17,558 MORE per month than Residential stores, all else being equal. |
| **type_Mall** | +28,984.87 | Mall stores earn ~$28,985 MORE per month than Residential stores, all else being equal. |

## Explanation of Dummy Variables

### What Are Dummy Variables?
Dummy variables convert categorical (text) data into numerical (0/1) format so regression can process them. Each category becomes a separate column with values of 1 (belongs to category) or 0 (does not belong).

### Region Dummies
- Original variable: `region` with 4 categories (East, North, South, West)
- Created 3 dummy variables: `region_North`, `region_South`, `region_West`
- **Reference category: East** — dropped to avoid multicollinearity

| Store Region | region_North | region_South | region_West |
|-------------|-------------|-------------|-------------|
| East | 0 | 0 | 0 |
| North | 1 | 0 | 0 |
| South | 0 | 1 | 0 |
| West | 0 | 0 | 1 |

### Store Type Dummies
- Original variable: `store_type` with 4 categories (Airport, High Street, Mall, Residential)
- Created 3 dummy variables: `type_Airport`, `type_HighStreet`, `type_Mall`
- **Reference category: Residential** — dropped to avoid multicollinearity

| Store Type | type_Airport | type_HighStreet | type_Mall |
|-----------|-------------|----------------|-----------|
| Residential | 0 | 0 | 0 |
| Airport | 1 | 0 | 0 |
| High Street | 0 | 1 | 0 |
| Mall | 0 | 0 | 1 |

### Why Drop One Category?
If we include ALL categories as dummies, they would perfectly predict each other (they always sum to 1). This creates **perfect multicollinearity** — the regression cannot solve. By dropping one category (the "reference"), we avoid this problem. The coefficients of the remaining dummies show the difference FROM the reference category.

### Why These Reference Categories?
- **East** was chosen as the region reference because it has the most observations (104 records), providing a stable baseline
- **Residential** was chosen as the store type reference because it is the most common format (100 records) and represents the "standard" store

## Final Model Selected

**Multiple Regression (Model 3)** is the final selected model.

### Reasons for Selection:
1. **Highest R-squared (0.8224)** — explains 82.2% of sales variation vs 73.6% (Model 1) and 16.7% (Model 2)
2. **Lowest standard error ($44,224)** — predictions are more accurate
3. **All variables significant** — every predictor contributes meaningfully (p < 0.05)
4. **Actionable insights** — identifies multiple levers (footfall, inventory, staffing, store type) that leadership can act on
5. **Includes categorical factors** — captures store type differences that simple models miss
