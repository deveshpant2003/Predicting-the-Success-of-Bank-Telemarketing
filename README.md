# Overview
The objective of this project was to build an ML model that can predict the success of the bank's telemarketing campaign, which aims to make customers subscribe to a term deposit scheme. Each such success receives a 'yes' label. The data pertains to a banking institution's direct marketing campaigns, which were based on phone calls.

# Evaluation
This project was a part of my coursework at IIT Madras (Diploma in Data Science). For its students who subscribed to the course, the institution organized a private competition using the Kaggle platform. The institution evaluated the final score using a test data set, concealing the labels from the participants. It used the F1 score as a metric for evaluation.

# Submission File
I had to predict a class for each ID in the test set for the target variable. The file should contain a header and have the following format:

id	target
0	"yes"
1	"no"
2	"no"
etc.	

The column 'target' consists of the predicted labels. It then compares these predictions with the actual labels to calculate the F1 score. This file needs to be named as submission.csv and saved in the working directory of the Kaggle before submission. 

# Dataset Description
The data pertains to a banking institution's direct marketing campaigns. The marketing campaigns were based on phone calls. Often, multiple contacts with the same client were necessary to determine whether they would subscribe to the product (bank term deposit) or not.

# Files
* train.csv - the training set
test.csv - the test set
The file sample_submission.csv serves as an example of a submission in the correct format.

# Input variables:
1 last contact date: last contact date
2 age (numeric)
3 job : type of job
4 marital : marital status (categorical: "married","divorced","single"; note: "divorced" means divorced or widowed)
5 education (categorical: "unknown","secondary","primary","tertiary")
6 default: has credit in default? (binary: "yes","no")
7 balance: the average yearly balance, expressed in euros (numeric)
8 housing: has housing loan? (binary: "yes","no")
9 loan: has personal loan? (binary: "yes","no")
10 contact: contact communication type (categorical: "unknown","telephone","cellular")
11 duration: last contact duration, in seconds (numeric)
12 campaign: number of contacts performed during this campaign and for this client (numeric, includes last contact)
13 pdays: it refers to the number of days that have passed by after the client was last contacted from a previous campaign (numeric, -1 means the client was not previously contacted)
14 previous: number of contacts performed before this campaign and for this client (numeric)
15 poutcome: outcome of the previous marketing campaign (categorical: "unknown","other","failure","success")

# Output variable (desired target):
16 target: has the client subscribed a term deposit? (binary: "yes","no")
