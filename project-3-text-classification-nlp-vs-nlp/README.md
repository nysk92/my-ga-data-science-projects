# Problem

When wanting to do a google search for material on natural language processing, one would instinctively type in 'nlp', the common abbreviation. However, doing so results in a lot of search results for the other thing 'nlp' stands for, neuro linguistic programming. This can be frustrating. Simply searching with the additional terms 'natural language processing' to overcome this is firstly tedious, and secondly is not guaranteed to return all relevant results because not all content about natural language processing would spell it out. This content could simply be talking directly about a subtopic (like text classification), or would use the abbreviation 'nlp' and not the long form. 

With this problem in mind, a text classifier could be a potential solution to help automatically distinguish between the two. Success would mean being able to filter out content about neuro-lingusitic programming and also not losing any content about natural language processing or adjacent topics like machine learning along the way.


# Methodology

1. Scrape data from the Language Technology (natural language processing) and NLP (neuro-linguistic programming) subreddits. The data can be found [here](../project-3-text-classification-nlp-vs-nlp/data).


2. [Clean data](../project-3-text-classification-nlp-vs-nlp/code/01_Data_Cleaning_and_EDA.ipynb) and featurize with Count Vectorizer/Tfidf Vectorizer. Try out stemming and lemmatization, and stopword removal as preprocessing steps.


3. Train a binary classification model that can distinguish between posts about natural language processing (1) vs neuro-linguistic programming (0). This and the next step is done in [Notebook 2](../project-3-text-classification-nlp-vs-nlp/code/02_Models.ipynb).


4. Iterate, evaluating against hold out test set, and on top of that, against a dataset of related topics, also scraped from reddit. For Language Technology, the related topic data would be from the Deep Learning subreddit. For Neuro-Linguistic Programming, the related topic data would be from the Hypnosis subreddit. A model trained to distinguish between Neuro Linguistic Programming and Natural Language Processing would prove itself to be all the more useful if it can also distinguish between the respective adjacent topics.



# Models

|   Model No. | Classifier             | Vectorizer      | Hyperparams                                                                                                                                                                                    |   Train Accuracy |   Test Accuracy |   Test F1 |   Related Topic Accuracy | Comments   |
|------------:|:-----------------------|:----------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------:|----------------:|----------:|-------------------------:|:-----------|
|           1 | LogisticRegression     | CountVectorizer | {'cvec__max_df': 0.9, 'cvec__min_df': 4, 'cvec__ngram_range': (1, 2), 'cvec__preprocessor': <function preproc at 0x7ffd44dba8b0>, 'lr__C': 1}                                                  |         0.992283 |        0.930591 |  0.928382 |                 0.847862 |            |
|           2 | LogisticRegression     | TfidfVectorizer | {'lr__C': 1, 'tvec__max_df': 0.9, 'tvec__min_df': 4, 'tvec__ngram_range': (1, 2), 'tvec__preprocessor': <function preproc_no_stem at 0x7ffd408b11f0>}                                          |         0.982637 |        0.946015 |  0.946292 |                 0.917268 |            |
|           3 | MultinomialNB          | CountVectorizer | {'cvec__max_df': 0.9, 'cvec__min_df': 2, 'cvec__ngram_range': (1, 2), 'cvec__preprocessor': <function preproc at 0x7ffd44dba8b0>, 'nb__fit_prior': False}                                      |         0.976206 |        0.946015 |  0.946015 |                 0.928373 |            |
|           4 | MultinomialNB          | TfidfVectorizer | {'nb__fit_prior': False, 'tvec__max_df': 0.9, 'tvec__min_df': 2, 'tvec__ngram_range': (1, 2), 'tvec__preprocessor': <function preproc at 0x7ffd44dba8b0>}                                      |         0.984566 |        0.951157 |  0.953317 |                 0.938368 |            |
|           5 | KNeighborsClassifier   | CountVectorizer | {'cvec__max_df': 0.9, 'cvec__min_df': 4, 'cvec__ngram_range': (1, 2), 'cvec__preprocessor': <function preproc at 0x7ffd44dba8b0>, 'knn__n_neighbors': 3, 'knn__p': 2}                          |         0.823151 |        0.727506 |  0.651316 |                 0.62965  |            |
|           6 | KNeighborsClassifier   | TfidfVectorizer | {'knn__n_neighbors': 3, 'knn__p': 2, 'tvec__max_df': 0.9, 'tvec__min_df': 4, 'tvec__ngram_range': (2, 3), 'tvec__preprocessor': <function preproc_no_stem at 0x7ffd408b11f0>}                  |         0.900965 |        0.70437  |  0.650456 |                 0.635758 |            |
|           7 | RandomForestClassifier | CountVectorizer | {'cvec__max_df': 0.9, 'cvec__min_df': 2, 'cvec__ngram_range': (1, 2), 'cvec__preprocessor': <function preproc at 0x7ffd44dba8b0>, 'rf__bootstrap': False, 'rf__max_depth': None}               |         1        |        0.928021 |  0.930348 |                 0.850083 |            |
|           8 | RandomForestClassifier | TfidfVectorizer | {'rf__bootstrap': False, 'rf__max_depth': None, 'tvec__max_df': 0.95, 'tvec__min_df': 2, 'tvec__ngram_range': (1, 2), 'tvec__preprocessor': <function preproc_no_stem at 0x7ffd408b11f0>}      |         1        |        0.943445 |  0.944444 |                 0.855081 |            |
|           9 | SVC                    | CountVectorizer | {'cvec__max_df': 0.9, 'cvec__min_df': 2, 'cvec__ngram_range': (1, 2), 'cvec__preprocessor': <function preproc at 0x7ffd44dba8b0>, 'sv__C': 1, 'sv__degree': 3, 'sv__kernel': 'linear'}         |         0.999357 |        0.899743 |  0.896    |                 0.805108 |            |
|          10 | SVC                    | TfidfVectorizer | {'sv__C': 1, 'sv__degree': 3, 'sv__kernel': 'linear', 'tvec__max_df': 0.9, 'tvec__min_df': 2, 'tvec__ngram_range': (1, 2), 'tvec__preprocessor': <function preproc_no_stem at 0x7ffd408b11f0>} |         0.994855 |        0.938303 |  0.938776 |                 0.912826 |            |
|          11 | XGBClassifier          | CountVectorizer | {'cvec__max_df': 0.9, 'cvec__min_df': 2, 'cvec__ngram_range': (1, 2), 'cvec__preprocessor': <function preproc_no_stem at 0x7ffd408b11f0>, 'xgc__max_depth': 5, 'xgc__n_estimators': 100}       |         0.970418 |        0.935733 |  0.934726 |                 0.844531 |            |
|          12 | XGBClassifier          | TfidfVectorizer | {'tvec__max_df': 0.9, 'tvec__min_df': 4, 'tvec__ngram_range': (1, 4), 'tvec__preprocessor': <function preproc at 0x7ffd44dba8b0>, 'xgc__max_depth': 2, 'xgc__n_estimators': 200}               |         0.971704 |        0.935733 |  0.934383 |                 0.838978 |            |



# Conclusion

1. The best model for prediction is multinomial naive bayes classifier with tifidf vectorizer (model 4), and it has proven to generalise well to distinguishing adjacent topics too. This shows promise that the classifier has the potential to learn from a wider range of natural language processing topics to be able to classify beyond the limited language technology reddit subset of vocabulary it has trained on.


2. Separating neuro-linguistic programming content from natural language processing content appears to be a very achievable task, however, the highest weighted features of the best models are slightly worrying in that they do not seem to be words that very obviously distinguish the two classes. (might not be a bad thing, that is why we have ML). More work can definitely be done to improve the model to be ready for a wider range of natural language processing topics. Moving forward, it would be helpful scrape a larger variety of training data that covers a wider range of vocabulary for both topics. 


3. Although the intuition is that the two topics can be separated by a few obvious terms, the model performance and coefficients indicate that better prediction comes from learning from a wider variety of features.
