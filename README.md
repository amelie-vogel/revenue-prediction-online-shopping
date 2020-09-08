# Prediction Of Revenue - Online Shopping 

## Dataset 

### Description 
The dataset consists of feature vectors belonging to 12,330 online sessions of shopping, and each session belongs to a different user in a 1-year period.

The features are composed of 10 numerical and 8 categorical attributes (see below). I've used the *Revenue* attribute as the class label.

The dataset is imbalanced: of the 12,330 sessions, 84.5% (10,422) were negative class samples that did not end with shopping, and the rest (1,908) were positive class samples ending with shopping.

You can find the whole datset through this link: https://archive.ics.uci.edu/ml/datasets/Online+Shoppers+Purchasing+Intention+Dataset

### Attribute information
* **Web page categories and online duration**: some attributes represent the number of different pages belonging to the same category a visitor visits, during one session, and the total time spent in each of these page categories (*Administrative*, *Administrative Duration*, *Informational*, *Informational Duration*, *Product Related*, *Product Related Duration*). The values of these features are derived from the URL information of the pages visited by the user and updated in real time when a user takes an action, e.g. moving from one page to another. 
* **Google Analytics metrics**: *Bounce Rates*, *Exit Rates* and *Page Values* features have been built from the Google Analytics metrics of pages. For example, if the session ends after only 1 page visited, the bounce rate and the exit rate of the session is 20% ; after 2 pages visited, the bounce rate is 0 and the exit rate 10% etc. 
* **The *Special Day* feature** indicates the closeness of time to a specific special day (e.g. Mother’s Day, Valentine's Day) in which the sessions are more likely to be finalized with transaction. 
* **Visitor information**: the dataset also includes *operating system*, *browser*, *region*, *traffic type*, *visitor type* as returning or new visitor. 
* **Time attributes**: a boolean value indicates whether the date of the visit is *weekend*, and another what *month of the year* it is.

## Cleaning the data

The main task of cleaning was dropping outliers with huge online durations (more than 3,000 rows), which can be explained by the user switching to another website and keeping this one open.


# Exploratory Data Analysis

## Visualization


# Modelling

## Supervised Learning

I tried xx models of classification and evaluated them using k-fold cross-validation. 

Here are the results:

### Logistic Regression

### SVM

### Random Forest

### XGBoost

### LSTM artificial recurrent neural network

## Model Evaluation and Selection

with k-fold cross-validation

##### Depth of the model:

![image](https://user-images.githubusercontent.com/63364114/92381073-76018700-f10a-11ea-8834-7b3490d2f08a.png)

##### Number ot estimators:

![image](https://user-images.githubusercontent.com/63364114/92381049-6f730f80-f10a-11ea-857b-61cfebcac843.png)


### Selected model 

Based on the previous results, we opt for the Random Forest Regression model with parameters: depth of 15 and 35 estimators. 

## Contact me
[LinkedIn](https://linkedin.com/in/amelie-vogel-/)

[GitHub](https://https://github.com/amelie-vogel/)
