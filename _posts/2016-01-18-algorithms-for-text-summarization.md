---
layout: post
title: "Algorithms for Document Summarization"
tags:
- nlp
- document summarization
- lda
- textrank
- machine learning
comments: true
---

`Documment Summarization` is an open and challenging problem in machine learning and `Natural Language Processing` (NLP). Whether it's keywords-based or sentence-based summarization, there's no satifying algorithm out these. 

The standard algorithm for analyzing document in industry is [`Latent Dirichlet Allocation`](https://www.cs.princeton.edu/~blei/papers/BleiNgJordan2003.pdf). Think about it as some form of matrix factorization on document-term matrix into a product of document-topic and topic-term matrix, where the number of topics is pre-specified. The topic-term matrix is what we're interested in, each vector is a collection weight of each term in the topic. The higher the weight, the more importance the word to the topic. Therefore, by examining the important words in the each topic, we know what the topic is about. So `LDA` is generally finding a bunch of topics with respect to a collection of documents. 

An alternative to `LDA` is [`TextRank`](https://github.com/summanlp/textrank), a version of `PageRank` applied to text data. In terms of performance, it works relatively alright and has both builtin keywords and sentence summarization. 

Another interesting and practical algorithm to carve out the keywords is to take some other corpus and look at top frequent words in that corpus (500, 1000). These words are supposed to be common words such as stopwords (a, the, ...), frequent adj or verbs that are not informative (good, give, take...). Then use these words to filter out all ngrams (NP or VP, AP) containing them. What we are left with are hopefully `domain keywords`. Then we can use something like [`TF-IDF`](https://en.wikipedia.org/wiki/Tf%E2%80%93idf) to measure importance of these words in the corpus. 

