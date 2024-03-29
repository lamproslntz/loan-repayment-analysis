# Data Science Case Study: Loan Repayment Analysis

## Overview
This case study is designed to test your skills in data exploration, feature engineering, machine learning, and analytics. You will work with three tables with data that **will be provided to you in a sqlite .db file**: `loans`, `loan_repayments`, and `transactions`, to build a model that can predict loan repayment behavior.

Learning to deal with new technologies and challenges is also part of the test.

This is challenging on purpose.
**Good luck friend!**

## Objective
Your primary goal is to explore the provided data, understand the operational dynamics, create meaningful features, and develop a machine learning model to distinguish between good and bad loans. This model must be able to, given the features of a new user, define if we should or shouldn't give a loan to them.

## Table Schemas

### Loans Table
- **id (int)**: Unique identifier for the loan.
- **user_id (int)**: Unique identifier for the user who has taken the loan.
- **amount (float)**: The amount of loan disbursed.
- **total_amount (float)**: The amount of loan, including fees.
- **due_amount (int)**: The amount of the loan by the due date if there are no repayments during the contract period. Good to get interest rates.
- **due_date (object)**: The date by which the loan is due.
- **status (object)**: Current status of the loan (e.g., repaid, debt_collection, ongoing, debt_repaid).
    - **repaid**: A loan that was was paid until due.
    - **debt_collection**: A loan that was not paid until due.
    - **debt_repaid**: A loan that was not paid until due but we recovered the money somehow.
    - **cancelled**: A canceled loan.
    - **error**: Operational error.
- **created_at (object)**: Timestamp of when the loan record was created. <u>Have it as the beginning of the loan</u>.

### Loan Repayments Table
- **id (int)**: Unique identifier for the repayment record.
- **loan_id (int)**: The ID of the loan this repayment is associated with.
- **type (object)**: The type of repayment (e.g., autopilot, pix).
- **amount (float)**: The amount that was repaid.
- **status (object)**: Status of the repayment.
    - **paid**: A loan repayment that effectively happened.
    - **defaulted**: A loan repayment that didn't come to reality.
    - **refunded**: A loan repayment that happened but was fully refunded to the user. 
- **created_at (object)**: Timestamp of when the repayment record was created. <u>Have it as the moment of the repayment</u>.

### Transactions Table
- **id (int)**: Unique identifier for the transaction.
- **user_id (int)**: The user ID associated with the transaction.
- **amount (float)**: Transaction amount.
- **status (object)**: Status of the transaction.
    - **approved**: A transaction that happened.
    - **denied**: A transaction that didn't happened due to it being denied.
- **capture_method (object)**: Method of capturing the transaction.
- **payment_method (object)**: Payment method used (e.g., credit, debit).
- **installments (int)**: Number of installments for the transaction.
- **card_brand (object)**: Brand of the card used for the transaction.
- **created_at (object)**: Timestamp of when the transaction record was created. <u>Have it as the moment the transaction happened</u>.

## Tasks
1. **Data Exploration**: Familiarize yourself with the data. Understand the relationships between the tables and the meaning of each field.
2. **Operational Insights**: Analyze the loans and repayment patterns. Visualize key metrics and trends.
3. **Feature Engineering**: Create features from the transactions data that could help in differentiating between good and bad payers.
4. **Label Definition**: Define a clear label for good and bad loans based on loan repayment behavior.
5. **Data Splitting**: Split the data into training and testing sets in a time-consistent and non-leaky way.
6. **Preprocessing Pipeline**: Prepare your data for modeling the way you see fit.
7. **Model Training**: Build and train a model using the features to predict loan repayment behavior.
8. **Iteration and Improvement**: Refine your model, features, and approach based on model performance.

## Deliverables
1. **Exploratory Data Analysis (EDA)**: A report or Jupyter notebook detailing your EDA process and findings.
2. **Feature Engineering Notebook**: Notebook with feature creation code and analysis (you can create in SQL,Python or in whichever other way you see fit).
3. **Modeling Notebook**: A Jupyter notebook containing the modeling process, including data preprocessing, model training, and evaluation.
4. **Final Report**: A <u>brief (!!!)</u> report outlining your approach, methodologies used, key insights, model performance, and any recommendations or conclusions. Don't overthink this, I'll be checking your code, but this way you can help me to help you.

## Evaluation Criteria
- **Quality of EDA**: Go beyond what's obvious and get true insights that will ENABLE you to continue.
- **Problem Structuring**: Understand the problem you are trying to solve and create a meaningful label.
- **Feature Engineering**: Creativity and effectiveness in feature creation.
- **Model Performance**: Show us what you can do.
- **Clarity and Structure of Deliverables**: How well-structured and understandable your reports and notebooks are.

## Tips for Success
- **Understand the Relationships**: Pay special attention to how the tables relate to each other. You can guess what happens if you make a mistake here...
- **Document Your Findings**: Keep a record of your insights, decisions, and rationales as you go through the data. This will be valuable.
- **Be Wary of Data Leakage**: Ensure that your training data does not contain information from the future (i.e., the test set period) or information not available at prediction time (new user being evaluated). Real data science problems are tricky, be a bit paranoid :).
- **Think Like a Business/Detective**: When creating features, consider what factors you would deem important if you were assessing loan repayment ability and had this data available.
- **Model Selection**: Start with simpler models before moving to more complex ones. For tabular data NNs are not the state of art... If you can deliver results though, any model is good.
- **Iterative Process**: Data science is iterative. Don't hesitate to revisit earlier steps if you find new insights later in the process.
