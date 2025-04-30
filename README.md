# Housing Price Prediction Using Linear Regression

## Overview

This project focuses on developing a robust linear regression model to analyze and predict residential housing prices based on a variety of property and neighborhood features. Using a cleaned dataset of 7,000 records, the objective was to identify the most influential factors that drive housing prices and to build a model that can inform decisions for real estate developers, investors, and potential homebuyers.

---

## Project Objectives

- **Primary Goal**: To determine which property and neighborhood features have the most significant impact on house prices.
- **Use Case**: Help real estate professionals make data-informed decisions about home development, marketing, and investments.
- **Methodology**: Perform a complete statistical data mining workflow including data preparation, linear regression modeling, and model optimization.

---

## Research Question

How do property features (e.g., square footage, number of bedrooms and bathrooms, backyard space) and neighborhood factors (e.g., crime rate, school rating, distance to city center) influence house prices?

---

## Dataset Summary

The dataset includes 7,000 observations and 22 features, both categorical and numerical, including:

- `SquareFootage`, `NumBedrooms`, `NumBathrooms`, `BackyardSpace`
- `CrimeRate`, `SchoolRating`, `DistanceToCityCenter`
- Target variable: `Price`

### Key Statistics

| Metric               | Value       |
|----------------------|-------------|
| Average Price        | $307,282    |
| Max Price            | $1,046,676  |
| Min Price            | $85,000     |
| Avg Square Footage   | 1,048 ft²   |
| Most Common Bedrooms | 3           |
| Most Common Price    | $85,000     |

---

## Data Exploration and Preparation

### Univariate Insights

- Most houses have **3 bedrooms** and **1–2 bathrooms**.
![image](https://github.com/user-attachments/assets/ed5b7cc2-60d2-4339-a86c-495f5e799210)
![image](https://github.com/user-attachments/assets/d0281427-228c-4586-b476-18f6ca8faee9)
- A **right-skewed distribution** was observed in price, square footage, and bathroom count.
- Majority of properties are clustered within **20 miles of the city center**.

### Bivariate Insights

- **SquareFootage** and **NumBathrooms** showed strong positive correlation with price.
![image](https://github.com/user-attachments/assets/c9072cb6-11d0-4d6f-a71a-c4b61fea1015)
- **DistanceToCityCenter** had a strong negative correlation.
![image](https://github.com/user-attachments/assets/75ae9f04-d7cd-474c-bb1f-230b6372497e)
- **BackyardSpace** showed a mild negative relationship, suggesting diminishing returns on large yards.
![image](https://github.com/user-attachments/assets/fe0c1aa1-61e8-4625-b899-e4ce4fa1e9f6)

### Preprocessing

- Converted categorical variables to numeric (one-hot encoding where applicable).
- Verified multicollinearity using VIF.
- Split the dataset into **training (70%)** and **testing (30%)** sets.

---

## Modeling Approach

- **Initial Model**: Included 7 predictors.
- **Optimization Strategy**: Backward Stepwise Selection based on p-values and VIF scores.
- **Final Model Variables**:
  - `SquareFootage`, `NumBedrooms`, `NumBathrooms`, `BackyardSpace`, `DistanceToCityCenter`

### Final Regression Equation

```
Price = 130.13 * SquareFootage
      + 42,185.27 * NumBedrooms
      + 45,890.50 * NumBathrooms
      - 37.60 * BackyardSpace
      - 1,635.42 * DistanceToCityCenter
```
- Distribution of **Price**
![image](https://github.com/user-attachments/assets/cd3e3663-d8d4-4c8a-8c0c-7496e2828172)

---

## Model Evaluation

### Performance Metrics

| Metric                  | Before Optimization | After Optimization |
|-------------------------|---------------------|--------------------|
| R²                      | 0.594               | 0.916              |
| Adjusted R²             | 0.593               | 0.915              |
| Training MSE            | —                   | 9,966,706,428.76   |
| Test MSE                | —                   | 9,825,425,331.64   |
| Test RMSE               | —                   | 99,123.28          |
| RMSE as % Avg Price     | —                   | 32.58%             |

### Interpretation

- The model explains **91.6%** of the variance in house prices after optimization.
- Low MSE values between training and test sets indicate **strong generalization**.
- Key features like **SquareFootage**, **NumBathrooms**, and **DistanceToCityCenter** were most predictive.

---

## Assumption Verification

- **Linearity**: Scatterplots showed clear linear trends.
- **Normality**: Q-Q plots suggested approximate normality.
- **Homoscedasticity**: Slight heteroscedasticity observed, but not severe.
- **Multicollinearity**: Handled by removing high VIF variables (`CrimeRate`, `SchoolRating`).

---

## Key Insights

### For Developers:
- Prioritize **square footage** and **bathroom count**.
- Invest in **urban-proximate locations** for higher returns.
- **Limit backyard size** beyond moderate levels to control costs.

### For Buyers:
- Focus on homes near city centers with adequate **indoor space**.
- Don’t overpay for homes with oversized backyards if other factors are lacking.

### For Investors:
- Use the regression model to prioritize investments with strong price drivers.
- Avoid properties with high costs but low-value return features.

---

## Tools and Technologies

- **Pandas, NumPy** – Data manipulation and numeric processing
- **Matplotlib, Seaborn** – Data visualization
- **Statsmodels** – Linear regression modeling and summary statistics
- **Scikit-learn** – Data splitting, error metrics (MSE, RMSE)
- **SciPy** – Residual analysis

---

---

## Final Thoughts

This project showcases how statistical data mining can be used to uncover actionable insights from real-world datasets. The housing market, influenced by both tangible features (like square footage) and contextual factors (like location), offers a rich domain for predictive modeling.

By leveraging rigorous EDA, optimized modeling, and validation strategies, this project not only demonstrates strong predictive accuracy but also yields meaningful recommendations for various stakeholders in the housing ecosystem.

---

## Conclusion

This project successfully built and optimized a linear regression model to predict housing prices with high accuracy and interpretability. It identifies actionable patterns in the housing market and offers data-backed strategies for real estate professionals and investors. The model balances complexity and precision, serving as a valuable tool for real-world decision-making.



---

## Extended Exploratory Data Analysis (EDA)

Understanding the dataset was a critical early step. The distribution and relationships between variables were explored using both statistical summaries and visual techniques.

### Detailed Descriptive Statistics

- **Price**: The wide range (from $85,000 to over $1M) highlights a dataset with substantial variability, ideal for regression modeling.
- **SquareFootage**: While some homes had over 2,800 ft² of space, many were clustered near the 550–1,000 ft² mark, indicating a market with a heavy mix of compact residences.
- **BackyardSpace**: Exhibits a long-tailed distribution. Larger backyards appear rare and might represent luxury or rural homes.
- **CrimeRate** and **SchoolRating**: These socio-environmental features introduce neighborhood quality indicators that can dramatically affect buyer perceptions and property valuations.
- **DistanceToCityCenter**: Properties closer to urban centers generally fetched higher prices, reinforcing classic real estate value dynamics.

### Univariate and Bivariate Visualizations

- **Histograms** and **box plots** were used to examine the spread, skewness, and presence of outliers.
- **Scatterplots** helped assess linearity with respect to `Price`, supporting the validity of using a linear model.
- **Heatmaps** of correlation matrices were used to identify initial multicollinearity concerns.

---

## Feature Selection and Optimization Process

The initial model included seven predictors. Through **backward stepwise elimination**, features with statistically insignificant contributions (p > 0.05) were removed.

### Step-by-Step Optimization

1. Started with all seven predictors: SquareFootage, NumBedrooms, NumBathrooms, BackyardSpace, CrimeRate, SchoolRating, DistanceToCityCenter.
2. Dropped `CrimeRate` due to high p-value (0.23).
3. Dropped `SchoolRating` with p-value ≈ 0.063, near but above the 0.05 threshold.
4. Verified and removed multicollinearity by computing **VIF scores** (threshold > 10).
5. Removed constant term to support uncentered model for statistical performance.

This resulted in a **simpler, high-performing model** without overfitting.

---

## Business Implications in Depth

The model’s outputs inform real-world strategies for multiple stakeholders:

### For Urban Planners and Policy Makers

- Incentivizing development near city centers may yield higher tax revenues and attract more residential investment.
- Schools already hold strong value correlation—continued funding for educational excellence in suburban zones may influence price parity.

### For Real Estate Startups and Marketplaces

- Incorporate distance to the city and house size prominently in pricing algorithms.
- Use model predictions to suggest fair market value ranges to buyers and sellers.

### For First-Time Homebuyers

- Leverage insights on square footage and bedroom count to prioritize essential features during the decision-making process.
- Consider trade-offs between backyard size and property value, especially if other key needs are already met.

---

## Limitations and Future Directions

Despite its strengths, the model assumes linearity and is limited to variables provided in the dataset. Areas for enhancement include:

- Introducing **interaction terms** between variables like bedrooms × bathrooms.
- Exploring **non-linear models** such as polynomial regression or random forests.
- Integrating **external data** such as interest rates, employment trends, or commute times to better contextualize housing value.

Additionally, incorporating **temporal dynamics** like seasonality in sales could yield richer insights for future iterations.

---

## Sample of the Dataset

Below is a preview of a few records from the dataset used in this project:

| ID   | Price       | SquareFootage | NumBathrooms | NumBedrooms | BackyardSpace | CrimeRate | SchoolRating | AgeOfHome | DistanceToCityCenter | EmploymentRate | PropertyTaxRate | RenovationQuality | LocalAmenities | TransportAccess | Fireplace | HouseColor | Garage | Floors | Windows | PreviousSalePrice | IsLuxury |
|------|-------------|----------------|---------------|--------------|----------------|------------|----------------|------------|------------------------|----------------|------------------|--------------------|-----------------|------------------|-----------|-------------|--------|--------|----------|--------------------|----------|
| 4922 | 255614.90   | 566.62         | 1.0           | 4            | 779.42         | 20.56      | 5.62           | 39.46      | 10.08                  | 97.29          | 1.84             | 4.93               | 4.44            | 4.55             | Yes       | Blue        | No     | 1      | 13       | 181861.54           | 0        |
| 5009 | 155586.09   | 1472.34        | 1.0           | 2            | 656.13         | 15.62      | 5.63           | 40.51      | 7.89                   | 93.22          | 0.95             | 4.08               | 5.56            | 6.83             | No        | Green       | No     | 1      | 17       | 50042.60            | 0        |
| 4450 | 131050.83   | 550.00         | 1.78          | 3            | 754.57         | 12.47      | 9.20           | 48.38      | 23.74                  | 96.60          | 1.87             | 4.26               | 8.07            | 8.48             | Yes       | Green       | Yes    | 2      | 34       | 48400.34            | 0        |
| 1070 | 151361.71   | 941.81         | 2.04          | 2            | 439.59         | 22.22      | 7.08           | 94.67      | 5.22                   | 91.45          | 1.45             | 4.45               | 5.00            | 6.27             | Yes       | Red         | No     | 1      | 14       | 84594.12            | 0        |
| 400  | 113167.61   | 550.00         | 1.06          | 3            | 353.03         | 8.28       | 5.93           | 16.80      | 43.13                  | 86.50          | 1.26             | 3.36               | 5.46            | 6.99             | No        | White       | Yes    | 1      | 21       | 22934.60            | 0        |
| 5979 | 224973.41   | 1474.99        | 1.86          | 2            | 774.45         | 25.39      | 4.92           | 57.62      | 19.71                  | 94.71          | 1.49             | 6.15               | 0.98            | 1.90             | No        | White       | Yes    | 2      | 36       | 160664.13           | 0        |
| 3703 | 169471.52   | 1069.49        | 1.23          | 3            | 757.58         | 37.84      | 4.40           | 46.86      | 5.73                   | 80.90          | 1.57             | 5.82               | 4.25            | 5.12             | No        | White       | No     | 1      | 10       | 89824.61            | 0        |
| 2260 | 265497.89   | 550.00         | 1.0           | 1            | 636.64         | 48.26      | 4.32           | 60.29      | 11.35                  | 94.18          | 0.72             | 5.81               | 5.43            | 6.03             | No        | Yellow      | Yes    | 1      | 15       | 177283.20           | 0        |

This subset highlights the diversity in housing characteristics and pricing used for training and testing the model.

---
