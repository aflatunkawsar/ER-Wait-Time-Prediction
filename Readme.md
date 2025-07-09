# ER Wait Time Prediction using Machine Learning  ⏱️

## Project Overview

This project presents a comprehensive machine learning framework for predicting patient wait times in a hospital Emergency Room (ER). Long and unpredictable wait times are a critical issue in healthcare operations, directly impacting patient satisfaction, quality of care, and resource allocation.

As a lecturer in Industrial and Production Engineering, my motivation was to apply systems thinking and data-driven methodologies to a complex, real-world problem. This project demonstrates the practical application of machine learning not just as a predictive tool, but as a diagnostic instrument for improving process efficiency and operational decision-making in healthcare systems.

---

## Dataset

The analysis is based on the `ER Wait Time Dataset.csv`. This dataset contains anonymized patient visit records. Key features utilized for modeling include:
* **Nurse-to-Patient Ratio**: The staffing ratio in the ER.
* **DayOfWeek**: The day of the week of the patient's visit.
* **Month**: The month of the visit.
* **Target Variable**: `Total Wait Time (min)`

---

## Methodology

The project followed a systematic data science workflow:

1.  **Data Cleaning**: Handled missing data points using median imputation and ensured all data types were correct for analysis.
2.  **Feature Engineering**: Created new time-based features (`DayOfWeek`, `Month`) from timestamps to capture temporal trends.
3.  **Exploratory Data Analysis (EDA)**: Performed visual analysis using histograms, box plots, and heatmaps to discover underlying patterns and relationships in the data.
4.  **Modeling**: Developed and compared multiple regression models to identify the most effective algorithm.
5.  **Hyperparameter Tuning**: Optimized the best-performing model (`XGBoost`) using `RandomizedSearchCV` to further improve its predictive accuracy.

---

## Strategic Feature Engineering

To enhance the model's predictive power, new features were engineered from the raw data. This step demonstrates an understanding of how to translate domain knowledge into machine-readable inputs.

1. **Temporal Feature Extraction**: Created DayOfWeek and Month features from the Visit Date. This allows the model to capture crucial temporal patterns, such as increased weekend traffic or seasonal effects (e.g., flu season).

2. **Avoiding Data Leakage**: Critically, features that would not be known at the time of prediction (e.g., Time to Triage, Time to Medical Professional) were deliberately excluded from the final feature set. This demonstrates a disciplined approach to building a model that is not just accurate in testing, but viable for real-world deployment.

---

## Iterative Model Development and Optimization

A multi-stage modeling approach was used to identify the most effective algorithm.

1. **Baseline Modeling**: A RandomForestRegressor was first established to create a performance baseline.

2. **Advanced Algorithm Evaluation**: More powerful gradient boosting models, XGBoost and LightGBM, were then trained and evaluated. These models are known for their high performance on tabular data and represent a step towards state-of-the-art solutions.

3. **Hyperparameter Tuning**: The best-performing model (XGBoost) was further optimized using RandomizedSearchCV. This automated process systematically searches for the best model configuration, demonstrating a commitment to maximizing performance beyond default settings.

---

## Model Performance Results 🏆

Multiple models were trained and evaluated on the unseen test set. The `XGBoost` model, after hyperparameter tuning, yielded the best performance.

| Model                   | R-squared (R²) | Mean Absolute Error (MAE) | Root Mean Squared Error (RMSE) |
| ----------------------- | -------------- | ------------------------- | ------------------------------ |
| Random Forest (Baseline)| 0.533          | 32.923 minutes            | 46.630 minutes                 |
| XGBoost (Initial)       | 0.561          | 31.942 minutes            | 45.170 minutes  		|
| LightGBM (Initial)      | 0.558	   | 31.987 minutes	       | 45.366 minutes			|
| **XGBoost (Tuned)**     | **0.566**      | **31.596 minutes**        | 44.921 minutes

**Results**: The final tuned `XGBoost` model demonstrated the strongest predictive performance, explaining 56.6% of the variance in wait times with an average error of approximately 31.596 minutes .

---

## Key Findings

The feature importance analysis of the final model revealed the primary drivers of ER wait times. Factors such as Nurse-to-Patient Ratio and specific DayOfWeek patterns were identified as most influential.

This is a critical insight for hospital administration. It provides empirical evidence that operational decisions, such as staffing schedules and resource allocation on peak days, are the most impactful levers for improving patient flow and reducing wait times.

---

## Conclusion and Future Directions

This project successfully developed a robust machine learning model capable of predicting ER wait times with quantifiable accuracy. More importantly, it demonstrates a structured, end-to-end analytical process that translates complex data into actionable operational intelligence.

Future work could include:

1. **Advanced Feature Engineering**: Incorporating features like public holidays or the specific hour of the day.

2. **Deployment**: Packaging the model into a simple web application (using Flask or Streamlit) to serve as a real-time decision-support tool for ER staff.

3. **Fairness Audit**: Analyzing the model's performance across different demographic groups to ensure equitable predictions.

---

## How to Run This Project

To ensure full reproducibility, the project is structured with clear separation of data and code.

1.  Clone the repository.
2.  Install the required libraries listed below.
3.  Execute the Jupyter Notebook in the `/notebooks` directory to review the full analysis.

**Core Libraries:** `Python`, `Pandas`, `Scikit-learn`, `XGBoost`, `Matplotlib`, `Seaborn`.