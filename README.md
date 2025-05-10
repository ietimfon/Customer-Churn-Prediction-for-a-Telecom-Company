# Customer-Churn-Prediction-for-a-Telecom-Company
This project aims to predict customer churn for a telecom company using machine learning models. It involves data cleaning, exploratory data analysis (EDA), feature engineering, and building three classification models. The best-performing model is deployed for churn prediction on new data.
________________________

## Table of Contents
- [Project Objectives](#project-objectives)
- [Dataset Overview](#dataset-overview)
- [Technologies Used](#technologies-used)
- [Workflow Summary](#workflow-summary)
- [Machine Learning Models](#machine-learning-models)
- [Model Evaluation](#model-evaluation)
- [Feature Importance](#feature-importance)
- [Model Deployment](#model-deployment)
- [Key Insights](#key-insights)
- [Recommendations](#recommendations)
- [Conclusion](#conclusion)

### Project Objectives
1. Identify key drivers of customer churn.
2. Build and evaluate multiple classification models.
3. Select the best-performing model based on evaluation metrics.
4. Save and deploy the final model for use on new customer data.

### Dataset Overview
The dataset contains information about telecom customers, including usage statistics, subscription details, demographic information, and churn labels.

|Customer Status:||
|----------------|------|
|Customer ID|The unique ID that identifies a customer|
|Churn Label|Contains 'Yes' or 'No' to indicate if a customer churned|
|Churn Category|Groups multiple churn reasons together for analysis purpose|

|Demographics:||
|-------------|---|
|Gender|The gender of the customer, indicated by 'Male', 'Female', or 'Prefer not to say'|
|Under 30|Indicates if the customer is under 30 with 'Yes' or 'No'|
|Senior|Indicates if the customer is above 65 with 'Yes' or 'No'|
|Age|The age of the customer|

|Contract Information:||
|-------------|---|
|Contract Type|Contains 'Month-to-Month', 'One Year', or 'Two Year'|
|Payment Method|Preferred payment method of the customer indicated with 'Credit Card', 'Direct Debit', or 'Paper Check'|
|State|The code of the state where the customer lives|
|Phone Number|Phone number of the customer|
|Group|Indicates if the customer is part of a group contract. A group contract offers advantages and is generally cheaper. Contains 'Yes' or 'No'|
|Number of customers in a group|Number of customers part of the group|

|Subscription Types and Charges:||
|----------|--------|
|Account Length (in months)|The number of months the customer has been with the company|
|Local Calls|Amount of local (within the country) calls from the customer|
|Intl Calls|Amount of international (outside the country) calls from the customer|
|Intl Mins|The number of minutes spent calling internationally|
|Intl Active|Indicates if the customer called internationally with a 'Yes' or 'No'|
|Extra International Charges|Contains the extra charges for international calls for customers who are not on an international plan|
|Customer Service Calls|The number of calls maade to customer service|
|Avg Monthly GB Download|Contains the average monthly download volume in gigabytes|
|Unlimited Data Plan|Indicates if the customer has a free unlimited download capacity with 'Yes' or 'No'. This premium is reflected in the amount of the monthly charge|
|Extra Data Charges|Contains the extra charges for data downloads for customers who are not on an unlimited plan|
|Monthly Charges|Average of all Monthly Charges to the customer|
|Total Charges|Sum of all monthly charges|

### Technologies Used
- Microsoft PowerBI
- Python (Pandas, NumPy, Matplotlib, Seaborn)
- Scikit-learn (Model building, preprocessing, evaluation)
- Imbalanced-learn (SMOTE)
- YData Profiling (Data profiling)
- Joblib (Model serialization)

### Workflow Summary

#### 🔍 Data Exploration
- Imported dataset and inspected shape, types, and unique values.
- Generated summary statistics and a Pandas Profiling report.

#### 🧹 Data Cleaning
- Removed unnecessary columns like 'Phone Number', 'Customer Service Calls'.
- Confirmed no null values and no duplicates.

#### 📊 Exploratory Data Analysis (EDA)
- Churn rate: ~27%.
- Grouped churn by age, gender, plan types, and contract type.

#### 📊 Data Visualization
Built an interactive dashboard displaying:
- Top reasons for churn.
- Distribution of churn category.
- Geographic analysis of churn rate.
- Demographic analysis of churn.
- Contracts/consumption analysis of churn.

### Machine Learning Models
Three classification models were trained and evaluated:

1. Logistic Regression
2. Support Vector Machine (SVM)
3. Random Forest Classifier

#### ⚙️ Preprocessing
- One-hot encoding for categorical variables.
- Standard scaling for numeric features.
- SMOTE oversampling to address class imbalance.
- Pipelines built using ImbPipeline from imblearn.

### Model Evaluation
|Model	Accuracy|ROC AUC|F1 Score (Churn=1)|Recall (Churn=1)|
|-----|-----|-----|-----|
|Logistic Regression|0.77|0.868|0.65|0.82|
|SVM|0.79|0.8725|0.67|0.81|
|Random Forest|0.81|0.8732|0.67|0.70|

✅ Selected Model: Random Forest Classifier

### Feature Importance
The top drivers of churn identified by the model include:
- Contract Type
- Total Charges
- Payment Method
- Monthly Charge
- Unlimited Data Plan
- International Plan

### Model Deployment
- 🔹 The best model was saved using joblib:
`joblib.dump(best_model, 'best_churn_model.pkl')`
- 🔹 Ready for integration into a web or batch prediction pipeline.

### Key Insights
1. The overall customer churn rate for TNM stands at 26.9%. The top reasons customers cited for leaving include better offers from competitors (29.2%), access to better devices through competitors (28.7%), and dissatisfaction with customer support attitude (19.6%).
2. Geographically, the highest churn rates were observed in California (63.2%), Ohio (34.8%), and Pennsylvania (33.3%). In contrast, the lowest churn rates were seen in the District of Columbia (19.4%), Oklahoma (19.5%), and North Carolina (20.6%).
3. Churn rates varied notably across age groups, with the highest rate among customers aged 60 and above at 34%, followed by those aged 40 to 49 at 25%, and those aged 20 to 29 at 23%. Hence, the 60+ age group is a high-risk group for churning.
4. When analyzed by gender, the churn rate for female customers was slightly higher at 27.2%, compared to 26.5% for male customers.
5. Contract type had a significant impact on churn, with monthly contract users exhibiting a churn rate of 46%, while yearly contract users had a much lower churn rate of 7%.
6. Finally, data plan type also influenced churn behavior. Users with unlimited data plans had a churn rate of 32.1%, compared to 16.1% for those on capped data plans.

### Recommendations
##### 1. Strengthen Competitive Positioning
   - Revise pricing and promotional offers to match or exceed competitors, especially in regions with high churn like California.
   - Introduce loyalty rewards or exclusive upgrades for long-term customers to reduce churn driven by competitor offerings (29.2%).
##### 2. Upgrade Device Options and Financing
   - Expand the range of high-demand devices with flexible financing or upgrade programs to address the churn due to device-related dissatisfaction.
   - Promote device trade-in programs or bundling options to add perceived value.
##### 3. Improve Customer Support Quality
   - Invest in customer service training to enhance support staff attitude and responsiveness, addressing the 19.6% churn tied to poor service interactions.
   - Implement feedback loops and satisfaction surveys to monitor support quality in real-time.
##### 4. Targeted Retention Campaigns by Geography
   - Focus retention efforts in high-churn states such as California, Ohio, and Pennsylvania with customized offers, localized marketing, and community engagement.
   - Leverage success strategies from low-churn states (e.g., North Carolina and Oklahoma) and replicate effective practices.
##### 5. Age-Specific Retention Strategies
   - For the 60+ segment (34% churn), emphasize simplicity, reliability, and dedicated customer support (e.g., senior-friendly plans, in-store help).
   - Engage younger age groups (20–29 and 40–49) with flexible, digital-first plans and lifestyle benefits aligned with their needs.
##### 6. Contract Structure Optimization
   - Encourage conversion from monthly to yearly contracts through incentives such as discounted rates, bundled services, or bonus data.
   - Test hybrid plans (e.g., 6-month options) for customers hesitant to commit to long-term contracts.
##### 7. Data Plan Strategy Refinement
   - For unlimited plan users (32.1% churn), explore adding value-added services like streaming partnerships or faster throttled speeds post-cap.
   - Offer affordable, customizable data plans for capped users to minimize dissatisfaction and up-sell opportunities.

### Conclusion
This project demonstrates the use of machine learning to solve a real-world customer retention challenge. The pipeline can be extended for deployment in a business environment, and further tuned using hyperparameter optimization or additional models like XGBoost.
