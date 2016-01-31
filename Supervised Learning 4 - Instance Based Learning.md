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

Looks at the k nearest neighbors to the query and determines the best answer based on the nearest neighbors. Nearest/distance is a stand-in for similarity.

Given: 
- Training Data D = {x_i, y_i}
- Distance metric d(q, x)
Number of neighbors k
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

|                       | Run Time      | space     |
| --------------------- | ------------- | --------- |
| 1-NN Learning         | 1             | n         |
| 1-NN Query            | log(n)        | 1         |
| k-NN Learning         | 1             | n         |
| k-NN query            | log(n) + k    | 1         |
| Regression learning   | n             | 1         |
| Regression query      | 1             | 1         |

## Doman Knowledge



## KNN Bias



## Curse of Dimensionalaity



## Summary

