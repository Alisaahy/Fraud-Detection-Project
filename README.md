# Fraud_detection_ML_project
Build predictive models to determine whether a given transaction will be fraudulent or not

## Project Objective
The financial services industry is suffering from fraud-related losses and damages. Only in one year, Fraudsters stole about $6 billion from banks last year. Fraud can also affect customer satisfaction and customer retention. As stated by ‘Javelin Strategy & Research’, more than 20 percent of customers choose to change their banks after experiencing fraud. This project used data from credit card transactions data loosely resembles real transactional data from a bank, and build a model to predict future fraud.

## Methods Used
- Machine Learning
- Data Visualization
- Feature Engineering
- Predictive Modeling
- etc.

## Technologies
- Python
- Pandas
- Scikit-learn
- Seaborn
- etc. 

## Project Description
Basically, the project includes 4 steps: 
- Load and Import Data
- Make Plots for Exploratory Data Analysis
- Data Wrangling and Feature Engineering
- Model Building
 
### Load data
The raw data is being kept [here](https://github.com/Alisaahy/Fraud_detection_ML_project/blob/master/src/transactions.txt.zip) within the repo

### EDA
Basically, I made histograms, kernel density estimate plots and cumulative distribution plots to show the distribution of some of my predictor variables.

### Data Wrangling and Feature Engineering
This is the most important part of this project, I focused on these features:
- Duplicated transactions: there’re many duplicated transactions in the raw data set and I want to detect them and label them. Generally speaking, there’re 2 types of duplicated transactions, one is the reversed transaction, where a purchase is followed by a reversal. Another is the multi-swipe, where a vendor accidentally charges a customer's card multiple times within a short time span. I built different functions to identify them and convert them to be dummy variables.

- rightCVV: Whether the entered CVV is correct. Typically, the card's verification value adds extra security to transaction. If the entered CVV is incorrect, it's highly possible that this transaction would be fraud.

- sameCountry: Whether the location where the card is acquired is the same as where the card is used. most of the time, people will use their cards in the country they acquired cards. If they use their cards in some other countries, it's possible that this transaction would be fraud.

- Whether first time purchasing merchant: Whether it’s the first time the user purchase in this merchant. Most of the time, fraud transactions happen in a merchant where the customer hasn't used before.

- expTime: The time between the transaction date and the expiration date.

- openTime: The time between the account open date and the transaction date.

- changeAddTime: The time between the last of address change date and the transaction date.

### Model Building
Methods I used in the model building part include:
- SMOTE: The target variable stating whether a transaction is fraud is highly imbalanced. SMOTE generates the virtual training records by randomly selecting one or more of the k-nearest neighbors for each example in the minority class. After the oversampling process, the data is reconstructed.

- Cross validation: cross validation is an algorithm that can ensure that each and every instance of the dataset will be trained and tested. The K-Fold Cross Validation works by first dividing the dataset into k-subsets. I divided the dataset into (k=3) parts. The algorithm helped us reserve 1 part for testing and train the algorithm over the 2 parts. It continued the process by changing the testing part in each iteration and training the algorithm over the other parts. The accuracies and errors are then averaged of the algorithm. With cross-validation, I can achieve a generalized model.

- RandomizedSearchCV: Random Search is a hyperparameter tuning algorithm. It helped me select models by setting up a grid of hyperparameter values and selecting random combinations to train the model and score. This allows me to explicitly control the number of parameter combinations that are attempted. It’s more efficient than GridSearchCV and its chance of finding the optimal parameter are comparatively similar.

- Decision tree: The decision true are generally in form of if-then-else statements. The deeper the tree, the more complex the rules and fitter the model.
I tried decision tree model first because it's a very interpretable model and it's very transparent. If the company is going to show the workflow of the machine learning model to non-technical audience, decision tree may be a good choice. Decision tree model can be easily visualized.

- Random forest: Random forest consists of a large number of individual decision trees that operate as an ensemble. Each individual tree in the random forest splits out a class prediction and the class with the most votes becomes our model’s prediction. I chose random forest because random forest works well in such high-dimensional cases. It’s typically less likely to be overfit.

- Light GBM: Light GBM is a gradient boosting framework that uses tree-based learning algorithms. Light GBM grows tree vertically. It chooses the leaf with max delta loss to grow. I choose chose GBM because it has faster training speed and higher efficiency, but at the same time, it typically has higher accuracy.
