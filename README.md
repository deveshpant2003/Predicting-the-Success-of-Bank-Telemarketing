# Overview
The objective of this project was to build an ML model that can predict the success of the bank's telemarketing campaign, which aims to make clients subscribe to a term deposit scheme. Each such success receives a 'yes' label. The data pertains to a banking institution's direct marketing campaigns, which were based on phone calls.

# Evaluation
This project was a part of my coursework at IIT Madras (Diploma in Data Science). For its students who subscribed to the course, the institution organized a private competition using the Kaggle platform. The institution evaluated the final score using a test data set, concealing the labels from the participants. It used the F1 score as a metric for evaluation.

# Submission File
I had to predict a class for each ID in the test set for the target variable. The file should contain a header and have the following format:

<br>id	target
<br>0	"yes"
<br>1	"no"
<br>2	"no"
<br>etc.	

The column 'target' consists of the predicted labels. It then compares these predictions with the actual labels to calculate the F1 score. This file needs to be named as submission.csv and saved in the working directory of the Kaggle before submission. 

# Dataset Description
The data pertains to a banking institution's direct marketing campaigns. The marketing campaigns were based on phone calls. Often, multiple contacts with the same client were necessary to determine whether they would subscribe to the product (bank term deposit) or not.

# Files
* train.csv - the training set
* test.csv - the test set
* The file sample_submission.csv serves as an example of a submission in the correct format.

# Input variables:
<br>**1. last contact date**: last contact date
<br>**2. age :** age of the client (numeric)
<br>**3. job :** type of job
<br>**4. marital :** marital status (categorical: "married","divorced","single"; note: "divorced" means divorced or widowed)
<br>**5. education :** level of education (categorical: "unknown","secondary","primary","tertiary") 
<br>**6. default:** indicates if the client has a credit in default (binary: "yes","no")
<br>**7. balance:** the average yearly balance, expressed in euros (numeric)
<br>**8. housing:** indicates if the client has a housing loan? (binary: "yes","no")
<br>**9. loan:** indicates if the client has a personal loan? (binary: "yes","no")
<br>**10. contact:** contact communication type (categorical: "unknown","telephone","cellular")
<br>**11. duration:** last contact duration, in seconds (numeric)
<br>**12. campaign:** number of contacts performed during this campaign and for this client (numeric, includes last contact)
<br>**13. pdays:** it refers to the number of days that have passed by after the client was last contacted from a previous campaign (numeric, -1 means the client was not previously contacted)
<br>**14. previous:** number of contacts performed before this campaign and for this client (numeric)
<br>**15. poutcome:** outcome of the previous marketing campaign (categorical: "unknown","other","failure","success")

# Output variable (desired target):
<br>**target:** has the client subscribed a term deposit? (binary: "yes","no")

# EDA (Exploratory Data Analysis)
* There are 15 columns and 39211 rows, including the target variable, and only categorical variables consist of null values. These variables are job, education, contact, and poutcome. This scenario holds true for both the train and test data. In the respective column, I replaced these null values with the most common non-null value.

* The majority of jobs are blue-collar, management, and technician. Together, they comprise 55% of total jobs. Self-employed, retired, entrepreneurs, unemployed, housemaids, and students are more or less the same. Students are the least in numbers (3.6%).

* The majority of them have the highest qualification in secondary education (53.7%), which is almost twice the tertiary education (29.6%) and three times the primary education (16.7%).

* The majority of samples use cellular phones, approximately 35000, compared to around 4000 for telephone users.

* The poutcome is mostly failure (87.7%), and the success rate is very low (5.7%).

* The proportion of married people (57.9%) is more than double the number of singles and almost five times more than the divorced (13.4%).

* Very few of them have credit in default (5.8%).

* The difference between people having housing loans (55.2%) and the ones not having them is not much (44.8%).

* Very few of them have taken personal loans (18.8%).

* The data is highly imbalanced. 85% of samples have a target value of no, and the rest are yes.

* The age appears to follow a log normal distribution, while all other numerical variables appear to have an exponential distribution, according to the histograms.

* Looking at the box plots, age appears to have a few outliers between 75 and 90. Campaigns have a greater number of outliers compared to age, but still, it is nothing compared to other numerical variables, which are highly imbalanced. 

* Variables like balance, duration, campaign, days, and previous share a positive correlation with each other, which varies between 0.4 and 0.8. It suggests that individuals with a substantial balance tend to make more inquiries about term deposits, receive frequent contact from the bank, and remain uncontacted throughout the campaign if they don't subscribe to term deposits. From a duration perspective, this could suggest that individuals who make more inquiries, subscribed, or expressed interest in previous campaigns receive more frequent contact in the current campaign. However, I believe all of these variables have an indirect correlation with each other via the balance variable. Also, they have a weak positive correlation with the value of poutcome being success. The campaign has a higher chance of success with people who have a sufficient balance in their bank accounts.

* Interestingly, these variables also have a positive correlation ranging between 0.4 and 0.6, with the value of default being yes, meaning that people with a higher average yearly balance have high chances of having credit in default. This is probably because such people's balance includes the debt amount they have raised.

* While analyzing the line graphs, I observed that every numerical variable repeats a pattern every year. Most likely, the data was only available for a year, but it was reproduced to span three years with minor variations. Also, all of the numerical variables are highly volatile, and their value just shoots and falls drastically on a monthly basis.

# Best Model 
I tried to train almost all the machine-learning models in the Scikit Learn library. However, the random forest classifier with the following value of hyperparameters turns out to be the best among them:
* bootstrap: True, 
* max_depth: 30,
* max_features: 12,
* min_samples_leaf: 6,
* min_samples_split: 15,
* n_estimators: 400

Below is the classification report for this model over validation set:

               precision    recall  f1-score   support

          no       0.97      0.87      0.92      7821
         yes       0.53      0.82      0.65      1390

    accuracy                           0.86      9211
   macro avg       0.75      0.85      0.78      9211
weighted avg       0.90      0.86      0.87      9211

<img width="400" alt="image" src="https://github.com/user-attachments/assets/aa81527f-845d-421c-9292-363d5c05d98e" />



