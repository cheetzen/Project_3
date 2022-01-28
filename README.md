
# GA Project 3 - How to use machine learning to accurately classify posts from Aliens subreddit and Space subreddit.

### Background
Men In Black (MIB) is an association that researches & promotes extraterrestrial knowledge. MIB sent a request to us, the Reddit data science team, to create a model to classify reddit posts and identify the key words that characterizes the post as "Aliens" from "Space". This would facilitate MIB's intelligence collection efforts about sentiments from ordinary citizens and promote its marketing effort on social media, events and podcasts.



### Problem Statement
The goal of the project is to create an accurate classification model and discover the key words that best differentiates posts related to "Aliens" from "Space" in reddit.

Three classification models, Naive Bayes, Logistic Regression and Random Forest will be developed to assist with the problem statement.

The success of the model will be assessed based on its accuracy and F1 score on unseen test data.

The primary stakeholder is Man In Black since we are addressing their request to seggregate aliens posts from space posts for marketing purposes. Secondary stakeholders such as UFO or Space enthutiasts would also benefit from such analysis because they can pay more attention to top words used in their respective discussion groups, to make sure they understand the hot topics that are being discussed.

### Data collection

1. Use api.pushshift to scrap posts from Aliens and Space subreddit respectively
2. Scrap 100 posts each time due to api limit and incorporated rest time of 3 seconds to considering the traffic.
3. Total scrapped 2,100 posts from each subreddit, export as csv file for subsequent cleaning. 



### Data Dictionary

|Feature|Type|Description|
|---|---|---|
|title|*object*|title of the post|
|selftext|*object*|text of the post|
|reddit|*bool*|aliens = 1, space = 0|
|post|*object*|title + selftext|

### EDA and cleaning data

**aliens_raw.csv**: This dataframe contains 2100 rows (i.e. posts) and 82 columns (i.e. features on the posts)

**space_raw.csv**: This dataframe contains 2100 rows (i.e. posts) and 80 columns (i.e. features on the posts)

1. Keep only useful features i.e. title, selftext, types of Reddit
2. Identify and remove meaningless word such as "[removed]" or "[deleted]".
3. Identify missing values in title or selftext features
4. Combine title and selftext into a single columns as post column
5. Identify outliers by using boxplot and remove outliers
6. Check distribution, word counts of aliens and space Reddit after cleaning
7. Check top words in each aliens and space Reddits to explore unique top words to address problem statement

### Preprocessing and Modeling

1. Tokenise posts into word and non-english words
2. Further cleaning by coverting all words into lower case and remove non-english words
3. Lemmatize words
4. Split train and test dataset
5. Train and score 3 different models, i.e. MultinomialNB, Random Forest and Logistic Regression with 2 different vectorizers i.e. Countvectorizer and TFIDF, total 6 pipelines
6. Evaluate train score, test score and F1 score on each of the 6 models
7. Select Logistic Regression as baseline model parameter tuning

### Evaluation and Conceptual Understanding

1. Perform parameter tuning on Logistic Regression (with Countvectorizer and TFIDF)
2. Evaluate and select Logistic Regression with TFIDF to be the best model in address the problem Statement
3. Explain feature importance of the model
4. Identify top 20 words with most influential power in determining the classification of aliens or space

### Conclusion and Recommendation

1. Logistic Regression with TFIDF is the best model to classify posts into aliens or space subreddit with good interpretability, with higher than 90% accuracy and F1 score
2. Posts that contain words like aliens, UFO, human, species are more likely to be from aliens subreddit
3. Posts that contain words like space, JWST, telescope, webb are more likely to be from space subreddit

We plan to incorporate the following areas into future work:
 - Image analysis, for wider scope (include both text and image)
 - Sentiment analysis, for gauging public feeling towards aliens (positive or negative)
 - Topic modelling, for more detailed understanding of the topic


### References

Aliens subreddit - https://www.reddit.com/r/aliens/  
Space subreddit - https://www.reddit.com/r/space/
