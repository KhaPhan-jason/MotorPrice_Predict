# Motorbike Price Prediction

This project performs **exploratory data analysis (EDA)** and **predictive modeling** to estimate the resale price of motorbikes. The analysis identifies key factors affecting selling price and builds a linear regression model to predict bike prices.

---

## Dataset

- **File:** `BIKE DETAILS.csv`
- **Key Columns:**  
  `name`, `km_driven`, `year`, `ex_showroom_price`, `selling_price`, `owner`, `seller_type`
- **Preprocessing:**  
  - Removed duplicates and rows with missing `ex_showroom_price`  
  - Created `Age` as `2025 - year`  
  - Dropped the `year` column  
  - Applied log transformation to numeric features for normalization  
  - Encoded categorical variables (`seller_type`, `owner`) using LabelEncoder  

---

## Libraries

- `numpy`
- `pandas`
- `matplotlib`
- `seaborn`
- `scikit-learn`
- `scipy`

---

## Exploratory Data Analysis (EDA)

1. **Overview**  
   - Checked dataset shape, data types, missing values, and duplicates  

2. **Categorical Features**  
   - `seller_type` and `owner` analyzed using countplots and ANOVA  
   - Both variables significantly influence resale price  

3. **Numeric Features**  
   - `km_driven`, `ex_showroom_price`, `Age`, and `selling_price` analyzed using histograms and boxplots  
   - Log transformations applied to reduce skewness and stabilize variance  

4. **Correlation Analysis**  
   - Strongest correlations with `selling_price`:  
     - `ex_showroom_price`  
     - `km_driven`  
     - `Age`  

5. **Visual Insights**  
   - First-owner bikes tend to have higher resale value  
   - Individual sellers often list higher prices than dealers  
   - Scatterplots show approximate linear relationships between log-transformed numeric features and selling price  

---

## Predictive Modeling

- **Model:** Linear Regression  
- **Features:** `km_driven_log`, `Age`, `owner`, `seller_type`, `ex_showroom_price_log`  
- **Target:** `selling_price_log`  
- **Preprocessing:** RobustScaler applied to features  
- **Train/Test Split:** 80% training, 20% testing  

### Model Performance

- **Full R² (all data):** [model.score(X, y)]  
- **Train R²:** [model.score(X_train, y_train)]  
- **Test R²:** [model.score(X_test, y_test)]  
- Coefficients indicate the contribution of each feature to predicted selling price  

---

## Insights

- **Key Price Drivers:**  
  - Higher `ex_showroom_price` increases resale value  
  - Older bikes (`Age`) and higher `km_driven` decrease selling price  
  - Ownership history and seller type also affect pricing  

- **Distribution Patterns:**  
  - Selling price is skewed; log transformation improves model performance  
  - Most bikes are sold by dealers; individual sellers often price slightly higher  
  - First-owner bikes generally retain higher resale value  

- **Model Insights:**  
  - Linear regression performs well with log-transformed and scaled features  
  - Features explain most variance in resale price  

- **Overall:**  
  The project demonstrates that motorbike resale prices can be accurately predicted using age, mileage, ownership history, seller type, and original showroom price. Proper preprocessing, feature engineering, and log transformations improve predictive accuracy.
