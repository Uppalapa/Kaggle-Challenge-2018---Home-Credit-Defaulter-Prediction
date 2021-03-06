
# Kaggle Challenge 2018 - Home Credit Defaulter Prediction
<img width="250" height="200" align="right" src="https://user-images.githubusercontent.com/25045759/45790092-056cb180-bc38-11e8-82cc-5185448f4a53.png">

# 1. Introduction
Home credit is an international non-bank financial institution which focuses on lending primarily to people with little or no credit history. They have challeneged the Kagglers to unleash the full potential of data to predict the clients repayment ability. In this project we are trying to solve the binary classification problem using 6 different classifiers, compare thier prediction accuracies and predict the probability that a client repays the loan using ML algorithms.

## 1.1 Problem Statement
* Many people struggle to get loans due to insufficient or non-existent credit histories. And, unfortunately, this population is often taken advantage of by untrustworthy lenders.
* Home Credit strives to broaden financial inclusion for the unbanked population by providing a positive and safe borrowing experience. 

*  In order to make sure this underserved population has a positive loan experience, they have to ensure clients that are capable of 
repayment are not rejected and that loans are given with a principal, maturity, and repayment calendar that will empower their clients to be successful.
* Predicting whether or not a client will repay a loan or have difficulty is a critical business need.
## 1.2 Data Description
### (Data Source - <a href="https://www.kaggle.com/c/home-credit-default-risk/data">DATA LINK </a> , Data Size - 3GB)
### Project Data link - <a href="https://drive.google.com/open?id=13fWkR-mqlqYcG9uv1-ABebXwP7kvuH1v">DATA</a>
## 1.3 About the Data
<img width="700" height="500" align="center" alt="home_credit" src="https://user-images.githubusercontent.com/42013395/45705337-2e088480-bb2e-11e8-8343-6a4937552052.png">

* application_train/application_test: It is the main training and testing data with information about each loan application at Home Credit. Every loan is identified by the column SK_ID_CURR. Traing data set has the column Target which specifies if the loan was repaid or not. 0 indicated loan was repaid. 1 - not repaid (Bad debts) 
* Note - There are 122 columns and 400,000 rows

## 1.4 Python Packages Used

<img width="700" height = "300" align="center" alt="packagenames" src="https://user-images.githubusercontent.com/25045759/45779873-18b85680-bc11-11e8-8275-3101afca69d1.PNG">

## 1.5 Project workflow

<img width="522" alt="workflow" src="https://user-images.githubusercontent.com/25045759/45781126-07247e00-bc14-11e8-9dcc-15ecc4e1e12d.PNG">

# 2. Exploratory Data Analysis
EDA helps us to make inferences from the data so that we can decide the features to use for modelling data. It generally starts out with a high level overview, then narrows in to specific areas as we find intriguing areas of the data.

### Pearson correlation plot
![corr_heatmap](https://user-images.githubusercontent.com/42013395/43896486-fc49b00a-9ba6-11e8-822d-9c4d08fd96b1.png)
* Found the positvely and negatively correlated columns with the target so that we can select the piority columns and eliminate the least important columns
* Sorted the correlation values
* Eliminated the least important columns

In this plot yellow lines indicate loans that are not repaid and blue indicates the loans that are paid. We can observe a positive linear relationship between EXT_SOURCE_1 and YEARS_BIRTH indicating that these columns can be considered as important features for Target prediction
![corr_diag_kde_heatmap](https://user-images.githubusercontent.com/42013395/45706124-4aa5bc00-bb30-11e8-83d6-fe1aa1c8452f.png)

Explored the % of unpaid loans by the following categories 
1 - Eductation Type
![of loans unpaid by name_education_type](https://user-images.githubusercontent.com/42013395/43896481-fbf1a914-9ba6-11e8-84ff-0baf0fb64ac8.png)
2 - Housing Type
![of loans unpaid by name_housing_type](https://user-images.githubusercontent.com/42013395/43896483-fc11184e-9ba6-11e8-9dbc-b6f43903150c.png)
3 - Occupation Type
![of loans unpaid by occupation_type](https://user-images.githubusercontent.com/42013395/43896484-fc23c7f0-9ba6-11e8-9a26-8e1c77402912.png)
4 - Organization
![of loans unpaid by organization_type](https://user-images.githubusercontent.com/42013395/43896485-fc3575a4-9ba6-11e8-816f-827e79da4d7f.png)

# 3. Missing Data Observations
Given data has a lot of missing values. Analysed the % of missing values in each column

<img width="800" height = "600"  src="https://user-images.githubusercontent.com/42013395/43896490-fc8e69de-9ba6-11e8-8ea7-edc9e5fe8762.png">

# 4. Handling Missing Data
Handeled both test and train data
* Replaced missing float values using mean
* Replaced missing string values using mode

# 5. Plot posterior - MLE & MCMC
Implemented MCMC and MLE algorithms to find the mean value of the number of years a borrower takes to close the credit account

#### MLE -
<img width="263" src="https://user-images.githubusercontent.com/42013395/43910771-b97623c4-9bcb-11e8-8200-3d8e9a89775c.PNG"/>

#### MCMC -
<img width="263" src="https://user-images.githubusercontent.com/42013395/43910772-b983574c-9bcb-11e8-9b95-9a2dd9f3fc5c.PNG"/>

# 6. Feature Importance
### 6.1 XGB Classifier
<img src="https://user-images.githubusercontent.com/42013395/43896487-fc587194-9ba6-11e8-9ce5-059730d36072.png" width="600" height="600" align="center"/>

### 6.2 Light gbm
<img width="600" height="600" src="https://user-images.githubusercontent.com/42013395/43896489-fc7d2aca-9ba6-11e8-8854-7426c5e2c071.PNG" />

# 7. Modelling
## 7.1 Model Accuracy Comparision
<img width="600" height = "600" alt="accuracy" src="https://user-images.githubusercontent.com/25045759/45781137-0d1a5f00-bc14-11e8-8711-c3f20223f663.PNG">

Probability accury for xgboost is the highest of all - 92%

## 7.2 Choosing the best model
* Selected XGBoost Classifier and modelled train data
* Applied this classifier to predict the TARGET Values of test data 
* The result of the predictor from 0 to 1 indicates probability that the loan will be repaid
* Considering the trend in train data we have chosen a threshold value and categorized the target values to 0 and 1
* Concatenated the target column to the test dataset

# 8. Prediction
<img width="700" height="600" alt="predictions" src="https://user-images.githubusercontent.com/25045759/45789876-df92dd00-bc36-11e8-8ac0-c4406111de53.PNG">

* Used predict_proba method to predict the target values based on train data values
* Considering the trend in train data we have chosen a threshold value and categorized the target values to 0 and 1
* Concatenated the target column to the test dataset

# 9. Conclusion
* Used 6 different classifiers and compared their prediction scores
* Improved the prediction accuracy up to 92.021 %  by applying feature importance on test data
* Modelled the training data using XGBoost classifier and predicted target values on test data
* Predicting the probability that each client (borrower) in the test data repays the loan
* Obtained satisfactory results when compared the test results with train data
<img src="https://user-images.githubusercontent.com/42013395/43896491-fca404d8-9ba6-11e8-9061-bf40d07b93d2.png" width="600" height="600" align="center">

<img width="700" height="600" align="center" alt="p1" src="https://user-images.githubusercontent.com/25045759/45781111-012e9d00-bc14-11e8-9220-7a33d0bd68ab.PNG">

<img width="700" height="600" align="center" alt="p2" src="https://user-images.githubusercontent.com/25045759/45781112-012e9d00-bc14-11e8-8f3c-ca0754703b5e.PNG">

<img width="700" height="600" align="center" alt="p3" src="https://user-images.githubusercontent.com/25045759/45781114-01c73380-bc14-11e8-9fd4-98f841abf0cd.PNG">

##  <a href="https://drive.google.com/drive/folders/1FdJc3mLMc-3hTXCkW4toVBoxi0mCQ-0U?usp=sharing">OUTPUT FILE</a>
