# Credit-card-Approval-Prediction
Crdit-card will be approved or not. 

Detailed Description:
Capstone Project Report 
Credit card approval prediction 

Q1: Why is your proposal important in today’s world? How predicting a good client is worthy for a bank?   

The proposal to predict credit card approval is highly relevant in today's world due to the increasing use of credit cards as a financial tool. With the rise in e-commerce and online transactions, credit cards have become a primary payment method for many individuals, making it essential for banks to efficiently process credit card applications and improve the approval rate. Predicting a good client is essential for a bank because it helps to minimize the risk of credit default and reduce the cost of managing credit card accounts. Banks can use machine learning algorithms to analyze various factors such as income level, employment status etc. By accurately predicting, banks can offer credit cards to clients with lower risk profiles, which can ultimately lead to better profitability and improved customer satisfaction.

Q2: How is it going to impact the banking sector?
predicting credit card approval using machine learning can have a transformative impact on the banking sector by improving the customer experience, reducing risk, and increasing profitability.
Improved customer experience: By using predictive models, banks can offer faster and more accurate credit card approvals, which can improve the overall customer experience. This can lead to increased customer satisfaction and loyalty.
Reduced risk of credit defaults: Machine learning algorithms can help banks to accurately predict the likelihood of a client defaulting on their credit card payments. By identifying clients with lower credit risk profiles, banks can offer credit cards with lower interest rates, which can reduce the risk of defaults and ultimately improve the bank's profitability.
Improved profitability: By reducing the risk of credit defaults and improving the efficiency of the underwriting process, banks can increase their profitability. This can help banks to offer better rates and benefits to their clients, leading to increased market share and revenue.

Q3: If any, what is the gap in the knowledge or how your proposed method can be helpful if required in future for any bank in India.
If there is a gap in the knowledge or process used by a bank in India for credit card approval, the proposed method can be helpful for banks in India by improving the accuracy of credit card approval predictions, enhancing credit risk management strategies, and improving efficiency. However, to fully leverage the benefits of our proposed method, banks will need to ensure that they have access to reliable and comprehensive data sources.




We have merged the data set with in order to get the individual and target variable in single table: 

# Reading the CSV files:
import pandas as pd
import numpy as np
#pip install pandas

# Load the dataset into a pandas DataFrame
Credit_card = pd.read_csv('Credit_card.csv')
Credit_card_label = pd.read_csv('Credit_card_label.csv')


#Merging both files 
# Merging the two dataset
Creditcard_dataset= pd.merge(Credit_card,Credit_card_label,on='Ind_ID',how='inner')

# Making a copy of dataset for further processing 
creditcard = Creditcard_dataset.copy()
creditcard.head()

Data Cleaning and preprocessing: 
   

 

 

 
   
 
 

 

 

 
 
   

EDA

 

 
     

 
Removing outliers 
 

 

Rechecking graphs after removing outliers 
 

ML Models : 
 
 
         

   
 

     
 

   
 

conclusion
Hence we got accuracy on different classification
-logisitic regression got accuracy 88%
-SVM accuracy 88%
-xg boosting got accuracy 91%
-Random Forest got accuracy 90%
we have done all the elementry EDA steps needed and plotted various graphs to determine the correlation among the independent variables and also between the independent and dependent variable.
After feature selection we used four machine learning models and achieved quite good accuracy 91% in XG boosting for predicting the credit card approval.

SQL Question:
SELECT * FROM creditcard.creditcardone;


##1.	Group the customers based on their income type and find the average of their annual income.
select avg(Annual_income), Type_Occupation From creditcard.creditcardone Group BY Type_Occupation;

##2.	Find the female owners of cars and property.
Select Car_Owner, Propert_Owner, GENDER, Ind_ID from creditcard.creditcardone Where GENDER = 'F' and Car_Owner= 'Y' and Propert_Owner= 'Y';

##3.	Find the male customers who are staying with their families.
select GENDER, Housing_type, Ind_ID from creditcard.creditcardone Where GENDER = 'M'and Housing_type= 'With parents';

## 4.	Please list the top five people having the highest income.
select MAX(Annual_income), Ind_ID from creditcard.creditcardone group by Ind_ID limit 5; 

## 5.	How many married people are having bad credit?
Select Marital_status, label, Ind_ID from creditcard.creditcardone 
Where Marital_status= 'Married' and label= 0;

## 6.	What is the highest education level and what is the total count?
select Count(EDUCATION), EDUCATION from creditcard.creditcardone 
where EDUCATION= 'Higher education';

## or ## 

select Count(EDUCATION), EDUCATION from creditcard.creditcardone 
group by EDUCATION ;

## 7.	Between married males and females, who is having more bad credit? 
select Count(label), GENDER, Marital_status from creditcard.creditcardone
where Marital_status = 'Married' 
group by GENDER;

Done and created By: 
Divya Pareek
