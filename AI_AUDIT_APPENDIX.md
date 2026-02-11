# AI Audit Appendix (Assignment 04)

## Tool(s) Used
- GitHub Copilot (Claude Haiku 4.5)

## Task(s) Where AI Was Used
1. Completing the `estimate_regression()` function to fit OLS regressions using statsmodels
2. Implementing `save_regression_summary()` to write regression output to text files
3. Implementing `plot_scatter_with_regression()` to create scatter plots with fitted regression lines, including R² values and axis zooming
4. Implementing `print_key_results()` to extract and display regression coefficients, standard errors, t-statistics, p-values, and R² values
5. Generating interpretation text for the assignment memo sections (slopes, significance, model fit, omitted variables, summary)

## Prompt(s)
Key prompts included:
- "Complete the estimate_regression function: estimate ret ~ x_var using statsmodels.formula.api.ols"
- "Implement save_regression_summary to write model.summary() to a text file"
- "Create a scatter plot with regression line, filtering data, computing the fitted line, zooming to central percentiles, and adding R² to title"
- "Extract and print regression coefficients with standard errors, t-stats, p-values, R², and significance test results"
- "Provide economic interpretation of regression slopes for dividend yield, prime rate, and FFO to assets"

## Output Summary
The AI provided:
- Working Python code for OLS regression estimation, model saving, and visualization
- Correct use of statsmodels formula API and numpy/matplotlib functions
- Calculations of fitted values and axis limits for readable scatter plots
- Extraction of model parameters (intercept, slope, standard errors, p-values, R²)
- Coherent economic interpretations based on regression results

## Verification & Modifications (Disclose • Verify • Critique)

**Verify:**
- Ran `assignment04_regression.py` successfully; script executed without errors and produced all required output files (3 regression summaries, 3 scatter plots)
- Spot-checked regression table outputs against console print statements to confirm coefficients, standard errors, and p-values matched
- Verified scatter plots appear visually correct with data points, fitted lines, and R² values displayed
- Confirmed all Results/ files (regression_*.txt and scatter_*.png) were created correctly

**Critique:**
- The AI code was accurate and required no substantial corrections
- The economic interpretations provided in the memo were reasonable and reflect standard finance theory (interest-rate sensitivity of REITs, dividend-growth tradeoff, operational efficiency limitations)
- All regression estimates match the console output, indicating correct implementation

**Modify:**
- Fine-tuned interpretation text to add specific details about each result (e.g., quantifying the magnitude of interest-rate sensitivity and its practical significance)
- Adjusted omitted-variables discussion to reflect the actual dataset structure and limitations of our sample
- Ensured memo text flows logically from coefficient comparison → interpretation → significance → model fit → bias concerns → conclusions
