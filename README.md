# Rotten Sentiment with Tomatoes
## Data Science Immersive Project Five: Sentiment Analysis on Rotten Tomatoes

## Table of Contents

- [Introduction](#introduction)
- [Dataset](#dataset)
- [Process](#process)
- [Results](#results)
- [Lessons Learned](#lessons-learned)
- [Resources](#resources)


## Introduction
For Project Five in my Data Science Immersive course, I chose to take on the [Kaggle](https://www.kaggle.com/c/sentiment-analysis-on-movie-reviews) competition for sentiment analysis of movie reviews on Rotten Tomatoes.

Rotten Tomatoes has become one of the go-to places to help determine if a movie is any good based on reviews from professional critics.  RT uses the Tomatometer which represents the percentage of professional critic reviews that are positive for a given film.

#### Tomatometer
- When at least 60% of reviews are positive, a red tomato is displayed to indicate its “Fresh” status.
- Anything less than 60% and a green “splat” is displayed indicating its “Rotten” status.
- Certified Fresh goes to movies/TV that meet certain strict requirements.
	- A steady Tomatometer score of 75% or higher.
	- At least five reviews from Top Critics.
	- Films in wide release must have a minimum of 80 reviews.
	- Films in limited release must have a minimum of 40 reviews.
	- Only individual seasons of a TV show are eligible, and each must have a minimum of 20 reviews.  

#### Audience Score
- Full popcorn bucket - 3.5 stars or higher
- Tipped over popcorn bucket - Less than 3.5 starts
- Plus sign for movies that do not have audience ratings

## Dataset

The datasets were available on Kaggle and were provided by the [Rotten Tomatoes](https://www.rottentomatoes.com).  There is a Train set as well as a Test set.  The data is comprised of phrases and sentiment ID's (positive, slightly positive, neutral, slightly negative, or negative).

## Process

Used a function to clean the phrases in the Phrase column eliminating "English" stop words and using the WordNet Lemmatizer in NLTK to group together inflections of a word for easier analysis.  

Using CountVectorizer(), I had to use max_features of 2000.  The reason for this is that anything bigger than that would create memory errors on my laptop.  This also keeps my laptop from having issues doing a train, test, split and running all the different models that I ran.  Unfortunately, using the max_features parameter for the CountVectorizer will not get me the best model for submitting to Kaggle.

I used several different models on my final features including Multinomial Naive Bayes, Bernoulli Naive Bayes, Random Forest, Extra Trees, Bagging Classifers, and simple Logistic Regression.

## Results

The best model ended up being Random Forest with a 61.3% score.  I initially ran a GridSearch using several parameters that took over 14 hours to complete on my desktop at home to find the best parameters.  I did the same with Logistic Regression.  Due to time constraints I couldn't do GridSearches for all the other classifiers that I used.

Insert image here with graph on different model results and their Kaggle scores.

While the Random Forest Classifier had the best overall accuracy score with 61.3%, when entered into the Kaggle competition, it ended up with the lowest Kaggle Score at 44.9%.  Inversely, the lowest accuracy score by model was the Multinomial Naive Bayes model with 56.7%, but it had the highest Kaggle Score among my models 48.7%.  As you can see, these are actually not very good results at all.

## Lessons Learned

After the course is completed, I definitely want to come back to this project to get better results.  There are several things to try:
- Neural Networks:  I initially tried this but was having with the Test Loss associated with my models.  The NN would also take a very long time to run so it would be easier on a better computer.
- Amazon Web Services: Since the resultant dataset was so large (and would be much larger if I tried to use the n-grams parameter), I could only use a small percentage of the features.  Running the data and models on an AWS instance would be more practical for this competition

## Resources

[Kaggle](http://www.kaggle.com)  
[Rotten Tomatoes](https://www.rottentomatoes.com)