![Fakenews](Images/Fakenews.jpeg)

# Fake News Detction Model
**Author**: [Ji Hoon Chung](mailto:jhj1650@gmail.com)

## Business Problem

We are living in an unprecedented era where we are easily being exposed to tons of news on social media which we did not intend to spot. From premature juveniles to mature adults with higher degrees of education, fake news could easily deprive their factual senses and having them fallen down to imperfect beliefs.

Accordingly, it is crucial for social media platforms to detect fake news automatically to prohibit their exposure in the first place.

Our clients are Social Media Platforms like Facebook, Twitter, and LinkedIn. I would like to introduce a machine learning model being able to classify fake news aside from actual news using the words and patterns that are prevalent in conventional news dataset.

## Overview

Dataset is obtained from source: https://drive.google.com/file/d/1er9NJTLUA3qnRuyhfzuN0XUsoIC4a-_q/view

I’ve collected a dataset which includes 6,335 rows of data containing 3,171 real news vs 3,164 fake news. Dataset is very straight forward containing only 3 columns such as, title, text (article contents), and label indicating real or fake.

Machine Learning Model will be built after tweaking the dataset as below:

1. Text Data will be combined with Title.
2. 2nd column will be created with lemmmatized text.
3. 3rd column will be created with stemmed text.
4. Dataset will be resampled with 0.17:1.0 FAKE to REAL news ratio. (Real World Fake to Real news ratio)

## EDA
1. For original Text, Title and text were combined for the Analysis.
2. Stemming & Lemmatization Methods were also brought in to change form of the words. Stemming and Lemmatization basically changes the form of words back to most basic root. (Ex. is, am, are, --> be)

3. It is shown that REAL news generally have quite longer length than the FAKE news.
![word_trend](Images/word_trend.png)

It is hard to distingusi FAKE vs REAL news from the wordcloud, but we can infer that most of the news were primarily focused on Political Topic.

## Modeling
***
5 Models were built using 5 classifiers below:
1. DummyClassifier Model (Used for baseline to see minimum performance of the model)
2. DecisionTree Classifier Model
3. RandomForest Classifier Model
4. MultinomialNB Classifier Model
5. PassiveAggressive Classifier Model

Out of MultinomialNB Classifier Model and PassiveAggressive Classifier model were the 2 best models:
![MultinomialNB_CF](Images/Imb_MNB_CF.png)

MultinomialNB Classifier was built after TFIDF Vectorization using the Stemmed Text.

![PassiveAgg_CF](Images/Imb_Pac_CF.png)

PassiveAggressive Classifier was built after TFIDF Vectorization using the Lemmatized Text.

## Conclusion

Although PassiveAggressive Model was a strong competitior, I concluded that MultinomialNB model being the optimal model for our dataset.

Compared to PassiveAggresive Model, MultinomialNB model was better in:
1. Higher Accuracy & F1-Score
2. Classified higher # of Fake News
3. Classified higher # of Real News
4. Lower False Negative

Sine MultinomialNB classifier is built to be suitable for classification with word counts for text classification, it is not a surprise that MultinomialNB was the optimal classifier.

## Ideas for Improvement
1. Try Unsupervised Learning Models. (Deep Learning)
2. Try Web-Scraping from Fake News sites like Onions and see how well our model performs.
3. Try Web-Scraping from Social Media and see the Fake News Detection Rate.

## Repository Structure

***
```
├── README.md                           <- The high-level overview of this project
├── Detecting Fake News.pdf             <- PDF version of project presentation
├── Capstone_notebook.ipynb             <- Final_Notebook used for the project
├── images                              <- Sourced externally and visualizations generated from code
├── data                                <- All the .csv data files used for the notebook.
```
