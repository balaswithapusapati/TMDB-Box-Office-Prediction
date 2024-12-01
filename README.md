# **TMDB Box Office Prediction**

This project aims to predict the box office revenue of movies using metadata such as genre, production companies, release date, and more. The model is built using Python and the XGBoost regression algorithm.

---

## **Objective**
To accurately predict movie revenue using metadata provided by the TMDB Box Office Prediction dataset.

---

## **Dataset**
- **Source**: [Kaggle - TMDB Box Office Prediction](https://www.kaggle.com/competitions/tmdb-box-office-prediction/data)
- **Files**:
  - `train.csv`: Contains training data with known revenues.
  - `test.csv`: Contains testing data for revenue predictions.

---

## **Project Workflow**

### **1. Data Preprocessing**
- Dropped irrelevant columns (`imdb_id`, `poster_path`, etc.) to reduce noise.
- Processed `release_date` to extract useful features:
  - **Year**: Adjusted years greater than 2022 (e.g., 2023 → 1923).
  - **Month**: Extracted the month of release.
  - **Weekday**: Extracted the day of the week.
- Converted `homepage` and `belongs_to_collection` to binary indicators.
- Filled missing `status` values with `'Released'`.
- Handled complex columns (e.g., `genres`, `production_companies`) by creating dummy variables.

### **2. Feature Engineering**
- Developed a custom function to generate dummy variables for multi-valued categorical features like `genres` and `production_countries`.
- Filled missing values with appropriate default values (`0` for numerical data).

### **3. Model Training**
- **Model Used**: XGBoost Regressor
- **Train-Test Split**:
  - Training Data: Rows with `id <= 3000`
  - Testing Data: Rows with `id > 3000`

### **4. Model Evaluation**
- **Training Metrics**:
  - **R2 Score**: `0.9698`
    
- **Kaggle Leaderboard Score**: `3.36883`

### **5. Submission**
- The predictions for the test set were saved in `submission.csv` for submission to the Kaggle competition.

---

## **Results**
The model achieved a **Train R2 Score** of `0.9698`, indicating excellent fit on the training data. However, the Kaggle score of `3.36883` suggests scope for improving generalization to unseen data.

---



