# GA-DSI-Project-03

## Summary

The objective of this project was to use web APIs to download posts from 2 subreddits, to pre-process and explore the data using Natural Language Processing, and finally to classify each post according to which subreddit it came from using several combinations of vectorizers and classifiers.

The subreddits chosen for this project were [r/TalesFromTheCustomer](https://www.reddit.com/r/TalesFromTheCustomer) and [r/TalesFromYourServer](https://www.reddit.com/r/TalesFromYourServer)

'r/TalesFromTheCustomer' posts generally comprise accounts of poor customer service encountered by contributors.

'r/TalesFromYourServer' posts mainly comprise contributions from people who work(ed) as waiters/waitresses regarding unreasonable customers they encountered at work.

The lexicon/vocabulary in both types of posts are very similar. Hence, the challenge is to create a model that relies not only individual words, but also multi-word sequences to tell the posts apart.

## Data

About 1,000 posts from each subreddit were downloaded. So approximately 2,000 rows of data were available to work with. All data were then stripped of HTML tags (if any) and punctuation. The posts were also changed to lowercase.

## General Approach

The following were carried out in different combinations:

1) Pre-processing<br>
Lemmatization of words, removal of stopwords, and removal of single characters (if not a stop-word).<br>
NLTK and spaCy libraries were used.

2) Vectorization<br>
Count vectorizer and TFIDF vectorizer were used.<br>

3) Classification<br>
Logistic Regression and Nive Bayes (Multinomial) were used.<br>

For each combination of the above, GridSearch was used iteratively to find the optimum parameters.

## Project Submission
The submission comprises 2 jupyter notebooks:

##### 01 collect data from reddit.ipynb
- Downloading of subreddit posts and saving these into their respective files.

##### 02 EDA, Models and Evaluation.ipynb
- Pre-processing and exploration of data
- Models and evaluation
- Findings and Conclusion

## Evaluation
The model that yielded the highest accuracy of 0.895 and ROC AUC of 0.955 was Model No. 4^ comprising:
- TFIDF Vectorizer (min_df=3, max_df=0.6, ngram_range=(1,3), max_features=3000)
- Naive Bayes Multinomial (alpha=0.7)
- Document pre-processing: remove punctuation, change to lowercase, remove HTML tags
- Single words, bi-grams and tri-grams were included in the feature set for classification.
