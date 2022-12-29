# Fraud_analytics

CREDIT CARD
 	

SP Jain School of Global Management
28-12-2022
SUSHANTH S
VINIT DSOUZA
ADITYA VERMA	



Table of Contents
CREDIT CARD	1
INTRODUCTION	2
EXPLORATORY DATA ANALYSIS	4
TNSE Analysis	7
Anomaly Detection	9
Model Development	10
Initial Models	10
Machine learning models deployment	11
Class Imbalance Handling	11
Random Under sampling technique is deployed	12
Model-1: Logistic Regression	12
Model-2: SVM	14
Model-3: Ensemble Random Forest	15
Model-4: Ensemble XG Boost	16
References:	18
















		
INTRODUCTION
About Dataset and Objective Setting 

The dataset consists of 
Rows: 1296675
Columns: 23

Features Available for analysis
1.	Transaction date and time
2.	Credit card number
3.	Merchant
4.	Category
5.	Amount
6.	Gender
7.	Street
8.	City
9.	State
10.	Zip
11.	Latitude
12.	Longitude
13.	City population
14.	Job
15.	DOB
16.	Transaction number
17.	Unix time
18.	Merchant latitude
19.	Merchant longitude
20.	Fraud label	
The dataset upon analysis shows high class imbalance as fraudulent transactions are minor chunk of cumulative purchases.

We will focus on following sub-areas to make a concrete prediction of fraud:
I.	EDA, Preprocessing
II.	Dimensionality check using TNSE
III.	Anomaly Detection
IV.	Fraud Detection – use of Machine learning and Deep Learning techniques
Focus 

 

 	


 
		EXPLORATORY DATA ANALYSIS
 

Use all the features and understand how fraudulent transactions are different with respect to normal transactions.




 		
 



Chart-1: Fraud Cases
 

We see a class imbalance in the dataset. Only   0.6% of data is giving us fraudulent transactions.

Chart-2: Transaction time density plot
 
Transaction time for fraudulent and normal are similar. Does not infer any information on fraud happening with respect to transaction





Unix time is converted to required time format for further analysis and exploration.

Chart-3: Total amount of transaction on Fraud and Normal during hour of day
 
Most of the transactions occur after 11hrs in morning. But observer a difference in Fraudulent transaction the amount (in Rs) peaks during mid-night transactions as per the data.

Chart-4: Total number of transactions on Fraud and Normal during hour of day
 
The number of fraudulent transactions also increase during the early morning and midnight periods.







Chart-5: Box plot fraud non-fraud transactions
 

The left plot shows non-fraudulent transactions has amounts from 0 to 30,000. Whereas, fraud transactions expanded (on the right side plot) shows that amount range from 0 to 1400 only.

TNSE Analysis
TNSE is a dimension reduction technique used to map high dimensional features on to a 2D plane.
Chart 5: TNSE without normalization of data
 



In the above plot we could not differentiate fraud vs non-fraud data for any transaction. One outlier is also found in the data.

Chart-6: TNSE plot after normalization
 
Here we can see the frauds are on the edges, whereas the non-fraud data is all over the circle.

Now, let’s increase the perplexity and rerun the TNSE plot. This would give a detailed picture of fraud vs non-fraud. After removing the outlier and plotting TNSE gives the results as follows
Chart-7: TNSE with perplexity 30 with normalization without outlier
 
The final plot shows the fraud and non-fraud data have something uncommon that a machine can understand. So, we move on to analyze the anomaly of such occurrences.

Anomaly Detection
Chart-8: Number of transactions by Amount of transaction

 
We cannot ascertain any pattern to number of transactions with respect to amount. Within the range of non-fraud, fraudulent transactions are also found.

Post conversion of Unix time feature, We use the time for further anomaly analysis

Chart-9: Amount vs Time of transaction
 
Very few outliers can be seen out of the normal transaction time zone. All other fraudulent transactions can be seen to be tagged along with non-fraudulent transactions.

Model Development
Initial Models
1.	Isolation forest method results
 
Overfitted model. Predicts all the fraud and non-fraud classes exactly



2.	Local Outlier Factor method

 

There are no outliers observed. The data clearly differentiates fraud and non-fraud.

3.	Support vector machine
 
Similarly, SVM dimensionality reduction technique also gives good result for prediction of fraud vs non-fraud.

Machine learning models deployment
Class Imbalance Handling
As the data for fraud and non-fraud is highly imbalanced as below:
 
More then 5 lakh rows are non-fraud, while only 2000 rows have fraud.

Random Under sampling technique is deployed
 


Post under sampling the dataset used for machine learning model has 50% of fraud data. About 2000 rows out of new total 4000 non-fraud rows.
A chuck of data has been used for better performance of model and system limitations. With the original data set we already performed SVM model above and that gives a good result.
Now, we focus on under sampling as a technique to understand and predict fraud for a class imbalance point of view.

Model-1: Logistic Regression
 








Model Performance
 

 
Recall is very poor. So, this model doesn’t provide a good prediction power
AUC Score: 60.9%

 








Model-2: SVM


 


Model Performance:
 
 
Recall is very poor. So, this model doesn’t provide a good prediction power
AUC Score: 62.2%



 



Model-3: Ensemble Random Forest
 
Model Performance:
 
 

This ensemble model performs much better than logistic and SVM. This is evident from the TNSE plot as well. As the data is non-linear. So linear model fails.

AUC Score: 98.58%
 

The above random forest model is a perfect model that can be deployed.


Model-4: Ensemble XG Boost
 
Model Performance:
 
 
Further improvement in confusion matrix as AUC score is obtained.
AUC : 99.39%
 

Further simple multilayer perceptron model analysis is performed. But performance is sub-optimal due to simple architecture (not a deep learning model)

References:

Dataset : https://www.kaggle.com/code/nathanxiang/credit-card-fraud-analysis-and-modeling/data

Codes: No codes where available in the Kaggle links for this dataset
So, all codes in bits and pieces were taken from various sites based on the analysis we learn during the lectures and in class exercises.

















 


	
	End of Credit Card Fraud Analytics	
	


