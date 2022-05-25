<img src="https://engineering.nyu.edu/sites/default/files/styles/embed_default_1x/public/2020-07/shutterstock_cybersecurity.jpg?h=68afcf76&itok=Tgb7prNY" width="90%" height="40%">

### Fraud Detection Model for E-Commerce Companies

According to Juniper research, "E-commerce retailers are at risk of losing over **$20 billion USD in 2021** due to online fraudulent activities' (Trivedi, 2021). This represents a staggering 18% of increase in digital crime as compared to 2020. 

Many E-Commerce companies are struggling to streamline their security systems to ensure their online transactions are based on verified consumer identity. Which makes identity and synthetic fraud among the most common types of online criminal activity. Fraudsters use stolen identity data (like Social Security numbers, addresses and card details) to create a synthetic ID and steal funds from accounts; take out loans; or create new credit lines in the name of the customer (Trivedi, 2021). 

For this project I will create a fraud detection model for the E-Commerce Company that will help cyber security team to identify potentially fradulent customers and transactions.

## 1. Data

This Datasets consists of 2 csv files both containing information on ecommerce transactions made by customers.

File 1: Customer_DF (1).csv (25.6 kB) File has 10 columns and 167 entries

File 2: cust_transaction_details (1).csv(55.67 kB) File has 11 coulmns and 622 entries

Data Source: https://www.kaggle.com/datasets/aryanrastogi7767/ecommerce-fraud-data

The Fraud Detection Model will be develpoed performing proper EDA and feature engineering.

## 2. Data Cleaning

*Data Cleaning Report*

The original data set was comparably clean with no duplicated or missing data.  
I had to reashape & merge data sets for two tables to align customer information with transctions data to train my model on a variaetly of different customer data.

- **Problem 1:** Customer email was identified as a primary key for data merge. There are total 168 entries and just 161 unique emails addresses. To ensure the data integrity, I had to verify if there there are any customer e-mail duplicates associated with different customer data (i.e. IP address, bulling address, customer device and phone number)

- **Solution:** To find duplicated emails I have created a for loop to check for duplicates and save duplicated emails in a list of duplicates.  
 I was able to identify 'johnlowery@gmail.com' as a duplicated email address, which was marked as a Fraud in trandactions dataset. 
 
- **Problem 2:** Address data is adrtess data is concatenated in one column, so I had to sperate State data, to verify if there is any geographically concentrated fraud cases. 
-   
- **Solution:** Used str.split() function to separate States, and created new df.States column. 


## 4. EDA

*EDA Report*




## 5. Algorithms & Machine Learning
ML Notebook

I chose to work with the Python surprise library scikit for training my recommendation system. I tested all four different filtered datasets on the 11 different algorithms provided, and every time the Single Value Decomposition++ (SVD++) algorithm performed the best. It should be noted that this algorithm, although the most accurate is also the most computationally expensive, and that should be taken into account if this were to go into production.



NOTE: I choose RMSE as the accuracy metric over mean absolute error(MAE) because the errors are squared before they are averaged which gives the RMSE a higher weight to large errors. Thus, the RMSE is useful when large errors are undesirable. The smaller the RMSE, the more accurate the prediction because the RMSE takes the square root of the residual errors of the line of best fit.

WINNER: SVD++ Algorithm

This algorithm is an improved version of the SVD algorithm that Simon Funk popularized in the million dollar Netflix competition that also takes into account implicit ratings (yj). Using stochastic gradient descent (SGD), parameters are learned using the regularized squared error objective.



## 7. Feature Engineering 


It is my hypothesis that the initial filtering of the routes is what affected the RMSE of the users

Increasing the user threshold to 5 would increase the RMSE by .005 & would lose approximately 40% of the data.
Increasing the user threshold to 13 would increase the RMSE by .0075 & would lose approximately 60% of the data
If there were a larger increase in the RMSE (>= .01) I would trade my users' data for this improvement. However, these improvements are too minuscule to give up 40%-60% of my data to train on. Instead, I voted to keep some of these outliers to help the model train, and will focus on fine tuning my parameters using gridsearch to improve the RMSE

## 7. Predictions

Final Predictions Notebook

In the final predictions notebook, the user can enter their user_id number and receive a list of top ten routes recommended to them:


## 8. Future Improvements
In the future, I would love to spend more time creating a filtering system, wherein a climber could filter out the type, difficulty of climb, & country before receiving their top ten recommendation

This recommendation system could also be improved by connecting to the 8a.nu website so that the user could input their actual online ID instead of just their user_id number

Due to RAM constraints on google colab, I had to train a 65% sample of the original 6x dataset. Without resource limitations, I would love to train on the full dataset. Preliminary tests showed that the bigger the training size, the lower the RMSE. One test showed an increase in sample size could increase the RMSE by .03 (in contrast to the .005 improvement I received when increasing the coldstart threshold)

## 9. Credits and  References:

Trivedi, V., I., & Trivedi, V. (2021, April 30). E-commerce fraud to surpass $20B in 2021, an 18% jump over last year, report finds. Payments Dive. https://www.paymentsdive.com/news/e-commerce-fraud-to-hit-20-billion-2021-an-18-jump-from-prior-year/599312/

Thanks to DJ Sarkar for being an amazing Springboard mentor.


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
