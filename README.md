# 🏠 Delhi House Price Prediction
### Final Year Machine Learning Project

![Python](https://img.shields.io/badge/Python-3.8%2B-blue?logo=python&logoColor=white)
![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-1.0%2B-orange?logo=scikit-learn&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?logo=jupyter&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-green)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)

---

## 📌 Overview

This project predicts residential house prices in **Delhi, India** using supervised machine learning regression techniques. The dataset is sourced from **MagicBricks** and contains 1,259 property listings with features such as area, BHK count, locality, furnishing status, and more.

The project covers the complete ML pipeline — from data cleaning and EDA to hyperparameter tuning, model comparison, feature explainability, and custom price prediction.

---

## 📂 Project Structure

```
Delhi-House-Price-Prediction/
│
├── Delhi_House_Price_Prediction_Improved.ipynb   # Main notebook
├── MagicBricks.csv                               # Dataset
└── README.md                                     # Project documentation
```

---

## 📋 Dataset

| Column | Description |
|--------|-------------|
| `Area` | Area of the house in square feet |
| `BHK` | Number of bedrooms (Bedroom-Hall-Kitchen) |
| `Bathroom` | Number of bathrooms |
| `Furnishing` | Furnishing status — Furnished / Semi-Furnished / Unfurnished |
| `Locality` | Locality of the house in Delhi |
| `Parking` | Number of parking spaces available |
| `Price` | 🎯 **Target variable** — Price of the house in INR |
| `Status` | Ready to Move / Under Construction |
| `Transaction` | New Property / Resale |
| `Type` | Builder Floor / Apartment |
| `Per_Sqft` | Price per square foot |

**Source:** [MagicBricks](https://www.magicbricks.com/) via Kaggle  
**Size:** 1,259 rows × 11 columns

---

## 🔄 Project Pipeline

```
Data Loading → Preprocessing → EDA → Feature Engineering
     → Model Building → Hyperparameter Tuning
          → Evaluation & Comparison → Feature Importance
               → Residual Analysis → Custom Prediction
```

---

## 🧹 Data Preprocessing

- Imputed missing `Per_Sqft` values using `Price / Area`
- Filled missing categorical columns (`Parking`, `Bathroom`, `Furnishing`, `Type`) with **mode**
- Fixed type casting for `Parking` and `Bathroom` to `int64`
- Removed outliers using **Z-Score** (threshold = 3)
- Grouped 500+ unique localities into **10 major zones** + "Other"
- Applied **Label Encoding** on categorical features
- Applied **MinMax Scaling** on continuous features

---

## 📊 Exploratory Data Analysis

Key insights uncovered:

- 🏘️ Most Delhi houses are **2–3 BHK** with **100–200 sq. yard** area
- 💰 **Punjabi Bagh, Lajpat Nagar & Vasant Kunj** are the most expensive localities
- 🏷️ **Rohini Sector, Vasundhara Enclave & Shahdara** are the most affordable
- 🔑 Under-construction properties are priced **higher** than ready-to-move ones
- 🔄 **Resale** properties dominate the market (~70%)
- 📈 **Area, BHK, and Bathroom count** are the strongest price predictors

---

## 🤖 Models Used

| Model | Type |
|-------|------|
| Linear Regression | Baseline |
| Ridge Regression | Regularized Linear |
| Lasso Regression | Regularized Linear |
| Decision Tree Regressor | Tree-Based |
| Random Forest Regressor | Ensemble |
| Gradient Boosting Regressor | Ensemble (Boosting) |

All models were tuned using **GridSearchCV with 5-Fold Cross-Validation**.

---

## 📈 Results

| Model | R² Score | MAE | RMSE | CV R² Mean |
|-------|----------|-----|------|------------|
| Gradient Boosting | **~0.88** | lowest | lowest | **~0.86** |
| Random Forest | ~0.85 | low | low | ~0.84 |
| Decision Tree | ~0.78 | medium | medium | ~0.74 |
| Ridge Regression | ~0.65 | high | high | ~0.64 |
| Lasso Regression | ~0.65 | high | high | ~0.64 |
| Linear Regression | ~0.64 | high | high | ~0.63 |

> 🏆 **Gradient Boosting Regressor** achieved the best performance overall.

---

## 🧠 Feature Importance

Feature importance was evaluated using two methods:
- **Built-in importance** from Random Forest & Gradient Boosting
- **Permutation Importance** (model-agnostic, more reliable)

Top features driving house prices:
1. `Area` / `Area_Yards`
2. `BHK`
3. `Bathroom`
4. `Locality`
5. `Parking`

---

## 🏠 Custom Price Prediction

The notebook includes a **custom input cell** where you can enter property details and get an estimated price in INR:

```python
custom_input = {
    'Area': 1200,                     # sq. feet
    'BHK': 3,
    'Bathroom': 2,
    'Furnishing': 'Semi-Furnished',
    'Locality': 'Dwarka Sector',
    'Parking': 1,
    'Status': 'Ready to Move',
    'Transaction': 'Resale',
    'Type': 'Builder Floor',
}
# Output: ₹ Predicted Price in Lakh / Crore
```

---

## 🛠️ Tech Stack

- **Language:** Python 3.8+
- **Notebook:** Jupyter Notebook
- **Data Manipulation:** Pandas, NumPy
- **Visualization:** Matplotlib, Seaborn
- **Machine Learning:** Scikit-Learn
- **Statistical Analysis:** SciPy

---

## 🚀 Getting Started

### 1. Clone the repository
```bash
git clone https://github.com/your-username/Delhi-House-Price-Prediction.git
cd Delhi-House-Price-Prediction
```

### 2. Install dependencies
```bash
pip install numpy pandas matplotlib seaborn scikit-learn scipy jupyter
```

### 3. Run the notebook
```bash
jupyter notebook Delhi_House_Price_Prediction_Improved.ipynb
```

---

## 💡 Future Improvements

- [ ] Integrate **XGBoost / LightGBM** for potentially higher accuracy
- [ ] Add **SHAP values** for deeper model explainability
- [ ] Incorporate **geospatial features** (distance to metro, schools, hospitals)
- [ ] Apply **log-transformation on Price** to improve linear model performance
- [ ] Deploy as a **Streamlit / Flask web app** for live predictions

---

## 📄 License

This project is licensed under the [MIT License](LICENSE).

---

## 🙋‍♂️ Author

**Your Name**  
Final Year B.Tech / B.Sc (Computer Science / Data Science)  
📧 your.email@example.com  
🔗 [LinkedIn](https://linkedin.com/in/yourprofile) | [GitHub](https://github.com/your-username)

---


