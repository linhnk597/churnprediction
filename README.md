# churnprediction
# Churn Prediction for Customer Retention Program

This report attempts to analyze existing customer data to predict whether the customer will port out the service in order to outline the customer retention program using machine learning algorithms.

# General Information
Churn customers can directly have an adverse effect on the business’ future expected revenue. Having the ability to predict the potential churn rate of a specific customer allows the company to implement the customer retention program in an attempt to prevent them from stopping subscription. 
Recently, many service providers, mobile apps or SaaS companies invest into customer service or marketing to acquire scientific and data-driven input for preventing customer churn. This project shows how a telecom company Telco can categorize the present customers into low risk and high risk of churn.

# Technologies
Data Tool: Python- Google Colab
Analytics techniques:
Supervised Learning: Binary Classification, predict whether the customers will port out the service.
Models used: Logistic regression, Random Forest and XGBoost

# Raw Data 
customerID – Customer ID
gender – Whether the customer is a male or a female
SeniorCitizen – Whether the customer is a senior citizen or not (1, 0)
Partner – Whether the customer has a partner or not (Yes, No)
Dependents – Whether the customer has dependents or not (Yes, No)
tenure – Number of months the customer has stayed with the company
PhoneService – Whether the customer has a phone service or not (Yes, No)
MultipleLines – Whether the customer has multiple lines or not (Yes, No, No phone service)
InternetService – Customer’s internet service provider (DSL, Fiber optic, No)
OnlineSecurity – Whether the customer has online security or not (Yes, No, No internet service)
OnlineBackup – Whether the customer has online backup or not (Yes, No, No internet service)
DeviceProtection – Whether the customer has device protection or not (Yes, No, No internet service)
TechSupport – Whether the customer has tech support or not (Yes, No, No internet service)
StreamingTV – Whether the customer has streaming TV or not (Yes, No, No internet service)
StreamingMovies – Whether the customer has streaming movies or not (Yes, No, No internet service)
Contract – The contract term of the customer (Month-to-month, One year, Two year)
PaperlessBilling – Whether the customer has paperless billing or not (Yes, No)
PaymentMethod – The customer’s payment method (Electronic check, Mailed check, Bank transfer (automatic), Credit card (automatic))
MonthlyCharges – The amount charged to the customer monthly
TotalCharges – The total amount charged to the customer
Churn - whether the customer churned or not (Yes or No)
Exploratory Data Analysis:
Dataset features: 
19 predictors including: float64(2), int64(2), object(15) and target - Churn (Yes/ No)
Check distribution of Yes/ No class in the Churn target: 73.5% and 26.5% Yes
=> The dataset is not too imbalance to be needed for adjustment




Data check - clean 
2.1.Check null/empty data:
By using heatmap, there is no missing data presenting as NULL or NAN 
Checking blank values in the dataset, there exist some blank value in the column “TotalCharges” -> Imputating with the median

2.2. Check unique value in each column and those values
(gender) Unique_Value 2 ['Female' 'Male']
(Partner) Unique_Value 2 ['Yes' 'No']
(Dependents) Unique_Value 2 ['No' 'Yes']
(PhoneService) Unique_Value 2 ['No' 'Yes']
(MultipleLines) Unique_Value 3 ['No phone service' 'No' 'Yes']
(InternetService) Unique_Value 3 ['DSL' 'Fiber optic' 'No']
(OnlineSecurity) Unique_Value 3 ['No' 'Yes' 'No internet service']
(OnlineBackup) Unique_Value 3 ['Yes' 'No' 'No internet service']
(DeviceProtection) Unique_Value 3 ['No' 'Yes' 'No internet service']
(TechSupport) Unique_Value 3 ['No' 'Yes' 'No internet service']
(StreamingTV) Unique_Value 3 ['No' 'Yes' 'No internet service']
(StreamingMovies) Unique_Value 3 ['No' 'Yes' 'No internet service']
(Contract) Unique_Value 3 ['Month-to-month' 'One year' 'Two year']
(PaperlessBilling) Unique_Value 2 ['Yes' 'No']
(PaymentMethod) Unique_Value 4 ['Electronic check' 'Mailed check' 'Bank transfer (automatic)'
 'Credit card (automatic)']
(Churn) Unique_Value 2 ['No' 'Yes']

Visualization dataset:
Categorize predictors into 3 group: 
+ #Demographic information: Gender, Partner, Dependents,SeniorCitizen
+ #Service information: 'PhoneService', 'MultipleLines', 'InternetService', 'OnlineSecurity',  'OnlineBackup', 'DeviceProtection','TechSupport', 'StreamingTV', 'StreamingMovies'
+#Payment information: 'Contract','PaperlessBilling','PaymentMethod'



Splitting Data: applying train_test_split(X, y, test_size, random_state, stratify) (70% train- 30% validation)

Models and Evaluation
Logistic Regression
   precision    recall  f1-score   support

           0       0.86      0.89      0.87      1582
           1       0.62      0.56      0.59       531

    accuracy                           0.80      2113
   macro avg       0.74      0.72      0.73      2113
weighted avg       0.80      0.80      0.80      2113



Random Forest (n_estimator=100)
precision    recall  f1-score   support

           0       0.83      0.89      0.86      1582
           1       0.59      0.47      0.52       531

    accuracy                           0.78      2113
   macro avg       0.71      0.68      0.69      2113
weighted avg       0.77      0.78      0.78      2113




XGBOOST
precision    recall  f1-score   support

           0       0.86      0.89      0.87      1582
           1       0.63      0.55      0.59       531

    accuracy                           0.81      2113
   macro avg       0.74      0.72      0.73      2113
weighted avg       0.80      0.81      0.80      2113


Finding
Gender is not useful to predict the churn rate in this case
If a person has a partner, there is less chance for them to give up on the service.
If a person has dependents, there may be less chance for them to give up on the service.
If a person is a senior, It is higher chance for them to give up on the service
People with Fiber Optic Internet Service, No online security, no online backup, no device protection, no tech support have more chance to port out the service (churn)
People with no internet service are less likely to port out
Person with month-to-month payment has a much higher chance to quit the service
Person with paperless billing and electronic check has a higher chance to quit the service
 
 


 


