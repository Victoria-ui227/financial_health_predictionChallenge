# FINANCIAL HEALTH PREDICTION CHALLENGE

## 1. Overview of the project


The goal of this project was to understand the factors that influence how people manage their savings and assets. Using a dataset provided, I analyzed personal, financial, and insurance-related information to predict whether someone’s savings and assets were High, Medium, or Low. This helps identify groups who may need financial support or targeted programs.

## 2. Data Protection and Cleaning

The first step was to ensure the data was ready for analysis:

- I looked at both numbers (like age, income) and categories (like having insurance or a credit card).

- Missing information was filled in appropriately — for numbers, we used averages; for categories, we labeled missing values as “Missing.”

- I transformed the data into a form that models could understand while keeping the categories separate from numbers.

Challenge: The dataset had missing values and categorical data that models could not interpret directly.
Solution: Used structured cleaning pipelines that handled missing values and converted categories into numeric formats.

## 3. Models tested and results

a) XGBoost Model

What it does: A model that learns patterns from features to predict the savings category.

Improvements: We used a technique called SMOTE to ensure that minority categories (people with High or Medium savings) were not ignored by the model.

Results:

Accuracy: 88%

Low savings were predicted very well (high recall), but initially, High savings were often misclassified.

By oversampling and balancing the dataset, predictions for High and Medium categories improved.

Challenge: The model was biased toward the largest group (Low savings) because there were more examples in that category.
Solution: Applied SMOTE to artificially increase the number of High and Medium cases, so the model could learn patterns for all groups equally.

b) Feature Analysis

We analyzed which factors mattered most in predicting savings behavior.

Top factors:

Having funeral insurance, medical insurance, or a credit card

Owning a motor vehicle

Having a loan account

Impact: This helped us understand which financial behaviors are strongly linked to higher savings.

Challenge: Some features were less obvious in their influence.
Solution: Using the model’s feature importance, we could clearly identify the strongest predictors and focus on them.

## Challenges and solutions

- Imbalanced Data: Most people fell into the Low savings category.

Solution: Used SMOTE to balance categories and improve predictions for minority groups.

- String-based Labels: The savings categories were words (“High,” “Medium,” “Low”), which some models could not process directly.

Solution: Converted them into numbers for the model and then mapped the results back to words.

- Mismatch in Sample Sizes: When using SMOTE with sample weights, the model sometimes crashed.

Solution: Removed sample weights after oversampling because SMOTE already balances the data.

- Complexity of Features: Some features interacted in ways that were hard to predict manually.

Solution: Used advanced models (like XGBoost) that automatically learn complex patterns without needing manual intervention.

## Recommendations

1. Target financial education: Focus on groups with low savings who do not own insurance or credit products.

2. Encourage insurance uptake: Programs promoting funeral and medical insurance could indirectly improve savings habits.

3. Design tailored financial products: High and Medium savers respond well to credit and loan products — this can guide product development.

4. Continuous monitoring: Keep updating models with new data to track changes in savings behavior and ensure accurate predictions.

