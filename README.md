<img src="https://i2.wp.com/teaser-trailer.com/wp-content/uploads/Avengers-Infinity-War-Banner.jpg?ssl=1" width="110%" >

# ABSTRACT
For this SOEN471 project, we will create a Sentiment Analysis Model that will be developed based on a Twitter dataset. This model will then be used to analyze, in a team of two people, the scripts of the Marvel Cinematic Universe Movies (Notably the Avengers and The Iron Man Franchise). Using dataset analysis learned in previous courses (Artificial Intelligence, Data Analytics), we will discuss and interpret various areas of the movies, namely the sentiment ratios of character and corresponding movies. Using tools like Jupyter notebook, we will write an in-depth analysis related to what we know already of the movies/character and our report of the model reflects this. 
# I. INTRODUCTION 
## Context
This project is to introduce ourselves to big data manipulation in the context of a topic we are fond of, movies. We feel that movies have complexity that is lost during the viewing and can be interpreted with data analysis with a new eye. Indeed, we are all aware who the main characters are, their choice of words is usually what distinguishes them, aside from looks of course, and sentiment analysis can confirm our beliefs/disbeliefs. 
## Objectives
The objective of this project is to use the knowledge from previous courses to analyze these movies to understand specific story elements while testing different classification models and see which one is the best fit for our problem. We want, as team interested in superhero movies and data analysis, to observe if a non-neural classification model can detect the nuances of dialogue.
Not only does these nuances let us better understand the story but might affirm or deny our pre-assumption of these algorithms and mainstream superhero movies.
# II. MATERIALS AND METHODS
## The Datasets

1. [Marvel Cinematic Universe Dialogue Dataset](https://www.kaggle.com/pdunton/marvel-cinematic-universe-dialogue?select=mcu_subset.csv)
2. [Twitter and Reddit Sentimental analysis Dataset](https://www.kaggle.com/cosmos98/twitter-and-reddit-sentimental-analysis-dataset)

Kaggle was an excellent resource as an extended twitter dataset with labeled and movie scripts were found. The twitter dataset has nearly 136k tweets labeled from [-1, 0, 1] where -1 is a negative sentiment, 0 a neutral statement and 1 is for a positive statement.
On the other hand, the superhero movies scripts are pre-processed and separated by coma along with important information such as the character that said the line and in which movie. In this project we will mostly using a subset of the MCU dialogue found in the file mcu_subset.csv. In this file, the dialogue is filtered by the top 10 characters from the franchise (or main cast). These characters are:
```['TONY STARK', 'STEVE ROGERS', 'NATASHA ROMANOFF', 'THOR', 'NICK FURY', 'PEPPER POTTS', 'BRUCE BANNER', 'JAMES RHODES', 'LOKI', 'PETER PARKER']```
What are superheroes without their counterpart? In this project the following villains were considered:
```['THANOS', 'N\'JADAKA (KILLMONGER)', 'RED SKULL', 'BUCKY BARNES', 'ULTRON', 'HELA', 'RONAN', 'ADRIAN TOOMES']```
## Technologies
One of the main technologies we will be using is Jupyter Notebook with various libraries to correctly text mine, analyse and understand the words found in the script of the Marvel Movies. 
Spark was also used as the main framework our project, notably their machine learning package found in PySpark. The ease of use their data structures, more precisely its Dataframe, will ease our manipulation, visualization and reiteration of the data.
## Algorithms
Since this is a classification problem, the following classification model will used and explored:
- Multinomial Logistic Regression
- One Vs. All
- Random Tree Classifier
- Naive Bayes (If time allows it)
## Tidy Text Data/Data Pre-processing
The use of tidy text principles will enable us to both handle and interpret the data more efficiently. The tidy text format is quite specific and uses a table with one-token-per-row, in our case each row will be a line of dialogue based on character.  For the data pre-processing, we removed all null values and duplicates and stop words using PySpark’s StopWordsRemover, with the addition of our own set of stops words. From there we hashed the texts (tweets/dialogue) using HashingTF(), so it can be understood by the models.
## Libraries

Matplotlib, “a plotting library for the Python programming language and its numerical” [1], will be used in order to provide visualizations of the relationships of the sentiments. 
# III. Results

Before we endeavoured our project, we believe it important for any analysis to have pre-assumption or hypothesises of the results:
1. Movies are mostly neutral dialogue, our results should reflect this
2. Protagonists will have greater positive sentiments
3. Antagonists will have greater negative sentiments
We believe this can provide us with an analytic basis and render the discussion of the results more fruitful.
## Model Comparison 

<p align="center">
<img src="https://imgur.com/xBd44ax.jpg" width="85%" >
</p>

As seen above, from the three models that we explored, the One Vs All (a algorithms meant for multinomial classification using logistic regression) was the clear winner. Before explaining why, we think it performed best, we will delve into why the other two did so poorly in comparison later in section IV.

<p align="center">
<img src="https://imgur.com/YF5W1xm.jpg" width="85%" >
</p>

It is important to highlight that we initially attempted binomial logistic regression on a [negative, positive] labeled dataset in the first iterations of our project and it failed miserably. Not that the model was inaccurate, it is quite the opposite with it having a over 99% accuracy and F1-score. The problem lied when we applied the model to the MCU script, we had received highly skewed results in the negative prediction. This can be easily explained from the fact that movie dialogue inherently neutral and lead to the predictor believing that neutral dialogue was negative. This reason alone led our team to rework the code, seek multinomial classification methods and their respective dataset.


## Overall Sentiment of The Marvel Cinematic Universe

<p align="center">
<img src="https://imgur.com/TVxyrC8.jpg" width="85%" >
</p>

This is the result when the Multinomial Logistic Regression Model is applied to all the movies in the MCU. The pie chart distribution indicates a mostly neutral dialogue (57.6%), with the rest being mostly positive (26.7%) and little negative sentimental dialogue (15.7%).

## Sentiment Analysis Sorted by the Main Cast

<p align="center">
<img src="https://imgur.com/NSsFpkV.jpg" width="85%" >
</p>

When the model is applied to the main cast, there is interesting results shown. The most neutral character (per their dialogue) is Peter Parker (Spiderman). The most positive sentimental character is Nick Fury and the most negative is tied by Bruce Banner (The Hulk) and James Rhodes (War Machine).

## Sentiment Analysis Sorted by the Villain Cast

<p align="center">
<img src="https://imgur.com/UDCojvj.jpg" width="85%" >
</p>
The villains are also an interesting case. The only character that is morally ambiguous, Bucky Barnes, is highly neutral at 69.1% while the most positive character is Red Skull. The most negative is Hela. Of note, Thanos, the ultimate antagonist of the series of movies, ranks the lowest ratio in all categories, making him perfectly balanced in terms of sentiments (as all things should be).

## Sentiment Analysis Sorted by the Movies

<p align="center">
<img src="https://imgur.com/yorzSRV.jpg" width="90%" >
</p>
Although we believe these results are the least compelling, the sentiments are still relevant to our discussion and somewhat connected to the hypothesises. The greater amount of positive sentiment can be found in Captain America: Winter Soldier while the more negative Movie is Captain American: The First Avenger. The most neutral is Thor.
 


# IV. Discussion

For starters, let us discuss the three models used, it is known that One vs All was the better model, but why is the accuracy so low for the other contenders? Before that, I would like to preface that (to the team’s surprise) the accuracy scores for the logistic regression models were surprisingly high for a non-neural classification model. Speech and dialogue are complex set of combination of tone, meaning, delivery and word choice. The fact that our model was able to predict speech sentiment at a rate over 70% is rather impressive for a simpler classifier. 

From there we can start dissecting the results of the three models. It is believed that random tree classifier did poorly in our project due to the nature of language or speech. Random forest is based on combining multiple independent classifiers in which “bagging” lonely terms does not represent the whole sentence, thus it becomes harder to classify if we cannot compare to other labels.

This is the reason why the one vs. all classifier worked for our case since the labels [negative, neutral, positive] are better suited for relative comparison. For instance, the word “avenge” is a connoted word that would not pass as neutral in most classifying operation. Therefore, the simple multinomial logistic regression falls slightly behind because it is much harder to choose 3 cases in which a word belongs then relatively comparing it between 2.  Thus, an initial test set of neutral dialogue (like a movie script) benefits from the One vs. All Model. 

In terms of the movie analysis, our hypothesis that “protagonists will have greater positive sentiments” was affirmed by the main cast having a greater positive sentiment than a negative one. However, our hypothesis about the villain proved to be false and unsurprisingly demonstrated that these movies are intended to have a positive outlook on life no matter which side you choose.








## References
[1] https://en.wikipedia.org/wiki/Matplotlib
As a disclaimer, we were inspired by the following [project](https://www.kaggle.com/xvivancos/analyzing-star-wars-movie-scripts/report)
