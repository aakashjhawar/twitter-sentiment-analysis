# Twitter Sentiment Analysis
Sentimental analysis of tweets to detect racist/sexist tweets using Bag of Words, TF-IDF Features, Word2Vec and Doc2Vec.

## Requirements
* Python
* Tweepy
* TextBlob
* Pandas
* nltk

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