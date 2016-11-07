---
layout: post
title: "Kaggle is fun - Otto Product Classification Challenge"
tags:
- kaggle
- machine learning
comments: true
---

[Otto Group Product Classification Challenge](https://www.kaggle.com/c/otto-group-product-classification-challenge) is the most popular Kaggle competition ever (in terms of participants). The task was to build a predictive model to classify products into one of the nine categories. I was fortunate to take part in this competition and learned a great deal of techniques from other fellow Kagglers.

One of the challenges in this competition is that the data was obfuscated, which made feature engineering impossible. No insight could be obtained by examining the data manually. Nevertheless, the dataset is huge. We were given a total of 93 numerical features, with 200,000 observations in both training and test data. To take full advantage of this, the trick is [ensembling/blending/stacking](https://en.wikipedia.org/wiki/Ensemble_learning) to push machine learning models to the limit. 

This led to another fun thing, everything came down to understanding of machine learning algorithms and hyper-parameter optimization, since ensembling involves using multiple different models and combine their predictions into one. My final model is a linear stacking of neural nets (H20), xgboost, and random forest. xgboost and neural net complement each other very well, they are the driving force in the ensemble. Most of my time was spent on improving each model individually. Capability of `Random Forest` was limited in this dataset, I tried various ways to tune parameters but improvement was minor. The only thing that works for RF was `Probability Calibration`. 

The final result was tight. I joined the competition very late, only had 2 weeks to work on it but I'm quite satisfied with the result. I ended up in [91th place](https://www.kaggle.com/c/otto-group-product-classification-challenge/leaderboard/private) (top 3%) with a logloss of 0.41576, which was not bad given a huge number of competitors (3514 teams), and most of people in the top 100 compete in team. 

Even it was fun, I'm not looking foward to many challenges like this, since it was tedious in terms of labour. I spent over $40 to rent machines in AWS running models, and working more than 12 hours everyday for 2 weeks. I want datasets that enables creativity on feature engineering, smart use of models and so on. Anyhow, Kaggle is fun!!!


