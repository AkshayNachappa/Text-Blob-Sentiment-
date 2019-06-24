# Text-Blob-Sentiment-
visit itsaihub.com for more  tutorials 

In this tutorial we are going to collect data from twitter using Twitter API and predict the sentiment using textblob


Welcome to our second part of TOP 5 MACHINE LEARNING PROJECTS FOR BEGINNERS. In the previous part we had classified iris flower using KNN algorithm. You can go through the project if you havent gone through it before. click here

It takes a lot of time to create a project which can truly showcase the depth and breadth of your knowledge. So try to walk before you start to run. This project is most suitable for people who have a basic understanding of python and Machine Learning. Even if you are absolutely new to it, give it a try. And ask questions in Comments below. R users can refer to this equivalent R script and follow the explanation given below.

ABOUT SENTIMENT ANALYSIS USING TWEETS
This involved several stages:

Scrape their tweets
Run them through a natural language processor
Classify them with a machine learning algorithm
Use them to predict the sentiment
Characteristic features of Tweets
From the perspective of Sentiment Analysis, we discuss a few characteristics of Twitter:

Length of a Tweet The maximum length of a Twitter message is 140 characters. This means that we can practically consider a tweet to be a single sentence, void of complex grammatical constructs. This is a vast difference from traditional subjects of Sentiment Analysis, such as movie reviews.

Language used Twitter is used via a variety of media including SMS and mobile phone apps. Because of this and the 140-character limit, language used in Tweets tend be more colloquial, and filled with slang and misspellings. Use of hashtags also gained popularity on Twitter and is a primary feature in any given tweet.

Data availability Another difference is the magnitude of data available. With the Twitter API, it is easy to collect millions of tweets for training. There also exist a few datasets that have automatically and manually labelled the tweets.

Domain of topics People often post about their likes and dislikes on social media. These are not all concentrated around one topic. This makes twitter a unique place to model a generic classifier as opposed to domain specific classifiers that could be build datasets such as movie reviews.

Datasets
As more and more users post about products and services they use, or express their political and religious views, micro-blogging web-sites become valuable sources of people’s opinions and sentiments. Such data can be efficiently used for marketing or social studies.

Twitter API
Twitter Dataset
TextBlob is a Python (2 and 3) library for processing textual data. It provides a simple API for diving into common natural language processing (NLP) tasks such as part-of-speech tagging, noun phrase extraction, sentiment analysis, classification, translation, and more.

As this is the project for beginners, we are going to use textblob, library for processing textual data. You can also use some other machine learning algorithms like Naive Bayes, SVM, CNN and many more once you get used to it.

In this tutorial we are going to collect data from twitter using Twitter API. First you need to create twitter developer account. Lets dive into the program and tutorials.

Installation Required
Twitter API : pip install TwitterAPI
Tweepy : pip install tweepy
Re : pip install re2
TextBlob : pip install textblob
All new developers must apply for a developer account to access Twitter APIs. Once approved, you can begin to use standard APIs and new premium APIs.

from textblob import TextBlob
import tweepy
import re
from API_tweeter import Consumer_Key,Consumer_Secret,Access_Token,Access_Token_Secret
All the modules and libraries should first be imported. If you haven't installed it yet follow the instruction in above installation section. We assume you have installed all the requisites, so lets move on further.

consumerKey = "###################"
consumerSecret = "################"
accessToken =  "#######################"
accessTokenSecret = "#####################"
You can get these keys from Twitter Developer account . Click here

auth = tweepy.OAuthHandler(consumer_key=consumerKey,consumer_secret=consumerSecret)
auth.set_access_token(key=accessToken,secret=accessTokenSecret)
api = tweepy.API(auth,wait_on_rate_limit=True)
Here we authenticate the keys and link it to twitter account.

searchTerm = input("Enter the keyword/hastag to search :")
noOfTwites = int(input("Enter how many tweets to analyze: "))
You can enter the number of tweets and the terms which to be searched.

tweets = tweepy.Cursor(api.search,q=searchTerm+" -rt",lang = 'en',
                       result_type="popular",count = noOfTwites).items(noOfTwites)
for tweet in tweets:
    remove_http_tweet = re.sub(r"http\S+","",tweet.text)
    clean_tweet = " ".join(re.findall("[a-zA-Z]+",remove_http_tweet))
    analysis = TextBlob(clean_tweet).sentiment.polarity
    print("tweet")
    print(clean_tweet)
    print("Sentiment",analysis)
    print(20*"==")
Here we remove the URL links, emoji and analyze the sentiments of the tweets using TextBlob. You can use VaderSentiment if you want to include emojis while analysing the sentiment.

In our next tutorial we will be writing about Stock prediction. Keep spreading love.
