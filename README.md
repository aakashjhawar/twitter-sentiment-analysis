# Twitter Sentiment Analysis
Sentimental analysis of tweets to detect racist/sexist tweets using Bag of Words, TF-IDF Features, Word2Vec and Doc2Vec.

## Requirements
* Python
* Tweepy
* TextBlob
* Pandas
* nltk (text manipulation)
* re ()

## Dependencies
1. Install TextBlob `pip install -U textblob`
2. Additional Dependency `python -m textblob.download_corpora`

## How to use
```
git clone git@github.com:aakashjhawar/twitter-sentiment-analysis.git
cd twitter-sentiment-analysis
```
Open the jupyter notebook file.

## Comparision

Accuracy of Bag of Words, TF-IDF Features, Word2Vec and Doc2Vec over Logistic Regression, Support Vector Machine(SVM), Random Forest and XGBoost classifier.

| Classifier | Bag of Words | TF-IDF Feature | Word2Vec | Doc2Vec |
| ---------- | ------------ | -------------- | -------- | ------- |
| Logistic Regression | 53.05% | 54.46% | 61.72% | 36.9% |
| Support Vector Machine | 50.6% | 51% | 61.30% | 19.32% |
| Random Forest | 53.29% | 56.21% | 50.2% | 65.06% |
| XGBoost | 51.30% | 51.85% | 64.54% | 34.83% |

## Steps
### Data Inspection
![Dataset](https://github.com/aakashjhawar/twitter-sentiment-analysis/blob/master/images/dataset.png)

### Data Cleaning
1. Remove @user from tweets
2. Remove punctuations and numbers from tweets 
`replace("[^a-zA-Z#]", " ")`
3. Remove words whose length is less than 3 `word < str.len(3)`
4. Text Normalization using PorterStemmer()

Porter Stemmer
* Tokenize the tweets
* Normalize the tweets
* Stich it back using nltk's [Moses Detokenizer](https://www.nltk.org/_modules/nltk/tokenize/moses.html)

![Dataset cleaned](https://github.com/aakashjhawar/twitter-sentiment-analysis/blob/master/images/tweets_comparision.png)

### Story Generation
Most common words
![Word Cloud](https://github.com/aakashjhawar/twitter-sentiment-analysis/blob/master/images/wordcloud.png)

Most Popular Hashtags
![Dataset cleaned](https://github.com/aakashjhawar/twitter-sentiment-analysis/blob/master/images/hashtags.png)

### Bag of Words Features
Bag of Words (BOW) is a method to extract features from text documents. These features can be used for training machine learning algorithms. It creates a vocabulary of all the unique words occurring in all the documents in the training set.
In simple terms, it’s a collection of words to represent a sentence with word count and mostly disregarding the order in which they appear.

### TF-IDF Features
Term Frequency-Inverse Document Frequency. It Penalise the most common words by assigning them lower weights while giving imortance to words which are rare in corpus but apper in good number in few documents.

> TF = (Number of times term 't' appears in a doc) / (Number of terms in doc)
> IDF = log(N/n) 
> where, N = number of document 
> n = number of documents a term 't' has appeared in
> TF-IDF = TF*IDF
 





