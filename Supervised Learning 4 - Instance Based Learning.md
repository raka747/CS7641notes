# Supervise Learning 4 - Instance Base Learning

## Introduction

Up until this point we look at <x_1, y_1>, ..., <x_n, y_n> to produce a f(x) = w*x + y.

Instance based learning says store <x_1, y_1>, ..., <x_n, y_n> in a database and so f(x) = lookup(x)

There are several quirks:
- It remembers - if you query something that you trained on you get the value rather than a rounded or smoothed out value
- Fast "learning"
- It's simple.
- Seems conservative - no generalization?
- Memorization - overfitting is a big problem; sensitive to noise
- What happens if the same x shows up with multiple y values?

This version might be a little too literal

## KNN

Looks at the k nearest neighbours to the query and determines the best answer based on the nearest neighbours. Nearest/distance is a stand-in for similarity.

Given: 
- Training Data D = {x_i, y_i}
- Distance metric d(q, x)
Number of neighbours k
Query point q

d(q, x) and k represent domain knowledge

1. NN = {i: f(q, x) k smallest}
2. Return
..* Classification: Vote, mode, plurality
..* Regression: Mean

Some caveats:
- Take the smallest that are >= k
- Returns might be weighted based on distance
- May need to make some choice of what specifically to return in the case of ties


### Performance

Lazy learner versus eager learner.

|                       | Run Time      | space     |
| --------------------- | ------------- | --------- |
| 1-NN Learning         | 1             | n         |
| 1-NN Query            | log(n)        | 1         |
| k-NN Learning         | 1             | n         |
| k-NN query            | log(n) + k    | 1         |
| Regression learning   | n             | 1         |
| Regression query      | 1             | 1         |


## KNN Preference Bias

What makes a good hypothesis, given all other things equal what makes the learner prefer one hypothesis to another.

- Locality : Points that are near by are similar. This is embedded in the distance function. There will be good and bad distance functions and requires domain knowledge
- Smoothness: Averaging. This is related to locality.
- All features matter *equally*

## Curse of Dimensionality

As the number of features or dimensions grows, the amount of data we need to generalize accurately grows exponentially.

For machine learning it's instinctual to add more and more features to determine which features is actually important. However, the curse of dimensionality states that as you add more features you need more data.

Dimensionality isn't just a problem for kNN but for machine learning in general. Adding in extra dimensions without actually adding more data, gives you more "volume" to fill without giving you more coverage within that volume.

## Misc.

- d(x, q) = Euclidean, Manhattan, weighted. Distance measures very heavily. Weighted dimensions can help deal with dimensionality and there are automatic ways for determining weights.
- Choosing k is important. In some cases you might have k = n using weighted average or weighted regression. The hypothesis space starts simply (possibly just a linear regression), but with locally weighted regression you can have a hypothesis space that can be more complicated depending on the local data.

## Summary

* Instance based learning
* Lazy learner vs Eager Learner
* kNN
* Nearest neighbor: similarity (distance) Domain knnowledge is important!
* Classification vs regression
* Averaging
* Locally weighted $x regression
* Curse of dimensionality O(2^d)