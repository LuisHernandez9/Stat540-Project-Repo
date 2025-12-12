# STAT 540 – Project 3: Decision Trees & Classification with NHANES

This project uses data from the **National Health and Nutrition Examination Survey (NHANES)** to explore **risk factors for diabetes** and apply several **classification methods** in R. The main focus is on building and evaluating models that predict whether a person has diabetes based on demographic and health variables.

All work is contained in **`STAT540-Project 3.Rmd`**.

---

## 📊 Dataset

- **Source package:** `NHANES` (R package)
- **Raw data:** `NHANES`
- **Working subset:** `people`

The `people` dataset is created by:

- Selecting the variables:
  - `Age`
  - `Gender`
  - `Diabetes`
  - `BMI`
  - `HHIncome` (household income)
  - `PhysActive` (physical activity)
- Dropping rows with missing values.

This subset is then used for all subsequent modeling and analysis.

---

## 🧩 Project Overview

### Part 1 – Creating the Working Dataset

- Load the `NHANES` data.
- Create a cleaned subset called **`people`** with selected variables and no missing values.
- Glimpse the resulting data to understand its structure.

### Part 2 – Diabetes Prevalence

- Use `group_by()` and `count()` to compute how many people **have** and **do not have** diabetes.
- Store results in a data frame called **`DiabetesFreq`**.
- Add a percentage column to show the proportion of each category.

### Part 3 – Decision Tree Classifier

- Build a **decision tree** to predict `Diabetes` using:
  - `Age`
  - `BMI`
  - `Gender`
  - `PhysActive`
- Implemented with **`parsnip`** and **`rpart`** as the engine.

### Part 4 – Visualizing the Tree

- Plot the fitted decision tree using **`partykit`** and `as.party()`.
- Interpret the tree in terms of:
  - How age and BMI splits relate to diabetes risk.
  - Which groups appear at highest risk (e.g., older age ranges with higher BMI).

### Part 5 – Decision Boundaries in Age–BMI Space

- Create a visualization of the decision tree’s **decision regions** in the **Age vs BMI** plane.
- Use `ggplot2` along with `segments` to show:
  - How the space is partitioned into regions.
  - Where the model predicts higher diabetes risk.
- Highlight the highest-risk rectangle (specific age and BMI range).

### Part 6 & 7 – Confusion Matrix and Accuracy

- Use **`yardstick`** to:
  - Generate a **confusion matrix** for the decision tree predictions on the `people` dataset.
  - Compute the **classification accuracy**.
- Briefly interpret how well the tree fits the data.

### Part 8 – Predicting for a Single Patient

- Use the fitted decision tree model to predict the **Diabetes status** for a singled-out patient (`patient7`).
- Interpret the prediction in context of that patient’s risk factors.

---

## 🧠 Task 2 & 3 – Supervised Learning Algorithms

After the tree-based exploration, the project moves into a more general **classification comparison**:

### Train/Test Split

- Create **training (≈80%)** and **test (≈20%)** sets from the `people` data.
- Check:
  - The percentage of the sample that has diabetes.
  - The accuracy of a **null model** (always predicting the majority class).

### Model Definition

- Define a formula for predicting `Diabetes` (e.g., `Diabetes ~ Age + BMI + Gender + PhysActive + HHIncome`).
- This formula is reused across different classifiers.

### K-Nearest Neighbors (KNN)

- Fit a **KNN classifier** on the training set.
- Predict on the test set.
- Compute and report **accuracy**.

### Naive Bayes Classifier

- Fit a **Naive Bayes** model to predict `Diabetes`.
- Evaluate performance on the test set.
- Compute and report **accuracy**.

### Logistic Regression

- Fit a **Logistic Regression** model using the same predictors.
- Predict diabetes status on the test data.
- Compute and report **accuracy**.

### Model Comparison

- Compare at least **two** of the classifiers (e.g., decision tree vs logistic regression, or KNN vs Naive Bayes).
- Use **test-set accuracy** as the main metric.
- Comment on which model performs better and possible reasons why.

---

## 🧠 Skills Practiced

- Data cleaning and subsetting with **`dplyr`**
- Exploratory summaries of binary outcomes
- Decision trees using **`parsnip`** + **`rpart`**
- Tree visualization with **`partykit`**
- Confusion matrices and accuracy with **`yardstick`**
- Train/test splits for supervised learning
- Implementing and comparing:
  - K-Nearest Neighbors
  - Naive Bayes
  - Logistic Regression

---

## 📄 Main File

- **`STAT540-Project 3.Rmd`**  
  Contains all code, plots, and written answers. Knitting this file generates an HTML notebook explaining the full diabetes classification analysis.
