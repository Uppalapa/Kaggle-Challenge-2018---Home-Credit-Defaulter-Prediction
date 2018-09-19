
# Kaggle Challenge 2018 - Home Credit Defaulter Prediction
# 1. Introduction
Home credit is an international non-bank financial institution which focuses on lending primarily to people with little or no credit history. They have challeneged the Kaggles to unleash the full potential of data to predict the clients repayment ability. In this project we are trying to predict the probability that a client repays the loan using ML algorithms.
## 1.1 Data Description
### (Data Source - <a href="https://www.kaggle.com/c/home-credit-default-risk/data">DATA LINK </a> , Data Size - 3GB)
### (<a href="https://drive.google.com/open?id=13fWkR-mqlqYcG9uv1-ABebXwP7kvuH1v">DATA</a>,  <a href="https://drive.google.com/drive/folders/1FdJc3mLMc-3hTXCkW4toVBoxi0mCQ-0U?usp=sharing">OUTPUT FILE</a>)
## 1.2 About the Data
<img width="600", height="500" align="center" alt="home_credit" src="https://user-images.githubusercontent.com/42013395/45705337-2e088480-bb2e-11e8-8343-6a4937552052.png" />

* application_train/application_test: It is the main training and testing data with information about each loan application at Home Credit. Every loan is identified by the column SK_ID_CURR. Traing data set has the column Target which specifies if the loan was repaid or not. 0 indicated loan was repaid. 1 - not repaid (Bad debts) 
* Note - There are 122 columns and 400,000 rows

## 1.2 Python Packages Used
* Matplotlib
* Pandas
* Scipy
*  _psi
*  _polygamma
* _newton
* _gamma
* Sklearn
* _LabelEncoder
* _cross_val_score
* _GaussianNB
* _SelectFromModel
* _accuracy_score
* _RandomForestClassifier
* _KNeighborsClassifier
* _LogisticRegression
* _StandardScaler
* seaborne
* Lightgbm
* XGBoost
* _XGBClassifier
* _plot_importance
* OS
* pymc3

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
<img width="263"  src="https://user-images.githubusercontent.com/42013395/43896490-fc8e69de-9ba6-11e8-8ea7-edc9e5fe8762.png" />

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
Probability accury for xgboost - 92%
## 7.2 Choosing the best model
Selected XGBoost Classifier
# 8. Prediction
<img src="https://user-images.githubusercontent.com/42013395/43896491-fca404d8-9ba6-11e8-9061-bf40d07b93d2.png" width="600" height="600" align="center"  />
# 9. Conclusion
<img width="491" alt="target_edu_comp" src="https://user-images.githubusercontent.com/42013395/43896492-fcb57f9c-9ba6-11e8-8677-9a798aae588b.PNG" />
<img width="477" alt="target_housing_cmp" src="https://user-images.githubusercontent.com/42013395/43896493-fcca1a2e-9ba6-11e8-8f4b-5bb26bc6bd60.PNG" />
