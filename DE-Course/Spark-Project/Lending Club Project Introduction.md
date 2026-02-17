Banking/Finance - Pyspark

### Money Lending Institutions

Traditional lending institutions - Bank

Alternate lending institutes - ZestMoney, Lendbox - peer to peer, Prosper, Propelld - education, Fibe, Liquiloans, Grayquest, Eduvanz - education, lending club - peer to peer

they give loan from their side.
- institute give the loan / borrower - institute
- peer to peer / borrower ---- investor/lender

Pros - 
- less paper work
- long term loans
- low credit score we can get loan
- quick process
- hassle free

cons - 
- high interest rates
- can be risky for the investors

investors get a interest percentage (6% to 36% anually)

36 months - 60 months (repayment)

consider one of these financial institutes is your client, and they send you the data so that our data engineering team can clean it, process it and give it back to be consumed by data analytics team.

You work for a consumer finance company which specializes in lending various types of loans to urban customers. The company has to either approve or disapprove a loan based on application.

Data Engineering team should clean the data so that the other teams can use the cleaned data and also the data engineering team should calculate the risk score based on which the company can decide whether to approve or disapprove.

- If the applicant is likely to pay the loan, then not approving the loan results in business loss.
- If the applicant is not likely to repay the loan, then approving the loan may lead to financial loss to the company.

As a Data Engineer - Clean and Process - calculate credit score (certain rules)

lending club dataset - 1.7 GB CSV (kaggle) 118 columns, 2M+ records

```
from pyspark.sql import SparkSession
import getpass
username = getpass.getuser()
spark = SparkSession. \
	builder. \
	config('spark.ui.port', '0'). \
	config('spark.shuffle.useOldFetchProtocol', 'true'). \
	config('spark.sql.warehouse.dir', f'/user/{username}/warehouse'). \
	enableHiveSupport(). \
	master('yarn'). \
	getOrCreate()
```

```
raw_df = spark.read \
.format("csv") \
.option("inferSchema", "true") \
.option("header", "true") \
.load("/user/itv005857/lendingclub/accepted_2007_to_2018Q4.csv")
```

```
raw_df.createOrReplaceTempView("lending_club_data")
```

```
spark.sql("select * from lending_club_data")
```

we can divide the data into 4 tables

**customers_data (borrowers details)**
member_id, emp_title, emp_length, home_ownership, annual_inc, addr_state, zip_code, country, grade, sub_grade, verification_status, tot_hi_cred_lim, application_type, annual_inc_joint, verification_status_joint

**loans_data**
loan_id, member_id, loan_amnt, funded_amnt, term, int_rate, installment, issue_d, loan_status, purpose, title

**loan_repayments**
loan_id, total_rec_prncp, total_rec_int, total_rec_late_fee, total_pymnt, last_paymnt_amnt, last_paymnt_d, next_paymnt_d

**loan_defaulters**
member_id, delinq_2yrs, delinq_amnt, pub_rec, pub_rec_bankruptcies, inq_last_6mths, total_rec_late_fee, mths_since_last_delinq, mths_since_last_record

