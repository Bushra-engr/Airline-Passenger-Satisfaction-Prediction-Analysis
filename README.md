# ✈️ Airline Passenger Satisfaction Prediction

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![Library](https://img.shields.io/badge/Library-Scikit--Learn%20%7C%20XGBoost%20%7C%20CatBoost-orange)
![Status](https://img.shields.io/badge/Status-Completed-green)

## 📌 Project Overview
This project aims to predict whether an airline passenger is **Satisfied** or **Neutral/Dissatisfied** based on their flight experience factors like service quality, delays, and flight class.

I have implemented an End-to-End Machine Learning pipeline including Data Cleaning, Exploratory Data Analysis (EDA), Feature Engineering, and Model Building using various algorithms including **XGBoost** and **CatBoost**.

---

## 📂 Dataset Description
The dataset contains **103,904 rows** and **25 columns**.
* **Target Variable:** `satisfaction` (0: Neutral/Dissatisfied, 1: Satisfied)
* **Key Features:** Class, Flight Distance, Inflight Services (Wifi, Food, Seat Comfort), Delays, Age, Customer Type.

---

## 🛠️ Data Preprocessing & Feature Engineering
Before feeding data into models, the following steps were taken:

1.  **Handling Missing Values:**
    * Found missing values in `Arrival Delay in Minutes`.
    * Created a new feature `total_delay` = `Departure Delay` + `Arrival Delay`.
    * Filled missing `total_delay` with **Median**.
2.  **Dropping Irrelevant Columns:**
    * Dropped `id`, `Unnamed: 0` (useless identifiers).
    * Dropped `Gender_Male`, `Gate location`, `Departure/Arrival time convenient` based on low correlation/feature importance.
3.  **Encoding:**
    * **Label Encoding:** For target `satisfaction`.
    * **Ordinal Mapping:** For `Class` (Business=1, Eco Plus=2, Eco=0).
    * **One-Hot Encoding:** For `Customer Type`, `Type of Travel`.
4.  **Feature Scaling:**
    * Applied `StandardScaler` on numerical columns: `Age`, `Flight Distance`, `total_delay`.

---

## 📊 Exploratory Data Analysis (EDA) Insights
* **Class vs Satisfaction:** Business class passengers are significantly more satisfied compared to Eco class.
* **Travel Type:** 'Personal Travel' usually results in lower satisfaction compared to 'Business Travel'.
* **Delays:** As `total_delay` increases, satisfaction tends to decrease (visualized via Boxplots).
* **Services:** Features like `Online boarding` and `Inflight entertainment` showed high correlation with satisfaction.

---

## 🤖 Model Building & Performance
I trained multiple Supervised Learning models to find the best accuracy.

| Model | Accuracy | F1-Score (Macro) |
| :--- | :--- | :--- |
| **CatBoost Classifier** | **96.15%** 🏆 | **0.96** |
| XGBoost Classifier | 96.11% | 0.96 |
| Random Forest | 96.00% | 0.96 |
| Gradient Boosting | 93.97% | 0.94 |
| K-Nearest Neighbors | 92.96% | 0.93 |
| Decision Tree | 88.96% | 0.89 |
| Logistic Regression | 87.42% | 0.87 |
| Naive Bayes | 87.04% | - |

**Winner:** 🏆 **CatBoost Classifier** with **96.15%** Accuracy.

---

## 🎛️ Hyperparameter Tuning
To further optimize the models, I performed advanced tuning techniques:

1.  **Cross Validation (K-Fold):**
    * Applied on XGBoost.
    * **Mean Score:** 95.54%.
    * This confirmed the model is not overfitting.

2.  **Grid Search CV:**
    * Applied on KNN.
    * Best Parameter: `n_neighbors: 5`.

3.  **Randomized Search CV:**
    * Applied on KNN.
    * Best Parameter: `n_neighbors: 7`.
    * Improved Accuracy to **92.88%**.

---

## 🚀 Technologies Used
* **Language:** Python
* **Data Manipulation:** Pandas, NumPy
* **Visualization:** Matplotlib, Seaborn, Plotly
* **ML Libraries:** Scikit-Learn, XGBoost, CatBoost

---

## 📝 Conclusion
The **CatBoost** and **XGBoost** models performed exceptionally well, achieving over **96% accuracy**. The analysis showed that **Inflight Entertainment** and **Seat Comfort** are crucial factors for passenger satisfaction, while **Delays** negatively impact the experience.

---


