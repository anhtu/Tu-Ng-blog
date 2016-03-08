---
layout: post
title: Lessons learned from the Otto Product Classification Challenge
tags:
- kaggle
- machine learning
comments: true
---

Otto Group Product Classification Challenge is the most popular Kaggle competition ever (in terms of participants). The task was to build a predictive model to classify products into one of the nine categories. I was fortunate to take part in this competition and learned a great deal of techniques from other fellow Kagglers.

One of the challenges in this competition is that the data was obfuscated, which made feature engineering impossible. We were given a total of 93 numerical features, with a huge 200,000 observations in both training and test data. The fun part of this challenge was that it all came down to understanding about the machine learning algorithms and hyper-parameter optimization.

The final result was tight. I joined the competition very late, only had 2 weeks to work on it but I'm quite satisfied with the result. I ended up in 91th place (top 3%) with a logloss of 0.41576, which was not bad given a huge number of competitors (3514 teams).

My final model is a linear stacking
