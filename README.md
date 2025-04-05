# HELOC Credit Risk Prediction

This repository contains the code and analysis for predicting credit risk in Home Equity Lines of Credit (HELOC). The project focuses on identifying borrowers with high risk of non-repayment. Our approach emphasizes explainability and optimization of the F1-score to balance two critical business objectives: minimizing the loss of potential customers while avoiding the costs associated with granting credit to high-risk borrowers.

---

## Table of Contents

- [Overview](#overview)
- [Dataset](#dataset)
- [Methodology](#methodology)
  - [Data Preprocessing and Feature Engineering](#data-preprocessing-and-feature-engineering)
  - [Model Training and F1-Score Optimization](#model-training-and-f1-score-optimization)
- [Results and Explainability](#results-and-explainability)
---

## Overview

The objective of this project is to predict the repayment behavior of HELOC borrowers. In the context of credit risk, it is crucial to:
- **Avoid rejecting potential good customers:** Denying credit to low-risk borrowers can result in lost business opportunities.
- **Prevent granting credit to high-risk borrowers:** Approving credit for borrowers likely to default can lead to significant financial losses.

To address these trade-offs, our model training process is optimized using the **F1-score** as the primary evaluation metric. The F1-score balances precision and recall, ensuring a balanced approach that mitigates both false positives (granting credit to those who might not repay) and false negatives (rejecting credit-worthy applicants).

---

## Dataset

The dataset (`FICO_dataset_reduced_MOD.csv`) contains detailed credit history information for HELOC applicants, including:

### Inputs
1. **ExternalRiskEstimate**: A measure of the borrower's riskiness based on consolidated external data sources.
2. **NetFractionRevolvingBurden**: The proportion of an individual's current credit usage compared to their maximum allowed credit.
3. **AverageMInFile**: The average duration, in months, of the trades in a borrower's credit file.
4. **MSinceOldestTradeOpen**: The age, in months, of a borrower's oldest credit account.
5. **PercentInstallTrades**: The percentage of a borrower's credit accounts that have fixed payment terms over a specified period.
6. **NumSatisfactoryTrades**: Count of trades where the borrower has met obligations satisfactorily.
7. **NumTotalTrades**: Total number of credit accounts.
8. **MSinceMostRecentInqexcl7days**: Months since the last credit inquiry, ignoring the most recent week.
9. **PercentTradesNeverDelq**: The percentage of a borrower's trades with no history of delinquency.

### Output
10. **Risk Performance**: A binary indicator (0 or 1) representing whether the borrower "paid as negotiated" over a 12–36 month period.

---

## Methodology

### Data Preprocessing and Feature Engineering

- **Data Cleaning**: Special placeholder values (e.g., -9, -8, -7) are removed, and missing values are handled based on user input.
- **Encoding and Type Conversion**: The target variable, Risk Performance, is converted to a categorical type.
- **Exploratory Analysis**: Visualizations (histograms, boxplots, Q-Q plots, correlation heatmaps, and pairplots) are used to understand data distributions and relationships.
- **Feature Selection**: Techniques such as the Chi-Squared test, Mutual Information, and PCA are applied to identify the most relevant features for predicting credit risk.

### Model Training and F1-Score Optimization

Multiple classifiers are evaluated through a rigorous pipeline that includes:
- **Hyperparameter Tuning via Grid Search and Cross-Validation**: Models are tuned to maximize the F1-score, a metric chosen for its ability to balance the precision-recall trade-off critical for this application.
- **Models Evaluated**: Logistic Regression, K-Nearest Neighbors, Decision Trees, Random Forest, Support Vector Machines, Gradient Boosting, Naive Bayes, and Multi-Layer Perceptron.
- **Explainability**: For selected models (e.g., Linear SVC and Random Forest), feature coefficients and importances are visualized to provide insights into which attributes most influence risk predictions.

---

## Results and Explainability

- **F1-Score Optimization**: Our evaluation is centered on the F1-score to ensure that the model does not excessively favor either precision or recall. This balance is vital to avoid:
  - **False Positives**: Granting credit to borrowers likely to default, leading to increased financial costs.
  - **False Negatives**: Rejecting credit-worthy borrowers, resulting in lost business opportunities.
  
- **Key Findings**:
  - The models were compared using cross-validation and test set metrics, with the F1-score guiding the final model selection.
  - Detailed visualizations, including confusion matrices and performance bar plots, illustrate model behavior and support explainability.
  - The feature importance analysis highlights which variables drive the prediction, providing stakeholders with transparent, actionable insights for credit decision-making.
