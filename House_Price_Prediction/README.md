# Advanced Regression Assignment ML2- House Price Prediction
### Problem Statement :

A US-based housing company named Surprise Housing has decided to enter the Australian market. 
The company uses data analytics to purchase houses at a price below their actual values and flip them at a higher price. The 
company wants to know 

* Which variables are significant in predicting the price of a house, and
* How well those variables describe the price of a house.

For the same purpose, the company has collected a data set from the sale of houses in Australia. The company is looking at prospective properties to buy to enter the market.

### Business Goal :

* Build a regression model using regularisation in order to predict the actual value of the prospective properties and decide whether to invest in them or not.
* This model will then be used by the management to understand how exactly the prices vary with the variables
* They can accordingly manipulate the strategy of the firm and concentrate on areas that will yield high returns.
* The model will be a good way for the management to understand the pricing dynamics of a new market.


### Approach:

1.   Importing modules, Reading the data
2.   Analyzing Numerical Features
    *   Checking Statistical summary
    *   Checking Distribution of numerical features
    *   Outlier Treatment
    *   Inspecting Correlation
    *   Missing Value Handling
    *   Extracting new features and drop redundant ones
    *   Correcting datatype
    *   Univaritate and Bivariate Analysis, Data Visualization
3.  Analyzing Categorical Features
    *   Missing Value Handling
    *   Encoding Categorical Features
    *   Data Visualization
    *   Dropping Redundant Features
4.  Splitting data into Train and Test data
    *   Transformation of Target Variable
    *   Imputing Missing Values
    *   Feature Scaling
5.  Primary Feature Selection using RFE
6.  Ridge Regression
7.  Lasso Regression
8.  Comparing model coefficients
9.  Model Evaluation 
10. Choosing the final model and most significant features.


#### Ridge Regression
- Optimum alpha for Ridge is 10.000000
- Ridge Regression with 10.0

===================================
* R2_score (train) : 0.9099792685238111
* R2_score (test) : 0.8987501807731075
* RMSE (train) : 0.11987714672785361
* RMSE (test) : 0.12680116170772152

***Comment:*** Ridge regression model was able to acheieve R2 score of 0.89875 on the test data i.e. 89.88% of the variance in test data can be explained by the model. Root Mean Square Error = 0.1268 on test data, that means the prediction made by the model can off  by 0.1268 unit.

#### Lasso Regression
Optimum alpha for lasso is 0.001000

Lasso Regression with 0.001

===================================
* R2_score (train) : 0.9092384262190387
* R2_score (test) : 0.8992035193146645
* RMSE (train) : 0.12036941161238388
* RMSE (test) : 0.1265169718517261

***Comment:*** Lasso regression model was able to acheieve R2 score of 0.8992 on the test data i.e. 89.92% of the variance in test data can be explained by the model. Root Mean Square Error = 0.1265 on test data, that means the prediction made by the model can off  by 0.1265 unit.

#### Final Model
* Lasso Regression produced slightly better R2 score than Ridge Regression. Choosing Lasso as the final model.

### Conclusion

- First the housing data is read and analyzed dividing the features into numerical and categorical types.


- SalePrice is the target column here.


- All the features are then analyzed, missing data handling, outlier detection, data cleaning are done. Trend of SalePrice is 
observed for change in individual features.


- New features are extracted, redundant features dropped and categorical features are encoded accordingly.


- Then the data in split into train and test data and feature scaling is performed.


- Target variable SalePrice is right skewed. Natural log of the same is Normal distributed, hence for model building, natural log of SalePrice is considered.


- Creating dummy variables increased the number of features greatly, highly imbalanced columns are dropped.


- Top 45 features are selected through RFE and adjusted R-square. 45 features : 
['MSSubClass', 'LotArea', 'LandSlope', 'OverallQual', 'OverallCond', 'YearBuilt', 'YearRemodAdd', 'BsmtExposure', 'BsmtFinSF1', 'BsmtFinType2', 'BsmtUnfSF', 'HeatingQC', 'CentralAir', '1stFlrSF', '2ndFlrSF', 'BsmtFullBath', 'FullBath', 'HalfBath', 'KitchenQual', 'Functional', 'FireplaceQu', 'GarageFinish', 'GarageArea', 'GarageQual', 'MSZoning_RL', 'LotConfig_CulDSac', 'Neighborhood_Edwards', 'Neighborhood_NridgHt', 'Neighborhood_Somerst', 'Condition1_Norm', 'BldgType_TwnhsE', 'Exterior1st_HdBoard', 'Exterior1st_Plywood', 'Exterior1st_Wd Sdng', 'Exterior2nd_Wd Sdng', 'MasVnrType_BrkFace', 'MasVnrType_None', 'MasVnrType_Stone', 'Foundation_PConc', 'GarageType_Attchd', 'GarageType_Detchd', 'GarageType_Not_applicable', 'SaleType_New', 'SaleCondition_Normal', 'SaleCondition_Partial']


- Ridge and Lasso Regression Model are built with optimum alpha calculated in GridSearchCV method.
Optimum alpha = 10.0 for ridge and 0.001 for lasso model.


- Model evaluation is done with R2 score and Root Mean Square Error.


- Lasso Regression is chosen as final model for having slightly better R-square value on test data.


- Out of 45 features in the final model, top 10 features in order of descending importance are ['1stFlrSF', '2ndFlrSF', 'OverallQual', 'BsmtFinSF1', 'OverallCond','LotArea', 'MSZoning_RL', 'SaleCondition_Normal', 'Condition1_Norm','SaleType_New']

   - 1stFlrSF	0.121192
   - 2ndFlrSF	0.110654
   - OverallQual	0.088439
   - BsmtFinSF1	0.047700
   - OverallCond	0.044622
   - LotArea	0.032116
   - MSZoning_RL	0.027356
   - SaleCondition_Normal	0.026485
   - Condition1_Norm	0.024909
   - SaleType_New	0.024793


- Model coefficients are listed in a table along with the corresponding features , for example natural log of SalePrice will change by 0.121192 with unit change in the feature '1stFlrSF' when all the features remain constant. Negative sign in the coefficient signifies negative correlation between the predictor and target variable. 


- Predicted value of SalePrice is tranformed into its original scale by performing antilog. 



