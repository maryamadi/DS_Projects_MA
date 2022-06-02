<img src="https://engineering.nyu.edu/sites/default/files/styles/embed_default_1x/public/2020-07/shutterstock_cybersecurity.jpg?h=68afcf76&itok=Tgb7prNY" width="90%" height="40%">

### Fraud Detection Model for E-Commerce Companies
 
According to Juniper's research, "E-commerce retailers are at risk of losing over **20 billion USD in 2021** due to online fraudulent activities" (Trivedi, 2021). This represents a staggering 18% of the increase in digital crime as compared to 2020. 

Many E-Commerce companies are struggling to streamline their security systems to ensure their online transactions are based on verified consumer identities. Which makes identity and synthetic fraud among the most common types of online criminal activity. Fraudsters use stolen identity data (like Social Security numbers, addresses, and card details) to create a synthetic ID and steal funds from accounts, take out loans, or create new credit lines in the name of the customer (Trivedi, 2021).  


To address this issue I will create a fraud detection model for the E-Commerce Company that will help smaller E-Commerce companies identify potentially fraudulent customers and transactions based on the digital footprint revealed by the analyzed dataset.

## 1. Data

The Datasets consist of 2 CSV files both containing information on eCommerce transactions made by customers.

File 1: Customer_DF (1).csv (25.6 kB) File has 10 columns and 167 entries

File 2: cust_transaction_details (1).csv(55.67 kB) File has 11 coulmns and 622 entries

Data Source: https://www.kaggle.com/datasets/aryanrastogi7767/ecommerce-fraud-data

The Fraud Detection Model will be developed by performing proper EDA and feature engineering.

## 2. Data Cleaning

*Data Cleaning Report*

The original data set was comparably clean with no duplicated or missing data.  
I had to reshape & merge data from two separate tables to align customer information with transactions data to train my model on a variety of different customer data.

- **Problem 1:** Customer email was identified as a primary key for data merge. There is a total of 168 entries and just 161 unique email addresses. To ensure the data integrity, I had to verify if there are any customer e-mail duplicates associated with different customer data (i.e. IP address, billing address, email, and phone number)

- **Solution:** To find duplicated emails I have created a for loop to check for duplicates and save duplicated emails in a list of duplicates.  
 I was able to identify 'johnlowery@gmail.com' as a duplicated email address, which was marked as a Fraud in the transactions dataset. 
 
- **Problem 2:** All address data were concatenated in one column, so I had to separate State data, to verify if there are any geographically concentrated fraud cases. 
  
- **Solution:** Used str.split() function to separate States, and created new df.States column. 

## 3. EDA

*EDA Report*

- Preliminary EDA revealed that out of a total of 2615 orders 9.83% were detected as being fraudulent. However, out of 623 transactions, 41.25% were marked as fraud.

- Payment method provider analysis revealed that payments made using 16-digit JCB and Visa cards were less likely to detect fraud fulfilling the majority of the fraudulent orders. 

- Additionally, a barplot below shows the likelihood of all payment attempts above 4 resulting in Fraud.  

<img src="https://github.com/maryamadi/DS_Projects_MA/blob/main/Capstone_Two_Ecommerce_Companies_Fraud_Detection/Notebooks/FraudFreqPlot.jpg?raw=true" width="90%" height="40%">

- The analysis of the geographic spread of Fraudulent activity revealed that 11% of all detected cases originated in Wisconsin, followed by 8% in the Marshall Islands and 6% in Louisianna. 

<img src="https://github.com/maryamadi/DS_Projects_MA/blob/main/Capstone_Two_Ecommerce_Companies_Fraud_Detection/Notebooks/newplot%20(1).png?raw=true" width="90%" height="40%">

- The box plot below shows a distinct difference in the mean and distribution of orders between fraudulent and valid cases. 

<img src="https://github.com/maryamadi/DS_Projects_MA/blob/main/Capstone_Two_Ecommerce_Companies_Fraud_Detection/Notebooks/FraudBoxPlot.jpg?raw=true" width="90%" height="40%">

## 4. Preprossesing and Training Data Development 

- Preprocessing portion of this project involved the creation of the dummy variables to prepare categorical features for modeling. According to the scaled correlation matrix, the highest dependencies were detected between Fraud and the Number of Orders (0.45), Number of Payments (0.33), and Transaction Amount (0.33).


## 5. Data Modeling

ML Notebook

I chose to work with supervised learning machines, as I am not performing an exploratory analysis but building my model using historical data. I have used Logistic Regressor, Random Forest Classifier, and Support Vector Machine-based models.   


NOTE: I choose the confusion matrix as the accuracy score metric. 

WINNER: Random Forest Classifier with accuracy precision of 86%, recall of 0.83, and F1 score of 0.85

## 6.References:

 *References* 
 
Trivedi, V., I., & Trivedi, V. (2021, April 30). E-commerce fraud to surpass $20B in 2021, an 18% jump over last year, report finds. Payments Dive. https://www.paymentsdive.com/news/e-commerce-fraud-to-hit-20-billion-2021-an-18-jump-from-prior-year/599312/



© 2022 GitHub, Inc.
Terms
Privacy
Security
Status
Docs
Contact GitHub
Pricing
API
Training
Blog
About
