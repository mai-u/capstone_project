
Capstone individual project (4 weeks timeframe):
# **“Ingredients for a successful restaurant - Predicting restaurant success and identifying good business practices”**


## Executive Summary
This project was completed during my time on the General Assembly Data Science Immersive course in London.

Through my analysis of Yelp data, I aim to identify **common traits which are predictive of restaurant success and failure**, and to **use these insights to help new restaurants achieve success**.

I performed various statistical learning models including regression and classification predictive modeling, sentiment analysis, and natural language processing. I created classification models that predicted future outcomes for restaurants with 75% accuracy. Actionable insights were extracted from the dataset through statistical analysis, identifying risks and opportunities for a restaurant owner and proposing new ideas. 

## Files in This Repository

 - [**Presentation slides**](https://github.com/mai-u/capstone_project/blob/master/Capstone_Result_Presentation.pdf): This was prepared to present the project, results, and recommendations to non-technical audience 
-   [**Technical report**](https://nbviewer.jupyter.org/github/mai-u/capstone_project/blob/master/Capstone_Technical_Report.ipynb): This was prepared for reporting and explaining my project to technical audience. It is written in detail about a literature review, data cleaning, feature engineering process, exploratory data analysis, findings per research question, limitations and recommendations for future research. 
-   **Jupyter Notebook files (.ipynb)**:
	-   Step 1: [Dataset and Data Collection](https://nbviewer.jupyter.org/github/mai-u/capstone_project/blob/master/Jupyter_Notebook_files/Step_01_Dataset_and_Data_Collection.ipynb)
	-   Step 2: [Data Cleaning](https://nbviewer.jupyter.org/github/mai-u/capstone_project/blob/master/Jupyter_Notebook_files/Step_02_Data_Cleaning.ipynb)
	-   Step 3: [Exploratory Data Analysis](https://nbviewer.jupyter.org/github/mai-u/capstone_project/blob/master/Jupyter_Notebook_files/Step_03_Exploratory_Data_Analysis.ipynb)
	-   Step 4: Data Modeling 
		-   [Research Question 1](https://nbviewer.jupyter.org/github/mai-u/capstone_project/blob/master/Jupyter_Notebook_files/Step_04_Question_1_Data_Modeling.ipynb)
		-   [Research Question 2](https://nbviewer.jupyter.org/github/mai-u/capstone_project/blob/master/Jupyter_Notebook_files/Step_04_Question_2_Data_Modeling.ipynb)
		-   [Research Question 3](https://nbviewer.jupyter.org/github/mai-u/capstone_project/blob/master/Jupyter_Notebook_files/Step_04_Question_3_Data_Modeling.ipynb)

-------
## Problem Statement
Opening a restaurant is often very costly and logistically complicated. It is not easy for restaurants to survive -  **60%**  of all restaurants close  **before their third anniversary,**  and  **80%**  **before their fifth**. However, it is often the case that restaurant owners and investors rely on their/others’ experiences and anecdotal evidence rather than a data-driven approach to decision making.

My friends would like to know if machine learning can be useful in accuracy predicting future business success as well as determining which key attributes and business practices lead to success, as well as failure.

## Objectives

I defined research objectives as below:
1.  Predict the probability that a business will be closed in the near future
2.  Identify good business practices
3.  Create a tool that can help restaurant owners improve their likelihood of success
  
For the purpose of this capstone, the success or performance of a restaurant is considered to be the survival after three years due to the resource availability and limited time. The feature is generated based on the business status information which shows whether the restaurant is closed or open.

## Hypothesis
My hypothesis is that peoples' perceptions are significantly predictive of business success. I would say:
-   Businesses with good ratings tend to be successful, and businesses with bad ratings remain open for a shorter time than the businesses with good or above average ratings.
-   If ratings do not contribute to the prediction, business successes are related to competitive advantages that refer to business attributes, service, and ambience that make them preferred choice of customers within the market.
    
In addition to verifying this hypothesis, I would like to provide relevant insights to business owners/investors to help them achieve future business success.

## Research Questions
<a href="https://imgur.com/sNXk6NQ"><img src="https://i.imgur.com/sNXk6NQ.png" title="source: imgur.com" /></a>
#### Question 1. : Are customers’ perceptions correlated to future success? If so, what features are important to becoming a successful restaurant?

My prediction is that models will not be accurate in predicting business success based on star ratings since each person defines star ratings differently. Thus, in addition to star rating information, I would use sentiment scores per review. However, there are still many other factors that can cause good businesses to close or bad businesses to remain open. Thus, if the first hypothesis fails, I would like to test the second hypothesis.

#### Question 2. Are business attributes and ambience features correlated to future success? If so, what did successful restaurants do?

I believe that, if the features of a business have a great impact on how a business is rated, this information can be used to predict business success significantly.

#### Question 3. Did successful restaurants get different reviews from those that failed? If so, what differentiates successful from failure?

Although it could  turn out that sentiment scores and star ratings are not relevant to business success, I would still believe that online customer reviews are essential in helping consumers make decisions and restaurants understand what customers think about a business. Therefore, it is also interesting to see whether consumer reviews can give interesting insights to business owners/investors to achieve future business success.

## Dataset

I used publicly available data on [Yelp](https://www.yelp.com/dataset/challenge) from 2005 to 2018. I downloaded JSON files which contain:
-   Information on 1.6M users
-   200+ attribute and ambience information on 200K businesses
-   Reviews (7+M)
-   Check-ins and Tips (3+M)

## Exploratory Data Analysis
<a href="https://imgur.com/EGw5nr9"><img src="https://i.imgur.com/EGw5nr9.png" title="source: imgur.com" /></a>

## Model Selection
Since it is a binary classification problem (1 as successful and 0 as failed), I selected the following classifiers for question 1 and 2 and trained models based on features available in the dataset:

1.  Logistic Regression with a Ridge penalty
2.  Logistic Regression with a Lasso penalty
3.  GridsearchCV on Logistic Regression
4.  K-Nearest Neighbours Classifier
5.  Ada Boost Classifier
6.  Gradient Boosting Classifier
7.  Decision Tree Classifier
8.  GridsearchCV on Decision Tree Classifier
9.  Support Vector Machine
   
I aimed to show the likelihood of success to restaurant owners by using predict_proba of classification models since the function returns the probability for each outcome class as a value between 0 and 1. In addition to the above, I used Natural Language Processing (Count Vectorization with scikit-learn) to extract good business practices for question 3.

## Findings

### Question 1. Are customers’ perceptions correlated to future success? If so, what features are important to becoming a successful restaurant?
Text features failed to have significant indications for the future success of the restaurant. 

It turned out that the test and mean cross-validation scores of any models were almost the same as baseline. Also, I found that the sentiment feature groups are not significantly related to the prediction - the coefficient values turned out to be too sparse, which means that my models did not catch important information to predict business success. 

It implies that star rating and sentiment did no help in predicting the success of the restaurant. It leads to the conclusion that restaurants with low review stars and sentiment scores were not necessarily more likely to shut down.

<a href="https://imgur.com/MOic32f"><img src="https://i.imgur.com/MOic32f.png" title="source: imgur.com" /></a>

### Question 2. Are business attributes and ambience features correlated to future success? If so, what did successful restaurants do?

Non-text features, especially business features, have a strong correlation to future restaurant performance. Classification models predicted future success with 75% accuracy. 

Comparing the classifiers, eight out of ten classification models achieved similar scores on evaluation metrics. Except Decision Tree Classifier, the results from train sets and test sets are quite close for different models.
<a href="https://imgur.com/3PkaPUO"><img src="https://i.imgur.com/3PkaPUO.png" title="source: imgur.com" /></a>

**Important categories for business success:**
<a href="https://imgur.com/KlRXoQI"><img src="https://i.imgur.com/KlRXoQI.png" title="source: imgur.com" /></a>

**Features correlated to business failure:**
<a href="https://imgur.com/9c8Rjle"><img src="https://i.imgur.com/9c8Rjle.png" title="source: imgur.com" /></a>

### Question 3. Did successful restaurants get different reviews from those that failed? If so, what differentiates successful from failure?

I identified customer experience topics that lead to a positive or negative experience which are valuable insights for restaurant owners and investors.

I found that:
-   Americans leave positive reviews of restaurants after they had a positive experience at restaurants - my expectation was. They also tend to talk about food, especially specific menu served at restaurants.
-   People write more about service, especially when they wasted time and money and had terrible customer service. Also, they tend to leave specific points such as 'It took 20 minutes to get my food, the manager was terrible, mold beer, mold floating'.

<a href="https://imgur.com/aZuLElw"><img src="https://i.imgur.com/aZuLElw.png" title="source: imgur.com" /></a>
<a href="https://imgur.com/lQQVaaO"><img src="https://i.imgur.com/lQQVaaO.png" title="source: imgur.com" /></a>

## Conclusion

### To Client
- Classification models managed to:
    -   Predict future success with 75% accuracy (vs. baseline 67%)
    -   Identify:
        -   Good business practices
        -   Risks for business failure
- Based on the results of sentiment analysis, restaurants should focus on more physical attributes than customer perception
- Based on nationwide analysis, restaurants would do well by:
    -  Offering parking spaces    
    -  Focusing on high margin food
    -  Avoiding commissions and unnecessary rent fees
- Restaurants should regularly analyse customer comments by:
    -   Checking frequently used words in reviews
    -   Avoiding subjective statements
    
### To Technical Audience
The goal of this paper is to look for features in order to better predict the future success of a restaurant. I generated features through several aspects, and both text and non-text features were covered.

It turns out that our model works fairly well, and achieved 75% accuracy in the end (65% baseline).

Since the goal of this project is to help restaurant owners and investors decide if certain restaurant/category is worth investing, precision for the 'successful' class is critical. The precision rate for 'successful' class is 75%, which means that in all restaurants that models tried to predict, 75% of them were predicted correctly. The coefficient table was provided to understand which features are the most important for prediction.

If someone who is not familiar with a given place wants to open a business or invest in a city, my models might be helpful for one to learn, exploit and improve weaknesses and strengthen the competitive advantages.