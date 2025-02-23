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

From the boxplot above, we can see some outliers from a couple of the columns like total day minutes, total eve minutes, total night minutes etc. They are represented by the dots that are outside the whiskers. Outliers can affect the model performance and make the predictions less accurate so we will remove them. From the 3333 rows that we initially had, we are left with 3254. This means that we were able to remover 79 extreme outliers. Now that we have removed the outliers, we can now check the churn distribution for any class imbalance.

![Churn Distribution](https://github.com/Brendamutai/SyriaTel-Customer-Churn-Prediction/blob/main/Capture.JPG)

