# Assignment 04 Interpretation Memo

**Student Name:** Sienna Lopez
**Date:** February 11, 2026
**Assignment:** REIT Annual Returns and Predictors (Simple Linear Regression)

---

## 1. Regression Overview

You estimated **three** simple OLS regressions of REIT *annual* returns on different predictors:

| Model | Y Variable | X Variable | Interpretation Focus |
|-------|------------|------------|----------------------|
| 1 | ret (annual) | div12m_me | Dividend yield |
| 2 | ret (annual) | prime_rate | Interest rate sensitivity |
| 3 | ret (annual) | ffo_at_reit | FFO to assets (fundamental performance) |

For each model, summarize the key results in the sections below.

---

## 2. Coefficient Comparison (All Three Regressions)

**Model 1: ret ~ div12m_me**
- Intercept (β₀): 0.1082 (SE: 0.0060, p-value: <0.0001)
- Slope (β₁): -0.0687 (SE: 0.0325, p-value: 0.0346)
- R²: 0.0018 | N: 2527

**Model 2: ret ~ prime_rate**
- Intercept (β₀): 0.2127 (SE: 0.0170, p-value: <0.0001)
- Slope (β₁): -0.0225 (SE: 0.0033, p-value: <0.0001)
- R²: 0.0176 | N: 2527

**Model 3: ret ~ ffo_at_reit**
- Intercept (β₀): 0.0973 (SE: 0.0092, p-value: <0.0001)
- Slope (β₁): 0.5770 (SE: 0.5675, p-value: 0.3093)
- R²: 0.0004 | N: 2518

*Note: Model 3 has fewer observations (2518 vs 2527) because ffo_at_reit has missing values; statsmodels drops those rows.*

---

## 3. Slope Interpretation (Economic Units)

**Dividend Yield (div12m_me):**
- A 1 percentage point increase in dividend yield (12-month dividends / market equity) is associated with a -6.87 percentage point change in annual return.
- This negative relationship is somewhat counterintuitive but could reflect the "dividend puzzle" in finance: high-dividend REITs may be in slower-growth periods or facing market challenges that cap their total return potential. Alternatively, the market may price in lower future capital appreciation for high-yield stocks, such that total return (price appreciation + dividend) is not necessarily higher.

**Prime Loan Rate (prime_rate):**
- A 1 percentage point increase in the year-end prime rate is associated with a -2.25 percentage point change in annual return.
- This negative relationship is economically intuitive: REITs are interest-rate sensitive. When the prime rate rises, borrowing costs increase, and the discount rate applied to REIT cash flows rises, depressing valuations and returns. REITs are often debt-financed, so higher rates directly reduce profitability and investor returns.

**FFO to Assets (ffo_at_reit):**
- A 1 unit increase in FFO/Assets (fundamental performance) is associated with a 0.5770 change in annual return.
- Although the slope is positive (suggesting higher operational efficiency correlates with better returns), the effect is not statistically significant and has a wide standard error. This suggests that FFO/Assets alone is a weak predictor of annual returns in our sample, perhaps because market sentiment, leverage, and capital structure also play major roles.

---

## 4. Statistical Significance

For each slope, at the 5% significance level:
- **div12m_me:** Significant — The slope of -0.0687 has a p-value of 0.0346, which is less than 0.05, so we reject the null hypothesis. Higher dividend yield is statistically significantly associated with lower annual returns.
- **prime_rate:** Significant — The slope of -0.0225 has a p-value < 0.0001, providing very strong evidence that the prime rate is a significant predictor of REIT annual returns. Higher interest rates are associated with significantly lower returns.
- **ffo_at_reit:** Not significant — The slope of 0.5770 has a p-value of 0.3093, which exceeds 0.05. We cannot reject the null hypothesis that FFO/Assets has no effect on returns.

**Which predictor has the strongest statistical evidence of a relationship with annual returns?** Prime rate has the strongest statistical evidence (p-value < 0.0001 and largest R²), followed by dividend yield (p-value = 0.0346). FFO/Assets shows no significant relationship.

---

## 5. Model Fit (R-squared)

Compare R² across the three models:
- Prime rate model: R² = 0.0176 (explains 1.76% of variation)
- Dividend yield model: R² = 0.0018 (explains 0.18% of variation)
- FFO to assets model: R² = 0.0004 (explains 0.04% of variation)

The prime rate predictor explains the most variation in annual returns, though even it accounts for less than 2% of the total variation. Overall, all three R² values are quite low, suggesting that annual REIT returns are driven primarily by factors not captured in these simple bivariate regressions—such as market sentiment, leverage, sector performance, and macroeconomic conditions beyond just the prime rate, dividend policy, or operational efficiency ratios. This highlights the complexity of predicting asset returns with single predictors.

---

## 6. Omitted Variables

By using only one predictor at a time, we might be omitting:
- **Market sentiment / Valuation (price-to-book ratio):** Investor sentiment and market valuations have strong effects on short-term returns. If high-dividend REITs trade at lower valuations (and thus offer higher future returns), omitting valuation could bias the dividend coefficient.
- **Leverage / Capital structure:** REITs with higher leverage may have different risk-return profiles. If leverage is correlated with dividend yield or prime-rate sensitivity, omitting it could distort slope estimates.
- **Sector / Property type exposure:** Some REIT sectors (e.g., residential, industrial, office) perform very differently. If certain sectors have different average dividend yields or FFO ratios, sector effects could confound our results.

**Potential bias:** The negative dividend coefficient might reflect omitted-variable bias: high-dividend REITs might be mature, low-growth properties, and if we omit growth expectations or sector growth trends, we may overstate (in magnitude) the negative effect of dividend yield. Similarly, if leverage is higher for REITs with higher dividend yields and leverage amplifies returns, the true partial effect of dividend yield (holding leverage constant) could be less negative than our simple regression suggests.

---

## 7. Summary and Next Steps

**Key Takeaway:**
The prime loan rate emerges as the strongest single predictor of REIT annual returns, with a statistically significant negative relationship (p < 0.0001): higher interest rates are associated with lower returns, consistent with the interest-rate sensitivity of debt-financed real estate. Dividend yield also shows a significant negative relationship, possibly reflecting the maturity and slower growth of high-dividend REITs. FFO to assets, by contrast, shows no significant predictive power in simple regression, suggesting that operational efficiency alone—without considering valuation, leverage, and market conditions—is insufficient to forecast returns. The low R² values across all models underscore that many other factors beyond these three variables drive REIT returns, motivating a move to multiple regression and broader economic indicators.

**What we would do next:**
- Extend to multiple regression (include two or more predictors simultaneously) to isolate partial effects and reduce omitted-variable bias.
- Test for heteroskedasticity using Breusch-Pagan or White tests; if rejected, use robust standard errors.
- Examine whether relationships vary by time period (e.g., before/after 2008 financial crisis) or REIT sector (residential, industrial, office, healthcare).
- Include lagged returns or volatility measures to capture momentum and risk-return trade-offs.
- Consider nonlinear relationships (e.g., log-returns, interactions) if economic theory suggests they matter.

---

## Reproducibility Checklist
- [ ] Script runs end-to-end without errors
- [ ] Regression output saved to `Results/regression_div12m_me.txt`, `regression_prime_rate.txt`, `regression_ffo_at_reit.txt`
- [ ] Scatter plots saved to `Results/scatter_div12m_me.png`, `scatter_prime_rate.png`, `scatter_ffo_at_reit.png`
- [ ] Report accurately reflects regression results
- [ ] All interpretations are in economic units (not just statistical jargon)
