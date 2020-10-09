# Credit-Card-Fraud-Detection

This was the final project for BUDT758X (Data Processing and Analysis in Python) course.

## Introduction

With the emergence of cashless economies and a significant rise in the number of online transactions, credit cards have become the norm. Unfortunately, with this growth in the usage of credit cards, the chances of fraud and consequently the amount of losses have also increased drastically. Statistics show that credit card fraud losses may climb to as much as $10 billion in the United States alone by 2020.

This project focuses on analyzing transaction data to infer some meaningful insights about card fraud. The motivation for this analysis stems from the need to come up with better strategies to promote a safer economy. Though EMV chip cards make payments relatively safer, experts predict fraud will still remain a major concern in the future. If the existing data is not analyzed, it will be extremely difficult to decode fraud methodologies and in turn, almost impossible to adopt counter measures and promote a secure environment for transactions.

## Dataset Description

It is often difficult to find data related to credit card transactions online because of the sensitive nature of such information. Therefore, we obtained a synthetic dataset, generated by a simulator called PaySim.

PaySim used real transactions implemented in an African country. Logs to create the dataset were provided by a multinational company later malicious behaviour was injected in it. This synthetic dataset was scaled down to 1/4 of the original dataset and is available on the open source website, Kaggle.

It has the following attributes:

* step - maps a unit of time in the real world. In this case 1 step is 1 hour of time. Total steps are 744 (30 days of simulation).
* type - represents the type of transaction (CASH-IN, CASH-OUT, DEBIT, PAYMENT and TRANSFER).
* amount - amount of the transaction in the local currency.
* nameOrig - name of the customer who started the transaction.
* oldbalanceOrg - initial balance before the transaction.
* newbalanceOrig - new balance after the transaction.
* nameDest - name of the customer who is the recipient of the transaction.
* oldbalanceDest - initial balance recipient before the transaction.
* newbalanceDest - new balance recipient after the transaction.
* isFraud - transactions made by the fraudulent agents inside the simulation.
* isFlaggedFraud - to control massive transfers from one account to another illegal attempts are flagged.

## Data processing Tasks

We have performed a number of data processing tasks throughout the notebook, to progressively increase the quality of our analyses.

### 1. The data set was highly unbalanced, with a large number of observations for legitimate transactrions (6,354,407) and very few observations (8213) for fraudulent transactions.Considering the huge size of the dataset, we chose to undersample the majority class using the resample module from sklearn.utils.

### 2. In order to obtain a better visualization of the relationship between the amount feature and class of the transactions, we divided the data into bins using qcut on amount. We classified each amount into a low, medium, or high amount bin.

### 3. As mentioned earlier, data was provided for 30 days or 744 steps where each step represented an hour of time. To analyze the relationship between transaction class and the time of day, we assigned each transaction an hour of the day (between 0 and 23). Since there are 24 hours in a day, we achieved this by dividing the corresponding step by 24.

### 4. As is observed later, certain transactions had virtually zero instances of fraud. In order to obtain improved accuracy for the machine learning algorithms, we subsequently removed certain types of transactions (CASH_IN, DEBIT, PAYMENT) which were skewing our results.
