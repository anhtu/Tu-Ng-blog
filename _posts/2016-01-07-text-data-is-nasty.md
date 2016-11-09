---
layout: post
title: "Text data is nasty"
tags:
- nlp
- text summarization
- machine learning
comments: true
---

Recently, in my work as a Data Scientist, I got to deal with text data. And believe me, they are the messiest data ever, it's like sh*it, or even worse... I'm really running out of word now. The thing I hate is that most of my time was spent on data cleaning: tokenization, stemming, lemmatization, POS tagging, dealing with stopword, abbreviation, translation... Obviously I want to put the text into some reasonable "standardized" format so that I can feed them into my stupid `Support Vector Machine` (SVM) classifier. 

Playing around with a few libraries, I recommend [`spacy`](https://spacy.io/), a relatively recent nlp library in python. It gives me the most satisfying result compared to [Stanford Corenlp](http://stanfordnlp.github.io/CoreNLP/), [gensim](https://radimrehurek.com/gensim/) or [nltk](http://www.nltk.org/). The API is quite friendly, it gets you to speed in no time, and its POS tagging, tokenization are really good. In addition, they have a pre-trained [`word2vec`](https://www.tensorflow.org/versions/r0.11/tutorials/word2vec/index.html) model, which is very nice, and you can train your own too. One drawback of spacy and other nlp libraries is that [`Named-Entities Recognition`](https://en.wikipedia.org/wiki/Named-entity_recognition) is no where satisfying. For that, my own solution would simply be to use [Bing Search API](http://datamarket.azure.com/dataset/bing/search) and figure out the entity yourself. It sounds stupid but it actually works for me. The thing is I have to figure out whether an entity in the text is a name of a financial institutions or some stores. Big names such as Well Fargo, Citi Bank or Starbucks are easy. How to deal with small companies like BECU (Boeing Employee Credit Union) or Golden 1 Credit Union? Only way is to ask search engine. They give you back short description such as 

{% highlight ruby %}
{u'description': u'Financial services company'}    
{% endhighlight %}

This is much better clue to what the entity is. You can even use it to deal with abbreviations or typo like Capitol One (Capital One), BofA/BOA (Bank of America), USAA... It works! 

Since Bing Search API is free up to 5000 transactions a month, make sure you build a simple lookup table if you don't want to pay. And also you don't want to query every entity that you found. So that's another domain problem that you have to deal with. In my case, I know before hand that 80% of my entities are in certain categories and half of them are banks and stores. 

I hope this post is useful for whoever reads it. Good luck with text data! 

