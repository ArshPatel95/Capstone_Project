# Capstone_Project
 
Project using NLP to determine how effectively ML programs can determine whether tweets by prominent politicians are from the left or right, and if so, how effectively they can distinguish between moderates and partisans in each faction


## Overview

This project was a sentiment analysis and classifier of tweets by prominent politicians in the US Congress and the last two Presidents. The purpose of this project was to see how effective I could make the classifier and if I could use sentiment analysis to see the difference in the text of the tweets between different groups.


## Web Scraping 

I web scraped over 380,000 tweets from prominent members of Congress and the last two presidents. I scraped all tweets from these politicians since 2017, when President Trump was inaugurated, beginning a new era of American politics. These tweets in the dataset were categorized into two groups, the two political parties (Democrats and Republicans) and four factions (Liberal Democrats, Conservative Republicans, Moderate Republicans, Moderate Democrats).


## Text Preprocessing

I preprocessed the tweets using basic NLP text-cleaning practices for tweets. The only major difference is that I used my own set of stopwords, removing many negative words that are considered standard for NLP stopwords. I did this as I had an intuition that as many political tweets are made in reference to other politicians, that many political tweets may have a negative connotation that may be lost if negative stop words were stripped from the data. I also removed tweets from the final dataset that had less than 8 tokens. This left us with a final dataset of roughly 325,000 tweets. 


## Sentiment Analysis

I used VADER to find the sentiment score of all tweets for each faction. I found that overall, there was an inverse relationship between whether a President was a member of a political party, and the sentiment score of the opposing party. For example, the sentiment score of Republicans tweets became more negative after Biden became President.

I also created word clouds for all factions and the parties to see if there were differences in the vocabulary between different parties and factions. Overall, there were very slight variations, but one notable takeaway was that moderate Republicans and Democrats talk about bipartisanship more often than more partisan politicians. 


## Classifier 

My first classifier was a binary classifier for the two parties. My first model was a Multinomial Naive Bayes using a CountVectorizer. This model only had an AUC of 64%. After model tuning, I found that the best classifier to use was a hypertuned random forest with a TfidfVectorizer. This final binary classifier had a F1 score of 84%. 

My first classifier was a multiclass classifier for the four factions. My first model was a Multinomial Naive Bayes using a CountVectorizer. This model only had an AUC of 44%. After model tuning, I found that the best classifier to use was a hypertuned random forest with a TfidfVectorizer. This final binary classifier had a F1 score of 71%. Curiously, looking at the results, it seems the model had trouble distinguishing between moderates and partisans of each party.


## Conclusion

The purpose of this project was to look at the tweets of prominent politicians and see whether or not a ML model could determine the category of a political tweet simply using NLP methods. Overall, this project was quite successful. 

Sentiment analysis was also used to see if we could uncover any meaningful differences between the tweets of different groups. Using sentiment analysis we could see that partisans tend to be more negative than moderates, and that the tweets of politicians would become more negative when the President was a member of the opposing party. We could also see that moderates mentioned bipartisanship more than partisans. 

Our binary classifier could identify the party affiliation of 84% of tweets, and our multiclass classifier could identify the political faction of each tweet with an accuracy up to 71%. Using sentiment analysis we could see that partisans tend to be more negative than moderates, and that the tweets of politicians would become more negative when the President was a member of the opposing party.
