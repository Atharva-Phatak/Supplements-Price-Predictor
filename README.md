# Supplements Prics Predictor

## Introduction
According to the IHRSA (International Health, Racquet & Sportsclub Association), the $30 billion health and fitness industry in the U.S. has been growing by at least 3 - 4% annually for the last ten years and shows no signs of slowing down anytime soon.So Fitness is a huge industry and everyone nowadays wants to stay healthy and be fit. Most people we know use some kind of supplements be it proteins or vitamins,etc. The supplement industry has insane amount of revenue and the supplement companies have varied products depending on your goals for your body,thus making it a lucrative market.

## Problem Definition

So here's the catch, for an average person purchasing supplements is sometimes costly and many a times he/she wonder why are supplement's so costly?

***What are the things that make them costly? i.e which factors dictate the cost price ?***
This is what we are going to explore in this project using Data Analysis and use a machine Learning models to try and predict the prices.

![overview](https://github.com/Atharva-Phatak/Supplements-Price-Predictor/blob/master/images/Overview.gif)

## Data Collection

I built a custom webscraper using BeautifulSoup and Selenium. The data was scraped from bodybuilding.com which a leading site for buying supplements. I scraped supplements from only two categories viz "Protiens" and "Workout-booster". For the products I only selected supplements which were consumed as powder. Protiens category contains all kinds of proteins like whey proteins,whey isolates,etc.
Workout Boosters contain all the supplements which help you boost your workouts and help in revovery. For ex products like pre workouts, BCAA's,etc are included in this category.

I'm not going to release the data,please collect your own data by modifying my scrapers code.

## About the Dataset

I have collected data form bodybuilding.com about two kinds of products. They are as follows:-

* ***Proteins*** : This is a general category which includes various kinds of protein powder like whey, whey isloate, casein,etc
* ***Workout Boosters*** : This is also a general cateogry encompassing workout boosters like creatine, pre-workout, BCAA's,etc
The data has the follwing columns:

  * ***Product***: The products name.
  * ***Brand***: The brand which has created the product and markets it.
  * ***Price***: The price of the product
  * ***Rating*** : The rating given by the users
  * ***Review Count***: The number of reviews for that product
  * ***Flavor Rating*** : The rating for that product
  * ***Flavor***: The flavor for that product
  * ***Size*** : The size of the container
  * ***Servings*** : The amount of scoop servings the person can have.
  * ***Scoop Size*** : The size of single scoop
  * ***Avaiable Size***: The number of available sizes for the product
  * ***Available Flavors*** : The number available flavors that are currently avaiable for the product.

## Data Cleaning and Exploratory Data Analysis

### Data Cleaning
So the data was super interesting to me and I wanted to know mode things about the data. Hence I first began cleaning the data and then did EDA on it.

So the columns Size, Servings and Scoop Size were all text data. I cleaned them as follows:-

* ***Servings*** : A single entry in this column looks like this : "Servings Per Container71".
 I created a function and extracted the servings size from the text using regex. 
* ***Scoop_Size*** : Every entry in this column gave the scoop size in grams for the number  of scoops mentioned in the text. I extracted scoop size using regex.
* ***Size*** : Finally I used the values extracted form the servings and scoop_size columns to calculate the accurate sizes.

### Exploratory Data Analysis

This time I used ipywidgets to build small inline apps for my analysis which are pretty useful as the reduce the amount of code. I'm attaching respective GIFs of the exploration.

***1. Distribution of numeric Features***

![dist](https://github.com/Atharva-Phatak/Supplements-Price-Predictor/blob/master/images/Distributions.gif)

***2. Scatter Plots***

![scatter](https://github.com/Atharva-Phatak/Supplements-Price-Predictor/blob/master/images/Scatter.gif)

***3. Violin Plots, Pie Diagrams and Bar Plots***

![extra_plots](https://github.com/Atharva-Phatak/Supplements-Price-Predictor/blob/master/images/Violin%2Bother.gif)

***4. Correlation Plot using Seaborn***
![](https://github.com/Atharva-Phatak/Supplements-Price-Predictor/blob/master/images/heatmap.png)

#### Findings

* If you look at the distributions most of the distributions are left or right skewed though the price distribution is almost normal.
* In Rating vs Price most values are concentrated between rating of 9-10 and value of price below 40$.
* In the plot for flavor_rating vs Price most data points are concetrated between flavor rating of 9-10 with prices between 20-40$.
* For size vs Price, most products have size between 0-5Lbs, though if you see there are very few products that charge above 100$.
* The company ***Optimum Nutrition*** dominates the ***Protein category*** and ***Evolution Nutrition*** dominates the ***workout booster*** category.
* ***Choclate flavor*** is the most selected flavor for ***protein supplements*** and apprently people like to take ***unflavored workout boosters.***

### Building Models

* I used three models RandomForests,XGBOOST,AdaBoost for predicting the prices.
* The metrics I used were RMSE,MAE and R2-Score

The model didn't perform well because of the less amount of the data avaialble. Also I used Ipywidgets for creating a drop down menu and a slider where you can select models name and number of folds to train on. 

![train](https://github.com/Atharva-Phatak/Supplements-Price-Predictor/blob/master/images/Train.gif)

* Here are the models R2-Score for the 5-folds

  * ***Random Forest*** : 0.378
  * ***XGBoost*** : 0.438
  * ***AdaBoost*** : 0.37
  
  * Also I used eli5 and shapely values for machine learning interpretability, to understand what features affected my models predictions. Have a look at it in the notebook.
  
 ## ***Conclusion and Future Scope***

* From the analysis it is clear that size , Servings are the most important factor which affect the price of the product.
* We also found that Available flavors and review count do not affect the predicitons of the model as much.
* For future scope, you can collect more data regarding the products  like their contents etc.
* You can also try to increase the amount of data using sampling methods like SMOTE.
* Try using hyperparameter tuning to find the most optimal hyperparameters.

## If you want to run it please download and run it on your local machine so that you can use ipywidgets.
# Requirements 

* Python 3.6
* Ipywidgets
* Seaborn,Matplotlib
* Scikit learn
* Eli5
* Shapely
# If you like my work please show appreciation by giving my repo a star and feel free to use it for your own purposes
 
