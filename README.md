# 🏀 NBA Player Longevity Prediction using Gaussian Naive Bayes

## Project Overview

This project uses **Gaussian Naive Bayes (GNB)** to predict whether an NBA player will remain in the league for **at least five years** based on their early-career statistics.

The analysis demonstrates how probabilistic machine learning models can support scouting decisions by identifying long-term talent while balancing the risk of selecting future busts.

---

## Business Problem

NBA teams invest heavily in scouting and player development. Predicting whether a player will remain in the league for at least five years can help teams:

* Identify long-term talent
* Reduce costly draft mistakes
* Support scouting decisions with data-driven insights

**Target Variable:**

* `target_5yrs = 1` → Player remains in the NBA for at least 5 years
* `target_5yrs = 0` → Player does not remain for 5 years

---

## Dataset

The dataset contains engineered NBA player statistics, including:

* Points scored
* Minutes played
* Rebounds
* Assists
* Shooting statistics
* Other performance metrics

---

## Methodology

### 1. Data Exploration

* Loaded and explored the dataset
* Checked missing values
* Examined feature distributions
* Investigated feature correlations

### 2. Data Preparation

* Defined `target_5yrs` as the classification target
* Split data into training and testing sets (80/20)

### 3. Model Development

* Built a baseline **Gaussian Naive Bayes** classifier
* Applied **GridSearchCV** for hyperparameter tuning using `var_smoothing`

### 4. Model Evaluation

Evaluated performance using:

* Accuracy
* Precision
* Recall
* F1 Score
* Confusion Matrix

---

## Results

### Baseline Model

| Metric    | Score |
| --------- | ----: |
| Accuracy  | 0.664 |
| Precision | 0.869 |
| Recall    | 0.550 |
| F1 Score  | 0.674 |

Confusion Matrix:

```text
[[85 14]
 [76 93]]
```

---

### Tuned Model

| Metric    | Score |
| --------- | ----: |
| Accuracy  | 0.690 |
| Precision | 0.736 |
| Recall    | 0.793 |
| F1 Score  | 0.764 |

Confusion Matrix:

```text
[[51 48]
 [35 134]]
```

---

## Business Interpretation

### Precision: Minimize False Positives (Draft Busts)

Precision measures how often players predicted to succeed actually succeed.

Higher precision means fewer players are incorrectly identified as future stars.

### Recall: Minimize False Negatives (Missed Talent)

Recall measures how many true long-term players the model successfully identifies.

Higher recall reduces the risk of overlooking future NBA talent.

The tuned model substantially improved recall, making it more effective for talent identification.

---

## Naive Bayes Independence Assumption

Gaussian Naive Bayes assumes that all features are conditionally independent given the target class.

In basketball, this assumption is often unrealistic because many statistics are naturally correlated.

Examples include:

* Points scored and minutes played
* Rebounds and playing time
* Assists and usage rate

Although this assumption is violated, Naive Bayes often performs well in practice due to its simplicity and efficiency.

---

## Model Reliability and Limitations

### Strengths

* Fast and computationally efficient
* Easy to interpret
* Works well with smaller datasets
* Useful for supporting scouting decisions

### Limitations

* Assumes independence among player statistics
* Cannot capture complex nonlinear relationships
* May produce false positives when predicting talent
* Should complement, not replace, expert scouting

---

## Key Takeaways

* Hyperparameter tuning improved model performance.
* Recall increased significantly, reducing missed talent.
* Precision decreased, increasing false positives.
* The model is best used as a decision-support tool for scouts.

---

## Technologies Used

* Python
* Pandas
* NumPy
* Matplotlib
* Seaborn
* Scikit-learn

---

## Conclusion

Gaussian Naive Bayes provides a lightweight and interpretable approach for NBA player longevity prediction. While its independence assumption simplifies complex player relationships, the model offers valuable scouting insights when combined with expert evaluation and domain knowledge.
