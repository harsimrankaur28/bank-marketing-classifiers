# Comparing Classifiers: Bank Marketing Campaign Prediction

## Business Objective
This project analyzes data from a Portuguese banking institution's telemarketing
campaigns to predict whether a customer will subscribe to a term deposit, using
only basic client demographic information. The goal is to help the bank identify
customers who are more likely to subscribe before making future marketing calls,
improving campaign efficiency.

## Data
Source: [UCI Machine Learning Repository — Bank Marketing Dataset](https://archive.ics.uci.edu/ml/datasets/bank+marketing)
~41,000 records from 17 marketing campaigns, using client demographic features
(age, job, marital status, education, default/housing/loan status).

## Approach
- Established a baseline (majority-class) accuracy of ~88.7%
- Compared four classifiers — Logistic Regression, KNN, Decision Tree, and SVM —
  using default settings
- Tuned each model via grid search with 3-fold cross-validation, optimizing for
  F1 score rather than accuracy, since only ~11% of customers subscribe
  (accuracy alone is misleading on imbalanced data)
- Interpreted Logistic Regression coefficients to identify which client
  characteristics are associated with subscription

## Key Findings
- Best-performing model: **Logistic Regression** (tuned), with test F1 = **0.223**,
  recall = **53.1%**, precision = **14.1%**
- Being a student or retired, and having no credit default, were the strongest
  positive predictors of subscription among the demographic features tested
- Demographic data alone is a weak-to-moderate signal — useful as an initial
  filter, but not sufficient on its own for confident targeting

## Recommendations
- Use the tuned Logistic Regression model as a low-cost initial filter to
  deprioritize very unlikely customers
- For meaningfully better performance, expand the feature set in a future
  iteration to include contact-history and macroeconomic indicators (e.g., prior
  campaign outcome, euribor rate), which are known to be stronger predictors
- Re-evaluate the precision/recall tradeoff based on actual call costs: prioritize
  precision if reducing call volume matters most, or recall if maximizing
  captured subscribers matters most

## Repository Structure
- `prompt_III.ipynb` — full analysis notebook (EDA, modeling, tuning, findings)
- `data/` — dataset files (bank-additional-full.csv, bank-additional.csv)

## Notebook
[View the full analysis notebook](https://github.com/harsimrankaur28/bank-marketing-classifiers/blob/76b42259e5dd3deb4b3dc0de17d1c19c9aef3e4e/prompt_III.ipynb)
