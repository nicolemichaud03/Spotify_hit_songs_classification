# Spotify Hit Songs Classification
## Business Problem
There could be a number of factors that determine whether a song will be a hit or not. If we know what these factors are, we may be able to better predict how popular a song will be and therefore improve features such as user recommendations.

By looking at Spotify data, can we use certain features to predict whether or not a song will be a hit? What features are most predictive of hit songs?

- Metrics!

## Data Understanding
To begin, I import all the neccessary tools I will need for this project as well as the dataset I will be working with. I also explore the dataset to get a better understanding of the data it contains.

The dataset contains 6,398 Spotify songs from the 2010s. Exactly half of these songs are hits and half are not.

To get a general idea of what features might be related to the target, I performed a Pearson correlation. From this I found that the most positively correlated features with the target were danceability, loudness, valence, and time signature. Instrumentalness had the strongest negative correlation with the target.

## Data Preparation
To compare later models to, first a baseline model must first be created.
I normalized the data and created a train-test split to evaluate the models with. 

After creating various models including a decision tree, K nearest neighbors, and a logistic regression model (see miscellaneous notebook), I determined that the single decision tree performed the best and would be used as the baseline model.

## Modeling
The baseline model had a testing accuracy score of about 80.3% and a testing precision score of about 76.6%. It also had an AUC value of about 0.80.
The most important features to this baseline model were instrumentalness, energy, loudness, valence, and danceability.

GridSearchCV was then used to tune the model's hyperparameters to see if this improved it. This did not improve the model's metrics.

Next, I created a random forests model to see if it performed better at the classification task than the baseline model. 
The random forests model had a testing accuracy of about 83.2% and a testing precision score of about 80.3%. These metrics are better than the baseline model, however the model may be overfitting.

*I also conducted a GridSearchCV of hyperparameters for this random forests model to try and improve its performance. By doing this, the accuracy score was improved to about 81.8%, while the precision score was about 77.6%, which is not as good as the original random forests model but is still better than the baseline.


## Evaluation
Our final model is about 81.8% accurate and about 77.6% precise in correctly identifying songs as hits or not. The rate of false negatives to false positives (AUC) was about 0.82. This is an improvement to our baseline model which was a single decision tree before hyperparameter tuning that was about 80.3% accurate, about 76.8% precise in classifying our target and had an AUC of about 0.81. 

## Deployment

