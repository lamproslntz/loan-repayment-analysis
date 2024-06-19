# Case Study: Loan Repayment Analysis

📃 Presentation: [here](reports/presentation.pdf)

## About the Project

The primary goal is to understand the operational dynamics of lending, create meaningful features, and develop a machine learning model to distinguish between good and bad loans. Given the features of a new user, the model should be able to define whether a loan should be given to them.

## Dataset

### Loans Table
- **id (int)**: Unique identifier for the loan.
- **user_id (int)**: Unique identifier for the user who has taken the loan.
- **amount (float)**: The amount of loan disbursed.
- **total_amount (float)**: The amount of loan, including fees.
- **due_amount (int)**: The amount of the loan by the due date if there are no repayments during the contract period.
- **due_date (object)**: The date by which the loan is due.
- **status (object)**: Current status of the loan (e.g., repaid, debt_collection, ongoing, debt_repaid).
    - **repaid**: A loan that was was paid until due.
    - **debt_collection**: A loan that was not paid until due.
    - **debt_repaid**: A loan that was not paid until due but we recovered the money somehow.
    - **cancelled**: A canceled loan.
    - **error**: Operational error.
- **created_at (object)**: Timestamp of when the loan record was created (beginning of the loan).

### Loan Repayments Table
- **id (int)**: Unique identifier for the repayment record.
- **loan_id (int)**: The ID of the loan this repayment is associated with.
- **type (object)**: The type of repayment (e.g., autopilot, pix).
- **amount (float)**: The amount that was repaid.
- **status (object)**: Status of the repayment.
    - **paid**: A loan repayment that effectively happened.
    - **defaulted**: A loan repayment that didn't come to reality.
    - **refunded**: A loan repayment that happened but was fully refunded to the user. 
- **created_at (object)**: Timestamp of when the repayment record was created (the moment of the repayment).

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
- **created_at (object)**: Timestamp of when the transaction record was created (the moment the transaction happened).

## What You Need

1. Clone the repository
```bash
git clone https://github.com/lamproslntz/loan-repayment-analysis.git
```

2.  Change into the project directory
```bash
cd loan-repayment-analysis
```

3.  Set up a virtual environment and activate it
```bash
python -m venv env
source env/bin/activate  # Linux
env/Scripts/activate.bat  # Windows
```

4.  Install the required dependencies
```bash
pip install -r requirements.txt
```

## License

Distributed under the MIT License. See [LICENSE](LICENSE) for more information