# Cardiovascular Disease Prediction: Model Training and Evaluation

This project focuses on predicting the presence of cardiovascular disease (CVD) based on a dataset of patient features. It implements a comprehensive machine learning workflow, including data preprocessing, model training, hyperparameter tuning, ensemble methods, and model comparison.  The goal is to develop a robust and accurate model for predicting cardiovascular disease risk, ultimately contributing to improved patient care and preventative strategies.

## Project Overview

Cardiovascular diseases are a leading cause of death globally. Early and accurate prediction of CVD risk is crucial for effective prevention and treatment. This project leverages machine learning techniques to analyze patient data and identify individuals at high risk. By identifying patterns and relationships within the data, we aim to build a model that can assist healthcare professionals in making informed decisions.

The project covers the following key steps:

*   **Data Loading and Preprocessing:** The dataset is loaded, preprocessed (age conversion from days to years, removal of the ID column), and split into training and testing sets.
*   **Model Training and Evaluation:** A variety of classification models are trained and evaluated, including:
    *   KNN
    *   Decision Tree
    *   Random Forest
    *   AdaBoost
    *   Gradient Boosting
    *   XGBoost
    *   Extra Trees
*   **Hyperparameter Tuning:**  `RandomizedSearchCV` is used for efficient hyperparameter optimization of *all* models.  This approach explores a wider range of hyperparameter combinations compared to traditional `GridSearchCV`, often finding better models in less time.  Distributions of hyperparameters are defined using `scipy.stats`.
*   **Ensemble Methods:** Stacking is demonstrated as a technique to combine the predictions of multiple base learners to potentially improve overall performance.
*   **Pipeline:**  `Pipeline` is used extensively to streamline preprocessing (using `StandardScaler` for feature scaling) and model training. This ensures proper data handling and avoids data leakage during cross-validation.
*   **Model Comparison:** The performance of different models (after hyperparameter tuning) is compared using test accuracy.  Interactive visualizations are generated using `Plotly` for clear and informative comparisons.
* **Checkpoint:** Saves and loads the status of `RandomizedSearchCV` using `joblib` to allow resuming training from where it left off, saving significant time.
*   **Early Stopping:** Implements early stopping in the XGBoost algorithm to prevent overfitting and speed up training.
* **Repeated Stratified K-Fold Cross-Validation:**  Utilizes `RepeatedStratifiedKFold` for robust model evaluation.

## Repository Structure
*   **README.md:** This file, providing an overview of the project.
*   **cardio_train_Models.ipynb:** Jupyter Notebook containing the complete analysis and code.
*   **3. cardio_train.csv:** The dataset used for training and evaluation.

## Data

The dataset used in this project is the "Cardiovascular Disease Dataset" . You need to place the `cardio_train.csv` file in the root directory of the project. **Important:** The script expects the CSV file to be semicolon-separated (`;`).

The data has the following columns:

*   age (in days, will be transformed to years)
*   height
*   weight
*   ap_hi (systolic blood pressure)
*   ap_lo (diastolic blood pressure)
*   cholesterol
*   gluc (glucose)
*   smoke
*   alco
*   active
*   cardio (target variable: 0 = no disease, 1 = disease present)
*   id (will be removed)

## Justification: The Importance of Cardiovascular Risk Classification

Analyzing the distribution of variables like age, blood pressure, cholesterol, glucose, and weight is critical for understanding and predicting cardiovascular risk.  Visualizations like violin plots (not directly included in this *specific* script, but a valuable addition for future EDA) can reveal variations and concentrations in these distributions, providing insights for:

*   **Prediction:**  Identifying patterns that predict future cardiovascular events.
*   **Management:**  Stratifying patients based on risk levels to tailor interventions.
*   **Understanding Risk Factors:**  Gaining a deeper understanding of the interplay of various risk factors.

> "La visualización de datos mediante gráficos de violín permite identificar patrones y diferencias en las distribuciones de variables fisiológicas. Estas diferencias pueden ser relevantes para la comprensión de factores de riesgo y la estratificación de pacientes en el contexto de las enfermedades cardiovasculares."
>
> — Rodríguez-Padial, L., & Ávila-Gandía, V. (2021). *Estadística para Ciencias de la Salud.* Paraninfo. ISBN: 9788428344825

Observations from exploratory data analysis (EDA, which *should* precede this modeling script) have shown:

*   Trends in age and weight that could aid in diagnosis.
*   Outliers in blood pressure, cholesterol, and glucose that highlight the need for further investigation, particularly in the context of hypertension.

> "Las variaciones en la distribución de variables... pueden estar asociadas a un mayor riesgo de enfermedades cardiovasculares. La identificación de valores extremos o concentraciones en ciertos intervalos puede ser útil para la predicción y el manejo de estas enfermedades."
>
> — García-Moll, X., & García-Legaz, S. (2018). *Manual de Hipertensión Arterial.* Elsevier España. ISBN: 9788491132638

This project emphasizes the importance of exploratory analysis and machine learning in medical data science, providing tools to improve the quality of care and prevention in cardiovascular health.
