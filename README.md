# SyriaTel-Customer-Churn-Prediction
## Overview
Customer churn is a huge challenge in the telecommunication industry today. This project aims to develop a machine-learning model that predicts which customers are likely to churn. By identifying them early, SyriaTel can take proactive measures that can improve customer retention and reduce revenue loss.

## 1. Business Understanding
SyriaTel is a telecommunication company that is highly affected by customer churn and this is leading to revenue loss. The company needs an early warning system to identify which customers might be leaving soon so they can take necessary actions to retain them.

*Objectives*
- Predict churn.
- Analyze key factors leading to churn.
- Recommendations on how they can reduce customer churn leading to increase in revenue.

## 2. Data Understanding
This dataset was sourced from [Kaggle](https://www.kaggle.com/datasets/becksddf/churn-in-telecoms-dataset?resource=download). This dataset is going to help us build the model. The key features include:

*Customer information* - State, Acc. length, Area code and Phone number

*Service plan* - International plan and voice mail plan.

*Usage data* - Total minutes, calls and charge (day, evening, night)

*Customer support interaction* - Customer service calls

*Target variable* - Churn(1 = left, 0 = Stayed)

## 3.Data Preparation
### Data cleaning

We will start by inspecting and cleaning our data. This process is crucial because raw data often contain errors, so it will improve our data accuracy. It will also enhance our model performance as it performs better with high-quality data. After that we will  standardize our data and remove any unnecessary columns so we can be left with the relevant ones. Machine learning models work best with numeric data but these columns are not numeric. We will have to convert them to numeric first.

## Handling Outliers

Now that we have successefully converted our columns to numeric, we are going to see if we can detect any outliers. We are going to do so by first generating a summary of our statistics which will help us identify possible values that are much higher or lower than expected.

![Outlier Detection Boxplot](https://github.com/Brendamutai/SyriaTel-Customer-Churn-Prediction/blob/main/Capture.JPG)

From the boxplot above, we can see some outliers from a couple of the columns like total day minutes, total eve minutes, total night minutes etc. They are represented by the dots that are outside the whiskers. Outliers can affect the model performance and make the predictions less accurate so we will remove them. From the 3333 rows that we initially had, we are left with 3254. This means that we were able to remove 79 extreme outliers. Now that we have removed the outliers, we can now check the churn distribution for any class imbalance.

![Churn Distribution](https://github.com/Brendamutai/SyriaTel-Customer-Churn-Prediction/blob/main/Churn%20distribution.JPG)

## Handling class imbalance

From the bar graph, there is a clear class imbalance. About 85.7% of customers stayed while 14.3% left. Because we do not want to get biased predictions, we are going to have to balance our classes. For this case we are going to use manual oversampling just to prevent losing any important data by undersampling. We are going to do this by duplicating the churned customers until both classes are balanced. Once they are both balanced we can check which features highly influence churn.

![Churn Correlation Heatmap](https://github.com/Brendamutai/SyriaTel-Customer-Churn-Prediction/blob/main/Correlation%20Heatmap.JPG)

From the heatmap above, we are able to see that:

1. Customers with international plan churn more.(0.29)
2. High daytime usage correlates with churn.(0.26)
3. Frequent support calls will likely cause someone to churn.(0.24)
4. Customers with voice mail plan are less likely to churn.(-0.13)
5. More international calls slightly reduce churn.(-0.08)

## Feature Engineering

Now that we know exactly what features correlate with churn, we are going to create new variables that are going to help improve our machine learning model and help it make better predictions.

1. Get the sum of all charges.
2. The customer service call ratio.
3. Average call duration.
4. How international plan affects usage.

Now that we have the features we need, we are going to standardize the numerical features for better model performance. We are also going to convert our categorical variables(specifically `area code` because we had converted the rest earlier) into a format that the machine will be able to read. Once that is done, We can fit our models!

## 1. Logistic Regression
 We will start by splitting our data into training(80%) and testing(20%) then train a simple logistic regression model, make predictions and see how it will perform.

![Logistic regression confusion Matrix](https://github.com/Brendamutai/SyriaTel-Customer-Churn-Prediction/blob/main/Logistic%20Confusion%20Matrix.JPG)

### Findings from our logistic regression model.

1. The model was about 78.14% accurate.
2. Precision and recall was balanced across all customers.(78%)
3. The customers who stayed and were correctly classified were 447(True Negatives)
4. The customers who left and were correctly classified were 425(True Positives)
5. The customers who stayed and were wrongly classified as churned were 111(False Positives)
6. The customers who left and were wrongly classified as stayed were 133(False Negatives)

### 2. Random Forest
We are now going to train a random forest model, just to see how it compares to our logistic regression model.
[Random Forest confusion Matrix](https://github.com/Brendamutai/SyriaTel-Customer-Churn-Prediction/blob/main/Logistic%20Confusion%20Matrix.JPG)


