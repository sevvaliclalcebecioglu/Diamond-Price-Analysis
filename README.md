# Diamond Price Prediction using Python

## Project Summary
The aim of this project is to **analyze and predict the price of diamonds** based on their features using Python and multiple regression models, including ensemble and tree-based methods.

The dataset contains the following attributes:

| Column | Description |
|--------|-------------|
| carat  | Weight of the diamond |
| cut    | Quality of the cut (Ideal, Premium, Good, Very Good, Fair) |
| color  | Diamond color from D (best) to J (worst) |
| clarity | Diamond clarity (IF, VVS1, VVS2, VS1, VS2, SI1, SI2, I1) |
| depth  | Total depth percentage = z / mean(x, y) = 2 * z / (x + y) |
| table  | Width of top of diamond relative to widest point |
| price  | Price in US dollars |
| x      | Length in mm |
| y      | Width in mm |
| z      | Depth in mm |

---

## Data Preprocessing
- Dropped `Unnamed: 0` column as irrelevant.
- Checked for missing values → no missing values found.
- Encoded categorical variables (`cut`, `color`, `clarity`) using one-hot encoding.
- Removed outliers above the 97th percentile for all numerical columns.
- Scaled numerical features to 0-1 range using MinMaxScaler.
- Split data into training (80%) and test (20%) sets.

---

## Models Tested
We tested **12 regression models**, including:

- Linear Regression, Ridge, Lasso, ElasticNet, SGDRegressor  
- Decision Tree, Extra Tree, Gradient Boosting, AdaBoost, XGBRegressor  
- KNeighborsRegressor  

> Heavy models like SVR and MLPRegressor were excluded to speed up computation.

---

## Model Performance

| Model | R² | RMSE | MAE |
|-------|-----|-----|-----|
| XGBRegressor | 0.9808 | 433.63 | 239.27 |
| AdaBoost | 0.9711 | 531.64 | 288.08 |
| Extra Tree | 0.9676 | 563.42 | 293.40 |
| Decision Tree | 0.9668 | 570.29 | 293.80 |
| Gradient Boosting | 0.9561 | 655.54 | 346.03 |
| Ridge | 0.9196 | 887.31 | 603.72 |
| Linear | 0.9195 | 887.57 | 602.38 |
| SGD | 0.9189 | 891.24 | 618.72 |
| Lasso | 0.9188 | 891.56 | 609.18 |
| KNeighborsRegressor | 0.8496 | 1213.46 | 913.47 |
| ElasticNet | 0.2413 | 2725.29 | 2106.26 |

> **Best Model:** XGBRegressor with R² = 0.9808, RMSE = 433.63, MAE = 239.27

---

## Deep Learning Model Performance

- R²: 0.9791  
- MSE: 452.08  

> The deep learning model performed comparably to XGBRegressor, demonstrating that tree-based ensembles and neural networks are both suitable for this regression task.

---

## Conclusion
- **XGBRegressor** provided the best prediction performance for diamond prices.  
- **Ensemble and tree-based methods** outperform simple linear models.  
- Outlier removal and feature scaling significantly improved model performance.
