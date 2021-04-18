
# ABSTRACT

For this SOEN471 project, we will create a Sentiment Analysis Model that will be developed based on a Twitter dataset. This model will then be used to analyze, in a team of two people, the scripts of the Marvel Cinematic Universe Movies (Notably the Avengers and The Iron Man Franchise). Using dataset analysis learned in previous courses (Artificial Intelligence, Data Analytics), we will discuss and interpret various areas of the movies, namely the sentiment ratios of character and corresponding movies. Using tools like Jupyter notebook, we will write an in-depth analysis related to what we know already of the movies/character and our report of the model reflects this. 


# I. INTRODUCTION 

## Context
This project is to introduce ourselves to big data manipulation in the context of a topic we are fond of, movies. We feel that movies have complexity that is lost during the viewing and can be interpreted with data analysis with a new eye. Indeed, we are all aware who the main characters are, their choice of words is usually what distinguishes them, aside from looks of course, and sentiment analysis can confirm our beliefs/disbeliefs. 

## Objectives
The objective of this project is to use the knowledge from previous courses to analyze these movies to understand specific story elements while testing different classification models and see which one is the best fit for our problem. We want, as team interested in superhero movies and data analysis, to observe if a non-neural classification model can. 
detect the nuances of dialogue.
Not only does these nuances let us better understand the story but might affirm or deny our pre-assumption of these algorithms and mainstream superhero movies.

# II. MATERIALS AND METHODS

## The Datasets

As the dataset is not publicly available as a parsable file, we will first need to gather the movie scripts from online sources and parse them into a distinguishable format for our code. The scripts will have to be pre-processed in order to reduce the amount of noise within the datasets, for example, removing commonly used words, white space, and numbers. From then, dialogue associated with their respective character will only be needed for the rest of the analysis.

## Technologies
One of the main technologies we will be using is Jupyter Notebook with various libraries to correctly text mine, analyse and understand the words found in the script of the Avengers movies series, not to be confused with the Infinity Saga (Which include all recent Marvel Movies). 

## Tidy Text Data
The use of tidy text principles will enable us to both handle and interpret the data more efficiently. The tidy text format is quite specific and uses a table with one-token-per-row, in our case each row will be a line of dialogue based on character.

## Libraries
Various libraries will be used for sentiment analysis including AFINN, bing, and NRC. All these lexicons contain English words that have an associated positive/negative value as well as possible related emotions.
The AFINN library assigns words with a score between -5 and 5, with negative scores referring to negative sentiments and vice versa. The bing library categorizes words in a binary fashion, into positive and negative categories. Lastly, the NRC library also categorizes words in a binary fashion, however they are categorized into positive, negative, anger, anticipation, disgust, fear, joy, sadness, surprise and trust.
Bigrams will be used for sentiment analysis to also provide context, because many words will be associated with positive sentiments even though that may not be the case. For instance, many words may be preceded by negating words, which would change the sentiment, therefore we will analyse the bi-grams and filter the ones that start with negating words. This will hopefully, provide a more accurate representation for our sentiment analysis.
The graph library will also be used in order to provide visualizations of bigrams and show the relations between various clusters of words. Other libraries such as ggplot and wordcloud2 will also be used mainly to provide visual representations of the data obtained from the text mining analysis. 

# III. Results

Before endeavouring into the project, we believe it important for any analysis to have pre-assumption or hypothesises of the results:


- Movies are mostly neutral dialogue, our results should reflect this
- Protagonists will have greater positive sentiments
- Antagonists will have greater negative sentiments

## Model Comparison 

![image](https://imgur.com/xBd44ax.jpg)
![image](https://imgur.com/YF5W1xm.jpg)

### Overall Sentiment of The Marvel Cinematic Universe

![image](https://imgur.com/TVxyrC8.jpg)

### Sentiment Analysis Sorted by the Main Cast

![image](https://imgur.com/NSsFpkV.jpg)

### Sentiment Analysis Sorted by the Villain Cast

![image](https://imgur.com/UDCojvj.jpg)

### Sentiment Analysis Sorted by the Movies

![image](https://imgur.com/yorzSRV.jpg)

# IV. Discussion

## References

As a disclaimer, we were inspired by the following [project](https://www.kaggle.com/xvivancos/analyzing-star-wars-movie-scripts/report)
