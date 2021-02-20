# Big-Data

## ABSTRACT

For this SOEN471 project, we will be analyzing, in a team of two people, the scripts of the Avenger Movies (The Avengers, Age of Ultron, Infinity War and Endgame). Using dataset analysis learned in previous courses (Artificial Intelligence, Data Analytics), we will discuss and interpret various areas of the movies, namely the frequency of the words used in dialogue. Using tools like Jupyter notebook (or R notebook), we will write an in-depth analysis related to the following topics with their corresponding graphical representation: importance of the characters, bigram frequencies, sentiment analysis.

As a disclaimer, we were inspired by the following [project](https://www.kaggle.com/xvivancos/analyzing-star-wars-movie-scripts/report)

## INTRODUCTION 

### Context
This project is to introduce ourselves to big data manipulation in the context of a topic we are fond of, movies. We feel that movies have complexity that is lost during the viewing and can only be interpreted with data analysis. Indeed, we are all aware who the main characters are, their choice of words is usually what distinguishes them, aside from looks of course.

### Objectives
The objective of this project is to use the knowledge from previous courses to analyze these movies to understand specific story elements. We want, as team of particularly interested in movies and data analysis, the intricacies of dialogue first and foremost. Not only does these nuances let us better understand the story but might affirm or deny our pre-assumption of these four blockbuster and mainstream superhero movies.

### Analysis
We have settled on specific analysis point, which may be subject to change (depending on the complexity of the Avenger Movies):

* Lines of dialogue per character
* Lines of dialogue per character from each movie
* Sentiment Analysis (How many words belong to a specific sentiment i.e., joy, sadness, anticipation…)
* Sentiment Analysis across all 4 movies
* Most frequent sentiment words for each category
* Sentiment count for each character
* Most frequents words found in each movie.
* Most frequent words for each character
* Optional: Gender Analysis

One of the key reasons we chose this project was because of the sentiment analysis from the project we were inspired. As a team that previously studied Artificial Intelligence, classified and labeled data is in our comfort zone. More on this type of analysis will be detailed in the libraries section.

## MATERIALS AND METHODS

### The Datasets

As the dataset is not publicly available as a parsable file, we will first need to gather the movie scripts from online sources and parse them into a distinguishable format for our code. The scripts will have to be pre-processed in order to reduce the amount of noise within the datasets, for example, removing commonly used words, white space, and numbers. From then, dialogue associated with their respective character will only be needed for the rest of the analysis.

### Technologies
One of the main technologies we will be using is Jupyter Notebook with various libraries to correctly text mine, analyse and understand the words found in the script of the Avengers movies series, not to be confused with the Infinity Saga (Which include all recent Marvel Movies). 

### Tidy Text Data
The use of tidy text principles will enable us to both handle and interpret the data more efficiently. The tidy text format is quite specific and uses a table with one-token-per-row, in our case each row will be a line of dialogue based on character. Tidy text will allow us to efficiently calculate the frequency of words for each Avenger film. It will also be used to determine the most frequent unigrams, bi-grams and trigrams, this can then be broken down further by character. 

### Libraries
Various libraries will be used for sentiment analysis including AFINN, bing, and NRC. All these lexicons contain English words that have an associated positive/negative value as well as possible related emotions.
The AFINN library assigns words with a score between -5 and 5, with negative scores referring to negative sentiments and vice versa. The bing library categorizes words in a binary fashion, into positive and negative categories. Lastly, the NRC library also categorizes words in a binary fashion, however they are categorized into positive, negative, anger, anticipation, disgust, fear, joy, sadness, surprise and trust.
Bigrams will be used for sentiment analysis to also provide context, because many words will be associated with positive sentiments even though that may not be the case. For instance, many words may be preceded by negating words, which would change the sentiment, therefore we will analyse the bi-grams and filter the ones that start with negating words. This will hopefully, provide a more accurate representation for our sentiment analysis.
The graph library will also be used in order to provide visualizations of bigrams and show the relations between various clusters of words. Other libraries such as ggplot and wordcloud2 will also be used mainly to provide visual representations of the data obtained from the text mining analysis. 

