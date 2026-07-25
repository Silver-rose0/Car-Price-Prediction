# 🚗 Car Price Prediction Model

A machine learning regression project that predicts car selling prices based on various car attributes and market conditions.

## 📋 Project Overview

**Objective:** Build a predictive model to estimate car selling prices based on features like year, mileage, fuel type, transmission, and seller type. This helps buyers and dealers understand fair market pricing.

**Problem Type:** Regression (Continuous Value Prediction)  
**Target Variable:** Selling_Price ($)

## 📊 Dataset

- **Source:** cardata.csv
- **Total Samples:** 301 car records
- **Features:** 8 original attributes + 1 engineered (Car_Age)
- **Target:** Selling_Price (in lakhs)
- **Train/Test Split:** 80% training (240 samples) / 20% testing (61 samples)
- **Price Range:** ₹1 lakh to ₹35 lakhs (₹10,000 to ₹3.5 million)

### Key Features:

| Feature | Description |
|---------|-------------|
| Car_Name | Name/model of the car |
| Year | Year of manufacture |
| Present_Price | Current market price (in lakhs) |
| Kms_Driven | Total kilometers driven |
| Fuel_Type | Type of fuel (Petrol/Diesel/CNG) |
| Seller_Type | Type of seller (Dealer/Individual) |
| Transmission | Type of transmission (Manual/Automatic) |
| Owner | Number of previous owners |
| **Selling_Price** | **Target: Selling price (in lakhs)** |

## 🔧 Methodology

### 1. **Data Exploration & Analysis**
   - Exploratory Data Analysis (EDA)
   - Data distribution analysis
   - Correlation analysis
   - Missing value handling
   - Statistical summaries

### 2. **Data Preprocessing**
   - Handling categorical variables (Fuel Type, Transmission, Seller Type)
   - Encoding categorical features (LabelEncoder)
   - Feature scaling/normalization (StandardScaler)
   - Outlier detection and treatment
   - Train-test split (80-20)

### 3. **Feature Engineering**
   - **Car_Age Feature:** Created from Year (calculates age relative to latest model year)
   - **Categorical Encoding:** LabelEncoder for Fuel Type, Transmission, Seller Type
   - **Feature Scaling:** StandardScaler normalization (mean=0, std=1)
   - **Polynomial Features:** Degree 2 for capturing non-linear price relationships
   - **Feature Selection:** Identified top 5 predictive features through coefficient analysis

### 4. **Model Development**
   Two regression approaches were tested and compared:
   
   - **Linear Regression:** Simple baseline model (R² = 0.8466)
   - **Polynomial Regression (Degree 2):** Captures non-linear price relationships (R² = 0.9750) ⭐ **BEST**
   - Tested polynomial degrees 1, 2, and 3 to find optimal complexity

### 5. **Model Evaluation**
   - **R² Score:** Measures how well the model explains variance in prices
   - **RMSE (Root Mean Squared Error):** Average prediction error in price units
   - **Mean Absolute Error:** Average absolute difference from actual prices
   - **Cross-Validation:** K-fold validation for robust evaluation
   - **Visualization:** Actual vs Predicted prices plot

## 📈 Results

Model performance comparison:

| Model | R² Score (Test) | RMSE (Test) | Key Finding |
|-------|----------|------|-----|
| Linear Regression | 0.8466 | 1.8801 | Good baseline, explains 84.66% of variance |
| Polynomial Regression (Degree 2) | **0.9750** | **0.7593** | **Best model - explains 97.5% of variance** |

**Performance Improvement:** Polynomial regression (degree 2) is 11.84% more accurate than linear regression!

### Key Findings:

1. **Polynomial Regression is Superior:** Degree 2 polynomial model significantly outperforms linear regression with R² = 0.9750 vs 0.8466

2. **RMSE of 0.7593 lakhs:** Predictions are off by approximately ₹75,930 on average - very accurate for practical use

3. **Present Price is Dominant Predictor:** 
   - Coefficient: 3.8018 (strongest impact)
   - A car's current market price is the best indicator of its selling price
   - Makes intuitive sense: newer, more valuable cars sell for higher prices

4. **Car Age Negatively Impacts Price:**
   - Coefficient: -1.0449 (second strongest impact, but negative)
   - Each year of age reduces selling price by approximately ₹1 lakh
   - Older cars depreciate significantly

5. **Seller Type Matters:** 
   - Individual sellers get lower prices than dealers (-0.6246 coefficient)
   - Dealerships negotiate better prices

6. **Transmission Type Impact:**
   - Automatic transmissions are worth more than manual (-0.5565 for manual)
   
7. **Fuel Type Preference:**
   - Petrol cars command better prices than diesel/CNG

### Model Performance Insights:

- **High R² Score (0.9750):** The model explains 97.5% of the variation in car prices
- **Low RMSE:** Average prediction error is less than 1 lakh rupees
- **Practical Usability:** The model is accurate enough for real-world price estimation
- **Feature Importance:** 5 features dominate predictions (Present Price, Car Age, Seller Type, Fuel Type, Transmission)

## 🛠️ Technologies & Libraries

- **Language:** Python 3.x
- **Data Manipulation:** pandas, numpy
- **Visualization:** matplotlib, seaborn
- **Machine Learning:** scikit-learn
- **Preprocessing:** StandardScaler, LabelEncoder, PolynomialFeatures
- **Jupyter:** For interactive analysis

## 📦 Installation

### Prerequisites
- Python 3.7 or higher
- pip (Python package manager)

### Setup Instructions

1. **Clone the repository:**
```bash
git clone https://github.com/Silver-rose0/car-price-prediction.git
cd car-price-prediction
```

2. **Create a virtual environment (recommended):**
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

3. **Install required dependencies:**
```bash
pip install -r requirements.txt
```

## 🚀 Usage

1. **Launch Jupyter Notebook:**
```bash
jupyter notebook
```

2. **Open the notebook:**
```bash
SellCarModel.ipynb
```

3. **Run cells sequentially** to see:
   - Data loading & exploration
   - Data preprocessing & cleaning
   - Feature engineering
   - Model training with different algorithms
   - Model evaluation & comparison
   - Visualization of results

## 📁 Project Structure

```
car-price-prediction/
├── README.md                           # Project documentation
├── requirements.txt                    # Python dependencies
├── .gitignore                         # Git ignore file
├── SellCarModel.ipynb                 # Main Jupyter notebook
└── data/
    └── cardata.csv                    # Car sales dataset
```

## 📚 How to Interpret Results

### R² Score
- Ranges from 0 to 1
- **this model:** R² = 0.9750 = "Excellent fit"
- This means the model explains 97.5% of price variation
- Only 2.5% of variation is unexplained (very good!)

### RMSE (Root Mean Squared Error)
- Average error in price units (lakhs)
- **Your model:** RMSE = 0.7593 lakhs = ~₹75,930 average error
- This is excellent for car price prediction
- Predictions are typically within ±75k of actual price

### Visualization
- Actual vs Predicted plot shows predictions closely follow the diagonal line
- This confirms the model predictions are very accurate

## 🎯 Feature Importance Ranking

### Top 5 Features That Predict Car Price:

1. **Present_Price (Coefficient: 3.8018)** ⭐⭐⭐⭐⭐
   - Strongest predictor
   - Current market value is the best indicator of selling price
   - Higher present price → Higher selling price

2. **Car_Age (Coefficient: -1.0449)** ⭐⭐⭐⭐
   - Second most important factor
   - Negative impact: older cars sell for less
   - Approximately -₹1 lakh per year of age

3. **Seller_Type (Coefficient: -0.6246)** ⭐⭐⭐
   - Dealers get better prices than individuals
   - Individual sellers lose ~₹60k compared to dealer sales

4. **Fuel_Type (Coefficient: -0.5694)** ⭐⭐⭐
   - Petrol cars command premium prices
   - Diesel/CNG cars sell at discount (~₹55k less)

5. **Transmission (Coefficient: -0.5565)** ⭐⭐⭐
   - Automatic transmissions worth more
   - Manual transmission reduces price (~₹55k)

## 📝 How to Read This Project

1. Start with **data loading & exploration** to understand car market data
2. Review **preprocessing steps** to see data cleaning approach
3. Study **feature engineering** to understand transformations
4. Compare **Linear vs Polynomial** regression performance
5. Analyze **results** to see which model performs better

## 🤝 Contributing

Suggestions and improvements are welcome! Feel free to fork and improve.

## 📄 License

This project is open source and available under the MIT License.

## 📧 Contact & Portfolio

This project is part of my machine learning portfolio. Feel free to reach out with questions!

---

**Last Updated:** 2026  
**Status:** Active Learning Project  
**Difficulty Level:** Beginner to Intermediate
