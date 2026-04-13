# ML CO₂ Emissions
EDA and building Multiple Linear Regression model to predict CO₂ Emissions from historical dataset


# CO₂ Emissions EDA & Regression Analysis
 
Exploratory Data Analysis and building Multiple Linear Regression model to predict CO₂ Emissions.
 
Completed as part of MIS710 Machine Learning in Business at Deakin University.
 
## Business Problem
 
There is no accurate and reliable method to estimate CO₂ emissions for individual vehicles. This project uses historical vehicle data to build a predictive model that supports environmental regulation, consumer awareness, and manufacturer accountability.
 
## Dataset
 
- **Source:** AESC CO₂ emissions dataset
- **Records:** 6,685 rows, 11 columns
- **Target variable:** CO₂ Emissions (g/km)
- **Key features:** Cylinders, Engine Size, Vehicle Category, Fuel Type, Transmission Type, Dealer State
 
## Tools & Libraries
 
- Python, Google Colab
- pandas, NumPy
- matplotlib, seaborn
- scikit-learn (LinearRegression, train_test_split, r2_score, mean_absolute_error)
 
## What I Did
 
### Data Cleaning & Preparation
- Handled missing values using median to fill (Cylinders, Engine Size) and mode to fill (Transmission Type)
- Detected outliers using IQR method across numerical variables
- Removed 69 records with "Unknown" Dealer State (1.03% of data)
- Grouped high-cardinality categorical variables to reduce complexity: Vehicle Category (30+ subcategories → 10 groups), Fuel Type (5 codes → 5 descriptive groups), Transmission Type (12 subtypes → Auto/Manual)     
- Applied one-hot encoding (dummy coding) for categorical features
 
### Exploratory Data Analysis
- Univariate analysis: distributions, descriptive statistics, box plots for each variable
- Bivariate analysis: relationships between CO₂ emissions and Transmission, Dealer State, Vehicle Group, Fuel Group
- Multivariate analysis: CO₂ emissions by Vehicle Group × Transmission Group
- Correlation analysis: identified Cylinders (r = 0.79) and Engine Size (r = 0.77) as strongest predictors ; however, they exhibit strong collinearity with each other (r = 0.82)
### Model Development (Iterative)    ==========   幫我加上adjust R² 欄位
| Model | Features | R² | Adjusted R²| 
|-------|----------|-----|----------|
| Simple Linear Regression | Cylinders | 0.62 | 0.62 |
| Multi Regression v1 | Cylinders + Vehicle Group | 0.71 | 0.71 |
| Multi Regression v2 | Cylinders + Engine Size | 0.67 | 0.67 |
| Multi Regression v3 | Cylinders + Vehicle Group + Fuel Group | 0.73 | 0.73 |
| **Final Model** | **Cylinders + Engine Size + Vehicle Group + Fuel Group** | **0.75** | **0.75** |  
 
### Model Evaluation
- Residual analysis: residuals vs predicted, residuals vs predictor
- Normality check: histogram and Q-Q plot of residuals
- Feature importance visualisation via regression coefficients
- MAE: 26 g/km, RMSE: 37 g/km (simple model baseline)
 
## Conclusion and Key Takeaway
 
The final multiple linear regression model explains 75% of the variance in vehicle CO₂ emissions. Cylinders and Engine Size are the strongest numerical predictors, while Vehicle Group and Fuel Type provide additional categorical context that improves prediction accuracy. As the primary goal of this project is to predict CO₂ emissions, we selected the model with the highest Adjusted R² (0.75). Alternatively, Multi Regression v3 (Adjusted R² 0.73) offers a simpler option with easier interpretability, as it excludes Engine Size and avoids the collinearity issue between Cylinders and Engine Size.

