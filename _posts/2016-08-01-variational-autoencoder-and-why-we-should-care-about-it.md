---
layout: post
title: "Variational Autoencoder and Why should we care about it"
tags:
- deep learning
- graphical models
- approximate inference
- machine learning
comments: true
---

Recently, I develop an interest about `Variational Autoencoder` (VAE), after reading the influential paper called [Auto-Encoding Variational Bayes by Kingma](https://arxiv.org/abs/1312.6114). This occurs very naturally to me as I have a strong interest in Probabilistic Graphical Model, which I believe is the way to go for future development of AI. VAE is basically an autoencoder, which in turns is a neural net with the same output as input. You might ask why letting a neural net learning a model from the data with same output as input? Well, this is called `Unsupervised Learning` problem, where we only have the covariate or input variable, no response variable \\( y \\). Usually the input is quite complex like a distribution of pixels in a picture, that's why we use a powerful approximator as neural net to learn its distribution. `Autoencoder` (AE) is a same-input-output neural net with strong regularization, hoping to learn some useful structure in the data. 

VAE remains in the same spirit as AE. However, it has a probabilistic interpretation as a pair of latent variable model (or decoding distribution) and its variational inference mechanism (or encoding distribution). This generative model lets us reproduce the data, and see the interesting underlying data structure. The paper goes much beyond that, it proposes an efficient algorithms to approximately solve the `Inference` and `Learning` problem through approximating the posterior of latent and optimizing a lower bound of marginal likelihood of data. 

As being said, Variational Autoencoder (VAE) is a common child of `Probabilistic Graphical Models` and `Deep Learning. Why people care about generative model? Because it opens a whole new world for (unsupervised) deep learning, as development in generative model has come a long way. Furthermore, it lets us dive into deep learning and understand what happens underneath the powerful blackbox algirthm. VAE do marvelous things such as learning and producing images of digits or street view (to learn more, check out [this paper](https://arxiv.org/abs/1502.04623)).  


