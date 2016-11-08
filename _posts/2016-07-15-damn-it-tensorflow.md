---
layout: post
title: "Damn it! Tensorflow"
tags:
- deep learning
- tensorflow
- machine learning
- automatic differentiation
comments: true
---

Damn it, `Tensorflow`! Why Google spent efforts to develop yet another deep learning library? Another library I have to learn!

That was my thought on first encounter with [Tensorflow](https://www.tensorflow.org/)... It hasn't changed a bit since recently. I got to develop a few machine learning algorithms and what I did was, as usual, coding it by hand from scratch. You might think how laborous it is since we got to deal with the very small detail, but it is fun, and more than that I own it. However, one of the very painful bit in the process was to code up the gradient of the loss function. Long and error-prone. I got stuck for a few hours debugging it. 

Then I remember tensorflow actually has a feature to automatically compute your gradient (Aha!), which I already used in my Variational Autoencoder project. I decided to give it a try and it works brillantly. Now, I know why tensorflow is not another deep learning library but so much more than that, it aims to be a numerical computation library. This is a goal for tensorflow and I feel that it's still pretty far from it, although it's making progress. Compared to `numpy`, tensorflow is lacking a lot of array manipulation such as [indexing and slicing](https://github.com/tensorflow/tensorflow/issues/206), people need to resolve to work-arounds. For instance, a very simple code for SVM loss in numpy like the following, would be very painful to translate to tensorflow, note that the code is vectorized and uses a lot of [array indexing](https://docs.scipy.org/doc/numpy/reference/arrays.indexing.html)

{% highlight python %}
def svm_loss(X, W, y):
    loss = 0.0
    num_classes = W.shape[1]
    num_train = X.shape[0]
    scores = np.dot(X, W)
    scores -= np.reshape(scores[range(num_train), y], (num_train, 1))   # broadcast minus
    scores += 1.0
    scores[range(num_train), y] = 0.0
    loss = np.sum(scores[scores > 0])
    loss /= num_train
    loss += 0.5*reg*np.sum(W**2)
    return loss
{% endhighlight %}

Simplest solution would be to use [`Autograd`](https://github.com/HIPS/autograd), another tool for `Automatic Differentiation`. Only a smalle change to one line

{% highlight python %}
# scores[range(num_train), y] = 0.0
loss = np.sum(scores[scores > 0]) - num_train
{% endhighlight %}

Nevertheless, tensorflow is still powerful to experiment deep learning models, and anyone working in ML should be aware of it. For everyone interested in learning more about tensorflow, there's a [lecture](https://www.youtube.com/watch?v=l6K-MFgIEjc) in Stanford course CS224D which serves a practical introduction to tensorflow. 

Some more word about this feature of tensorflow, it's called [`Automatic Differentiation`](https://justindomke.wordpress.com/2009/02/17/automatic-differentiation-the-most-criminally-underused-tool-in-the-potential-machine-learning-toolbox/
). Some people claim it's more powerful than [`Symbolic Differentiation`](http://deeplearning.net/software/theano/tutorial/gradients.html) (used in Theano), as it can compute gradient of not only expressions but also algorithms (such as for loop). I really don't care about the details as long as they work. To me, they look like as some variants of `backpropagation`.  


