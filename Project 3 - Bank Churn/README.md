Here’s a README for **Project 3**. Copy it into `project3/README.md` on GitHub.

# Project 3: Bank Customer Churn Analysis

This project analyzes bank customer churn using Python in Google Colab and creates an interactive dashboard in Power BI. It explores which customer groups have higher churn, evaluates two prediction models, and presents a hypothetical retention-offer scenario.

## Project question

Which customer groups are more likely to leave the bank, how well can churn be identified, and where could a retention effort be tested?

## Dataset

The project uses Maven Analytics’ Bank Customer Churn dataset.

- `Bank_Churn.csv`: clean reference data
- `Bank_Churn_Messy.xlsx`: workbook used to practice data cleaning
- `Bank_Churn_Data_Dictionary.csv`: descriptions of the dataset fields
- `Project3_Bank_Churn_Dashboard_Data.xlsx`: prepared data for the Power BI dashboard

The source data contains 10,000 customers. The dashboard workbook includes customer data, test-set risk scores, model metrics, and offer scenarios. Raw data files are not included in this repository.

## Data preparation

The messy workbook was cleaned and checked against the clean reference CSV using `CustomerId`.

- Removed duplicate records and joined customer and account data.
- Standardized `FRA` and `French` to `France`.
- Converted salary and balance from euro-formatted text to numbers.
- Converted Yes/No fields to 1/0.
- Restored three missing ages and surnames from the reference data.
- Corrected inaccurate credit-card values and three placeholder salary values.
- Checked the final data against the reference CSV; all 10,000 customer records matched.

## Analysis and methods

The analysis was completed in Python using pandas and scikit-learn. It includes overall churn, comparisons by geography, age group, number of products, and membership status, plus a comparison of logistic regression and decision tree models.

The data was split into training and test sets using an 80/20 split, with churn proportions preserved. Model performance was evaluated on the 2,000-customer test set using accuracy, precision, recall, and F1 score.

## Key findings

- **Customers:** 10,000
- **Churned customers:** 2,037
- **Overall churn rate:** 20.37%
- **Germany had the highest geography churn rate:** 32.44%
- **Customers aged 50–59 had the highest age-group churn rate:** 56.04%
- **Customers with one product had a 27.71% churn rate**, compared with 7.58% for customers with two products.
- **Inactive members had a 26.85% churn rate**, compared with 14.27% for active members.

The groups with three or four products had much higher churn rates, but they were small groups. Their results should be interpreted carefully.

## Model results

| Model | Accuracy | Precision | Recall | F1 score |
|---|---:|---:|---:|---:|
| Logistic regression | 81.6% | 62.7% | 23.6% | 34.3% |
| Decision tree | 85.7% | 72.7% | 47.7% | 57.6% |

The decision tree performed better on these test-set measures. Its recall was 47.7%, meaning it identified fewer than half of the customers who actually churned in the test set.

## Retention-offer scenario

A hypothetical scenario targets the 267 high-risk customers in the test set. It assumes an offer costs €10 per customer and estimates retention uplifts of 5%, 10%, or 15%. Under those assumptions, the estimated cost per additional retained customer ranges from €200 to €66.67.

These are scenario estimates, not measured campaign results. The dataset does not include actual offer responses or campaign costs.

## Power BI dashboard

The interactive dashboard is planned to include:

- Customer, churned-customer, retained-customer, and churn-rate cards
- Slicers for geography, gender, age group, membership status, and number of products
- Churn comparisons by geography, age group, product count, and membership status
- Model performance comparison
- Test-set churn risk by risk band
- Hypothetical retention-offer scenario

Risk scores and model results describe the 2,000-customer test set, not all 10,000 customers.

## Limitations

- Churn patterns show associations and do not prove causes.
- A model’s risk score is an estimate, not certainty that a customer will leave.
- The offer scenario is hypothetical and does not prove an offer will retain customers.
- The dataset does not provide measured campaign outcomes or enough information to calculate actual profitability.
- Small customer groups can produce unstable churn rates.

## Tools used

Python, pandas, scikit-learn, Google Colab, Excel, and Power BI.

## AI use

AI was used for guidance with project planning, explanations, and documentation. Code and results were reviewed against the dataset and analysis outputs.

