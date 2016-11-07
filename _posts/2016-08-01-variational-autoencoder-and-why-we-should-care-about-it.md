---
layout: post
title: "Variational Autoencoder and Why should we care about it"
tags:
- deep learning
- graphical models
- machine learning
comments: true
---

Recently, I develop an interest about `Variational Autoencoder` (VAE), after reading the influential paper called [Auto-Encoding Variational Bayes by Kingma](https://arxiv.org/abs/1312.6114). This occurs very naturally to me as I have a strong interest in Probabilistic Graphical Model, which I believe is the way to go for future development of AI. VAE is basically an autoencoder, which in turns is a neural net with the same output as input. You might ask why letting a neural net learning a model from the data with same output as input? Well, this is called `Unsupervised Learning` problem, where we only have the covariate or input variable, no response \\( y \\). Usually the input is quite complex such as a picture, that's why we use neural net to learn its distribution, which is a powerful approximator. Autoencoder is a same-input-output neural net with strong regularization, hoping to learn some useful structure in the data. 

VAE remains in the same spirit as AE. However,  


 lets us perform efficient inference of complicated posterior, so complex like the distribution of pixels in a digit, using a neural net as the powerful approximator. The trick is to approximate the posterior by a simpler distribution called `recognition model`, which leads to a lower bound on the marginal likelihood, then use variational inference to optimize the bound with respect to variables in the model. 

Interestingly, Variational Autoencoder (VAE) turns out to be a common child of Probabilistic Graphical Models and Deep Learning. In short, it's a probabilistic/generative model for autoencoder, which itself is a neural net. 

Why people care about generative model? Because it opens a whole new world for deep learning, as development in generative model has come a long way. Furthermore, it lets us dive into deep learning and understand what happens undernreath the powerful blackbox algirthm. VAE do marvelous things such as learning digits and producing similar digits or learning pictures of ...

