#  Prediction of Online Shoppers’ Purchasing Intention

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

The main task of cleaning was dropping outliers with invalid online durations (more than 3,000 rows). 


# Exploratory Data Analysis

## Visualization

![image](https://user-images.githubusercontent.com/63364114/102078166-c1fb5080-3e0a-11eb-8218-80f5d447e517.png)

Very important point here: the dataset is properly imbalanced with almost 90% of "No Purchase" and 10% of "Purchase". 

![image](https://user-images.githubusercontent.com/63364114/92531851-6334a280-f22f-11ea-810f-3c17dda0cb32.png)

The month of the year seems to contain distinctive information to help classify the sessions: autumn months generate more revenue than other months.

![image](https://user-images.githubusercontent.com/63364114/92531889-75164580-f22f-11ea-90db-2e7b20b802d3.png)

![image](https://user-images.githubusercontent.com/63364114/92531910-7c3d5380-f22f-11ea-904a-9eb92ac44c9c.png)

As a consequence of the important number of returning visitors compared to new visitors, the proportion of sessions ending with purchase drops with returning visitors, while the new ones are around 25% to buy something at the end of their sessions.

![image](https://user-images.githubusercontent.com/63364114/102077165-29b09c00-3e09-11eb-9b0b-22fa4dc994d6.png)

The duration in minutes is longer on average for the sessions that end with purchase.

![image](https://user-images.githubusercontent.com/63364114/102077199-3503c780-3e09-11eb-919d-6d727f46f030.png)

The bounce rate is much higher on average for the sessions that don't end with purchase.

![image](https://user-images.githubusercontent.com/63364114/102077216-3a611200-3e09-11eb-8656-227ab5ba966f.png)

The exit rate is much higher on average among the sessions that don't end with purchase.

![image](https://user-images.githubusercontent.com/63364114/102077228-3df49900-3e09-11eb-9e77-7885ce7e96b2.png)

Logically, the page value seems to be an important distinctive feature, since you visit pages with high value when you buy.

![image](https://user-images.githubusercontent.com/63364114/102077253-43ea7a00-3e09-11eb-809c-01291216ad6b.png)


![image](https://user-images.githubusercontent.com/63364114/102077248-41882000-3e09-11eb-8ad3-5a59383a39d4.png)

Week-end sessions are more likely to generate revenue compared to weekday sessions, even though the latter are more numerous.


# Modelling

## Supervised Learning

This project was aimed to learn the Logistic Regression Model. That's why, I only used this model of classification and tried to get better results first with a recursive features elimination process, and then with the "balanced" mode of the LR algorithm.

The dataset was indeed imbalanced, as we saw before: 90% of "No purchase" labeled sessions, and 10% of "Purchase". 

I quickly evaluated my model using a confusion matrix.

Here are the results:

### Recursive Features Elimination

From the RFE, we got these features as the best to classify our sessions - some of them were expected from our visualizations: *'BounceRates', 'ExitRates', 'PageValues', 'VisitorType_ ReturningVisitor',  'Month_Dec', 'Month_Feb', 'Month_Mar', 'Month_May', 'Month_Nov', 'Month_Sep'*


Testing the LR model with a different number of features, we see that our metrics (accuracy, precision and recall) don't increase significantly after k=10 features: this confirmed our RFE.

![image](https://user-images.githubusercontent.com/63364114/102080855-7b5c2500-3e0f-11eb-8ac1-768218cc4752.png)


### Balanced Logistic Regression

To balance the dataset, I used the class penalties/weights option of the Logistic Regression ("imbalanced" mode).

The accuracy of my model is 0.91, the precision is 0.63, the recall is 0.75, and the mean of all scores is 0.68.

The confusion matrix gives us this results: 

- There are 2716 right results: 2429 true negatives, 287 true positives

- There are 267 errors: 95 false negatives, 172 false positives


### Conclusion

The Logistic Regression Model gives us a quite good result on accuracy, but could be improved on precision and recall. For this purpose, we could test other models that usually get better performance on classification: Random Forest calssifier, SVM classifier, Neural Networks classifier ; and also tr handling the imbalanced dataset differently.

## Contact me
[LinkedIn](https://linkedin.com/in/amelie-vogel-/)

[GitHub](https://https://github.com/amelie-vogel/)
