# hackathon

## Contents

- [Team Name](#Team-Name)
- [Dataset](#Dataset)
- [Problem Statement](#Problem-Statement)
- [Data Dictionary](#Data-Dictionary)
- [Executive Summary](#Executive-Summary)
- [Conclusion](#Conclusion)


## Team Name

Team 2
- Andy Deemer
- Anna Jobsis
- Francisco Trejo


## Dataset

- [Kaggle](https://www.kaggle.com/c/kobe-bryant-shot-selection)


## Problem Statement

What characteristics of a shot lead to a higher probability of a shot being made by Kobe Bryant. 

## Data Dictionary

- [Data](https://www.kaggle.com/competitions/kobe-bryant-shot-selection/data)

|Feature|Type|Dataset|Description|
|---|---|---|---|
|combined_shot_type|object|kaggle|The type of basketball shot taken|
|minutes_remaining|object|kaggle|Minutes remaining on the clock when the shot was taken|
|period|object|kaggle|The period the shot was made|
|shot_type|object|kaggle|Whether the shot was 2 points or 3 points|
|year|object|calculated|The year the shot was taken|
|opponent|object|kaggle|The team that Kobe's team played against|
|playoffs|int|kaggle|The postseason tournament that the NBA has to determine season's champion|
|shot_distance|int|kaggle|The distance the shot was taken|
|shot_made_flag|float|kaggle|Binary flag whether the shot was made or missed|


## Executive Summary

The baseline was 55% for the majority class of our Target ("shot_made_flag" a.k.a. "Shots Made") class 0 which were shots that were missed. We looked at the dataset that include Kobe's shots from 1996 to 2016. The original dataset included over 30,000 shots, 5,000 of which had null values for the target class. These were left null by Kaggle and meant to be the test set for which models would predict the target class. Since we would not be able to use these to check the accuracy of our models' predictions, we dropped these 5,000 rows. 

Several features had overlapping information and thus would lead to issues with multicollinearity, so during exploratory data analysis, we identified these conflicting features and selected ones that we believed would capture the most signal and avoid multicollinearity issues. The features we ended up with after EDA and before beginning any preprocessing are included in the data dictionary described above. 

To begin preprocessing our selected features, we dummified categorical data. One of the features "shot_distance" was a continuous variable, and "playoffs" was already a one-hot-encoded variable. We concatenated these variables into a dataframe. 

After this dataframe was created with the dummified features, we created a test train split, and standard scaled all of our data. 

After standard scaling, we used SelectKBest to select the top 20 features that captured most of the signal. If we were to continue this project in an effort to improve the models and capture more signal, we would incorporate PCA on the remaining features that were not select by SelectKBest to capture more of the signal and inevitably some noise. 

The two models we chose to use were Logistic Regression and Random Forest. Both models had similar accuracy in predicting the target class. The resulting conclusions are explained in the section below. 


## Conclusion

We are going to use our Logistic Regression model over our Random Forest model. Even though both models scored the same our Logistic Regression model provides more interpretable coefficients to better identify which characteristics lead to whether a shot is made or not. Due to time constraints we did not run a GridSearch on our Random Forests model. Provided we have more time that would be an important next step to help better improve our model's score. combined_shot_type_Dunk was one characteristic that showed up with the highest coefficient in the Logist Regression model and as the 2nd most important feature in the Random Forests model. To better improve chances of making a shot dunk the ball!!!!