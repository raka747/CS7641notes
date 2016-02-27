# Supervised Learning 8 - VC Dimension

## Infinite hypothesis space

last time we found that:

m >= 1 / \epsilon (ln|H| + ln(1 / \delta))

The problems is if you have an infinite set of hypothesis this equation is infinite. This is bad because linear separators, artificial neural networks, and decision trees with continuous inputs all have infinite hypothesis spaces. Of the various algorithms discussed so far, pretty much only decision trees with discrete inputs don't!

## Maybe it's not so bad

Assume you have a data set and hypothesis space:

```
X: {1, 2, 3, 4, 5, 6, 7, 8, 9, 10}
H: h(x)= x >= \theta
```

Where \theta is any real number. The hypothesis space for this problem is infinite. However really only hypothesis space that matters given X is positive integers 1 to 10 which is finite. There is a notion of syntactic hypothesis space which is anything that can be written as the hypothesis. However there is also semantic hypothesis or only the meaningfully different hypothesis space.

## Power of a hypothesis space

What is the largest set of inputs that the hypothesis class can label in all possible ways.

In the above example, a set of one element i.e. S = {6} can be labeled as True or False depending on if \theta is less or more than 6. 

However not all pairs of inputs can be labeled in any way. For x_1, x_2 where x_1 < x_2, x_1 cannot be true if x_2 is false (all other combinations of x_1 and x_2 being true or false work). So this hypothesis space, even though it's infinite, isn't very expressive.

## What does VC stand for?

What is the largest set of inputs that the hypothesis class can shatter? This quantity is the VC dimension.

VC stands for Vapnik-Chervonenkis - two people who related the largest set of inputs that the hypothesis space can shatter to the amount of data need to learn. As long as dimensionality is finite, even if the hypothesis class is infinite we can say things about how much data is needed to learn.

## Internal training

So for a problem such as:

```
X = \mathbb{R}
H = {h(x)= x \in [a, b]}
```

## Linear separators



## The ring



## Polygons



## Sample complexity



## VC of finite H



## Summary


