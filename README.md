# Credit Risk Prediction

## Problem Statement
Our lending company partner ask us to develop a predictive model for assessing credit risk based on historical loan data. The objective is to create a robust model that can accurately predict the likelihood of default or delinquency for future loan applicants.
The expected outcome of this project is a reliable credit risk assessment model that enhances the efficiency and effectiveness of the lending process. By accurately identifying high-risk borrowers, the model will help minimize potential financial losses for lenders and promote responsible lending practices.

## Analytical Approachs
Exploratory data analysis to understand the data distribution and identify patterns.
Feature selection to identify the most relevant variables for predicting credit risk.
Model training and evaluation using machine learning algorithms.
I use Binning, WoE, IV, PD Model White-Box and Black-Box.

## Data Set
The provided credit risk dataset contains information related to loan applications and borrowers, offering insights into the factors influencing creditworthiness. It includes attributes such as credit scores, employment history, loan amounts, and borrower demographics. The dataset presents an opportunity to analyze and model credit risk, enabling lenders to make informed decisions while evaluating loan applications and managing potential default or delinquency risks.

## Data Dictionary
> **Identifier columns**

|variable                       |type     |description |
|:------------------------------|:---------|:-----------|
id 			|int64|Unique LC assigned ID for the loan listing.
member_id 		|int64|Unique LC assigned Id for the borrower member.

> **Borrowers & co-borrower's personal information columns**

|variable                       |type     |description |
|:------------------------------|:---------|:-----------|
emp_title 			|object|The job title supplied by the Borrower when applying for the loan.*
emp_length 		|object|Employment length in years. Possible values are between 0 and 10 where 0 means less than one year and 10 means ten or more years. 
home_ownership 			|object|The home ownership status provided by the borrower during registration. The values are: RENT, OWN, MORTGAGE, OTHER.
annual_inc 		|float64|The self-reported annual income provided by the borrower during registration.
zip_code 			|object|The first 3 numbers of the zip code provided by the borrower in the loan application.
addr_state 		|object|The state provided by the borrower in the loan application.
annual_inc_joint 			|float64| The combined self-reported annual income provided by the co-borrowers during registration.

> **Loan specific columns**

|variable                       |type     |description |
|:------------------------------|:---------|:-----------|
loan_amnt 			|int64|Last month payment was received.
funded_amnt 			|int64|The total amount committed to that loan at that point in time.
funded_amnt_inv 			|float64|The total amount commited by investors for that loan at that point in time.
term 			|object|The number of payments on the loan. Values are in months and can be either 36 or 60.
int_rate 			|float64|Indicates if income was verified by LC, not verified, or if the income source was verified.
installment 			|float64|The monthly payment owed by the borrower if the loan originates.
grade 			|object|LC assigned loan grade.
sub_grade 			|object|LC assigned loan subgrade.
issue_d 			|object|The month which the loan was funded.
loan_status 			|object|Current status of the loan
pymnt_plan 			|object|Indicates if a payment plan has been put in place for the loan.
url 			|object|URL for the LC page with listing data.
desc 			|object|Loan description provided by the borrower.
purpose 			|object|A category provided by the borrower for the loan request.
title 			|object| The loan title provided by the borrower.
initial_list_status 			|object|The initial listing status of the loan. Possible values are – Whole, Fractional
out_prncp 			|float64|Remaining outstanding principal for total amount funded.
out_prncp_inv 			|float64|Remaining outstanding principal for portion of total amount funded by investors.
total_pymnt 			|float64|Payments received to date for total amount funded.
total_pymnt_inv 			|float64|Payments received to date for portion of total amount funded by investors.
total_rec_prncp 			|float64|Interest received to date.
total_rec_int 			|float64|Interest received to date.
total_rec_late_fee 			|float64|Late fees received to date.
recoveries 			|float64|Indicates if a payment plan has been put in place for the loan.
collection_recovery_fee 			|float64|Post charge off collection fee.
last_pymnt_d 			|object|Last month payment was received.
last_pymnt_amnt 			|float64|Last total payment amount received.
next_pymnt_d 			|object|Next scheduled payment date
last_credit_pull_d 			|object|The most recent month LC pulled credit for this loan.
application_type 			|object|Indicates whether the loan is an individual application or a joint application with two co-borrowers.

> **Borrowers & co-borrower's public records columns**

|variable                       |type     |description |
|:------------------------------|:---------|:-----------|
verification_status 			|object|Indicates if income was verified by LC, not verified, or if the income source was verified.
dti 			|float64|A ratio calculated using the borrower’s total monthly debt payments on the total debt obligations, excluding mortgage and the requested LC loan, divided by the borrower’s self-reported monthly income.
dti_joint 			|float64|A ratio calculated using the co-borrowers' total monthly payments on the total debt obligations, excluding mortgages and the requested LC loan, divided by the co-borrowers' combined self-reported monthly income.
verification_status_joint 			|float64|Indicates if the co-borrowers' joint income was verified by LC, not verified, or if the income source was verified.
delinq_2yrs 			|float64|The number of 30+ days past-due incidences of delinquency in the borrower's credit file for the past 2 years.
earliest_cr_line 			|object|The month the borrower's earliest reported credit line was opened.
inq_last_6mths 			|float64|The number of inquiries in past 6 months (excluding auto and mortgage inquiries).
mths_since_last_delinq 			|float64|The number of months since the borrower's last delinquency.
mths_since_last_record 			|float64| The number of months since the last public record.
open_acc 			|float64|The number of open credit lines in the borrower's credit file.
pub_rec 			|float64|Number of derogatory public records.
revol_bal 			|int64|Total credit revolving balance.
revol_util 			|float64|Revolving line utilization rate, or the amount of credit the borrower is using relative to all available revolving credit.
total_acc 			|float64|The total number of credit lines currently in the borrower's credit file.
collections_12_mths_ex_med 			|float64|Number of collections in 12 months excluding medical collections.
mths_since_last_major_derog 			|float64|Months since most recent 90-day or worse rating.
acc_now_delinq 			|float64|The number of accounts on which the borrower is now delinquent.
total_col_amnt 			|float64|The total collection amounts ever owed.
total_cur_bal 			|float64|The total current balance of all accounts.
open_acc_6m 			|float64|Number of open trades in last 6 months.
open_il_6m 			|float64|Number of installment accounts opened in past 12 months.
open_il_12m 			|float64|The number of installment accounts opened in the past 12 months.
open_il_24m 			|float64|Number of installment accounts opened in past 24 months.
mths_since_rcnt_il 			|float64|Months since most recent installment accounts opened.
total_bal_il 			|float64|Total current balance of all installment accounts.
il_util 			|float64|Ratio of total current balance to high credit/credit limit on all install acct.
open_rv_12m 			|float64|Number of revolving trades opened in past 12 months.
open_rv_24m 			|float64|Number of revolving trades opened in past 24 months.
max_bal_acc 			|float64|The maximum current balance owed on all revolving accounts.
all_util 			|float64|Balance to credit limit on all trades.
total_rev_hi_lim 			|float64|Total revolving high credit/credit limit.
inq_fi 			|float64|Number of personal finance inquiries
total_cu_tl 			|float64|Number of finance trades.
inq_last_12m 			|float64|The number of credit inquiries in the last 12 months.

> **Others**

|variable                       |type     |description |
|:------------------------------|:---------|:-----------|
Unnamed 			|int64|The row-index information.
policy_code 			|int64|Publicly available policy_code=1. New products not publicly available policy_code=2.
