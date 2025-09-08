# Housing Price Regression Analysis

## Overview

This repository contains Python notebooks for analyzing housing price data using both univariate and multivariate regression techniques. The analysis explores the relationship between housing prices and various property characteristics including size, location, number of rooms, and year of construction.

## Dataset

The analysis uses a housing dataset (`Housing.xlsx`) containing 20 observations with the following features:

- **House Price**: Target variable (dependent variable)
- **House Size (sq.ft.)**: Square footage of the house
- **State**: Location (IN, LA, NY, TX)
- **Number of Rooms**: Total number of rooms
- **Year of Construction**: Year the house was built

### Sample Data Overview
The dataset includes houses ranging from 860 to 2200 square feet, with prices between $570,000 and $1,250,000, built between 1987 and 2017 across four states.

## Analysis Files

### 1. Univariate Regression Analysis (`Housing Prices - unvariate REGRESSION.ipynb`)

This notebook performs simple linear regression using only house size as a predictor variable.

#### Key Results:
- **Model Equation**: `House Price = 260,806 + 401.92 × House Size (sq.ft.)`
- **R-squared**: 0.678 (67.8% of variance explained)
- **Adjusted R-squared**: 0.660
- **F-statistic**: 37.95 with p-value < 0.001 (highly significant)

#### Interpretation:
- For every additional square foot, house price increases by approximately $402
- The base price (intercept) is around $260,806
- The model explains about 68% of the variation in house prices
- The relationship is statistically significant (p < 0.001)
- Standard error of the slope coefficient is 65.24, indicating good precision

#### Coefficient Statistics:
- **Slope (β₁)**: 401.92 ± 65.24 (95% CI: 264.85 to 538.99)
- **Intercept (β₀)**: 260,806 ± 97,600 (95% CI: 55,800 to 466,000)

### 2. Multivariate Regression Analysis (`Housing Prices - multivariat REGRESSION.ipynb`)

This notebook extends the analysis to include multiple predictor variables.

#### Model Variables:
- House Size (sq.ft.)
- Number of Rooms
- Year of Construction

#### Key Results:
- **R-squared**: 0.736 (73.6% of variance explained)
- **Adjusted R-squared**: 0.687
- **F-statistic**: 14.90 with p-value < 0.001

#### Model Coefficients:
- **Intercept**: -9,452,000 (p = 0.099, not significant)
- **House Size**: 341.83 per sq.ft. (p = 0.075, marginally significant)
- **Number of Rooms**: 11,600 per room (p = 0.760, not significant)
- **Year of Construction**: 4,863.58 per year (p = 0.090, marginally significant)

#### Model Interpretation:
```
House Price = -9,452,000 + 341.83 × Size + 11,600 × Rooms + 4,863.58 × Year
```

#### Key Insights:

1. **Model Performance**: The multivariate model explains 73.6% of the variance, an improvement over the univariate model (67.8%).

2. **House Size Effect**: Each additional square foot increases price by ~$342 (compared to $402 in the simple model).

3. **Temporal Effect**: Houses built in more recent years command higher prices (~$4,864 per year).

4. **Room Count**: Additional rooms add value, but the effect is not statistically significant in this dataset.

5. **Statistical Concerns**: The model shows signs of multicollinearity (condition number = 5.40e+05), suggesting predictor variables are correlated.

## Model Diagnostics

### Univariate Model:
- **Durbin-Watson**: 1.810 (acceptable, no strong autocorrelation)
- **Normality**: Jarque-Bera test p-value = 0.699 (residuals appear normal)
- **Condition Number**: 5.66e+03 (moderate multicollinearity concern)

### Multivariate Model:
- **Durbin-Watson**: 1.938 (good, no autocorrelation)
- **Normality**: Jarque-Bera test p-value = 0.418 (residuals normal)
- **Condition Number**: 5.40e+05 (high multicollinearity warning)

## Dependencies

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import statsmodels.api as sm
from scipy import stats
```

## Usage

1. Ensure all dependencies are installed
2. Place `Housing.xlsx` in the appropriate directory
3. Run the notebooks in Jupyter environment
4. Update file paths as needed for your system

## Example Prediction

Using the univariate model to predict price for a 1,000 sq.ft. house:
```python
predicted_price = 260,800 + 402 * 1000 = $662,800
```

## Limitations and Recommendations

1. **Small Sample Size**: Only 20 observations limit the generalizability of results
2. **Multicollinearity**: High correlation between predictors in the multivariate model
3. **Geographic Variation**: State effects not properly modeled (could use dummy variables)
4. **Model Selection**: Consider feature selection techniques to address multicollinearity
5. **Validation**: Implement cross-validation for more robust performance estimates

## Future Enhancements

- Add state dummy variables for better geographic modeling
- Implement regularization techniques (Ridge/Lasso) to handle multicollinearity
- Collect more data for improved statistical power
- Add polynomial features or interaction terms
- Perform residual analysis for model validation

## License

MIT License - see LICENSE file for details.

## Author

OUTGOUGUA MUSTAPHA

---

*This analysis demonstrates fundamental regression techniques for real estate price prediction, suitable for educational purposes and as a foundation for more complex modeling approaches.*