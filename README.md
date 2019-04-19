# Twitter Sentiment Analysis
Sentimental analysis of tweets to detect racist/sexist tweets using Bag of Words, TF-IDF Features, Word2Vec and Doc2Vec.

## Requirements
* Python
* Tweepy
* TextBlob
* Pandas
* nltk (text manipulation)
* re (regular expression)

## Dependencies
1. Install TextBlob `pip install -U textblob`
2. Additional Dependency `python -m textblob.download_corpora`

## How to use
```
git clone git@github.com:aakashjhawar/twitter-sentiment-analysis.git
cd twitter-sentiment-analysis
```
Open the jupyter notebook file.

## Procedure
### 1. Data Inspection
![Dataset](https://github.com/aakashjhawar/twitter-sentiment-analysis/blob/master/images/dataset.png)

### 2. Data Cleaning
1. Remove @user from tweets
2. Remove punctuations and numbers from tweets 
`replace("[^a-zA-Z#]", " ")`
3. Remove words whose length is less than 3 `word < str.len(3)`
4. Text Normalization using Porter Stemmer

Porter Stemmer
* Tokenize the tweets
* Normalize the tweets
* Stich it back using nltk's [Moses Detokenizer](https://www.nltk.org/_modules/nltk/tokenize/moses.html)

![Dataset cleaned](https://github.com/aakashjhawar/twitter-sentiment-analysis/blob/master/images/tweets_comparision.png)

### 3. Story Generation
##### Most common words
![Word Cloud](https://github.com/aakashjhawar/twitter-sentiment-analysis/blob/master/images/wordcloud.png)


##### Most Popular Hashtags
![Dataset cleaned](https://github.com/aakashjhawar/twitter-sentiment-analysis/blob/master/images/hashtags.png)

### Bag of Words Features
Bag of Words (BOW) is a method to extract features from text documents. These features can be used for training machine learning algorithms. It creates a vocabulary of all the unique words occurring in all the documents in the training set.
In simple terms, it’s a collection of words to represent a sentence with word count and mostly disregarding the order in which they appear.

### TF-IDF Features
Term Frequency-Inverse Document Frequency. It Penalise the most common words by assigning them lower weights while giving imortance to words which are rare in corpus but apper in good number in few documents.

> TF = (Number of times term 't' appears in a doc) / (Number of terms in doc)
>
> IDF = log(N/n) 
>
> where, N = number of document 
>
> n = number of documents a term 't' has appeared in
>
> TF-IDF = TF*IDF


### Word2Vec Features
It represents each word as a vector(Word Emebddings). The objective is to redefine high dimensional word features into low dimensional features by preserving contexual similarity in corpus.

Example
> King - Man + Woman = Queen

###### Similar words using Word2Vec
![similar image](https://github.com/aakashjhawar/twitter-sentiment-analysis/blob/master/images/similar_words.png)


Advantages> 
* Dimensionality reduction: Significant reduction in number of features
* It captures the meaning of word i.e., semantic erlations and different types of context

Word2Vec is combination of two algorithms:
* [CBOW - Continous Bag of Words](https://iksinc.online/tag/continuous-bag-of-words-cbow/): Predict probability of given context
* [Skip-Gram Model](https://www.kdnuggets.com/2018/04/implementing-deep-learning-methods-feature-engineering-text-data-skip-gram.html): Capture different semantic for sigle word. eg. Apple is company as well as fruit.
 

Both are shallow Neural Network. They map words to target variables which are also words.

### Doc2Vec Features
Unsupervised algorithm to generate vector for sentence, paragraph and documents.
 It provides an additional context which is unique for every document in corpus.
 Doc vector is trained along with Word vector.

To implement Doc2Vec Algorithm, labelize/tag each tokenised tweet with unique ids. ([Genism's LabledSentence](https://radimrehurek.com/gensim/models/doc2vec.html))

### 4. Modeling
Evaluation Matrix: F1 score is used as EM. It is weighed average of Precision and Recall.

### Fine tuning XGBoost + Word2Vec
General approach for parameter tuning
1. Choose relatively high learning rate (0.3 usually)
2. Tune tree-specific parameters, eg. max_depth, min_child_weight, subsample etc.
3. Tune learning rate
4. Finally tune gamma to avoid overfitting


## Results

Accuracy of Bag of Words, TF-IDF Features, Word2Vec and Doc2Vec over Logistic Regression, Support Vector Machine(SVM), Random Forest and XGBoost classifier.

| Classifier | Bag of Words | TF-IDF Feature | Word2Vec | Doc2Vec |
| ---------- | ------------ | -------------- | -------- | ------- |
| Logistic Regression | 53.05% | 54.46% | 61.72% | 36.9% |
| Support Vector Machine | 50.6% | 51% | 61.30% | 19.32% |
| Random Forest | 53.29% | 56.21% | 50.2% | 65.06% |
| XGBoost | 51.30% | 51.85% | 64.54% | 34.83% |


#### XGBoost + Word2Vec gives best F1 score of 64.54%.
