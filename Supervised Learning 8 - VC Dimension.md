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



## What does VC stand for?



## Internal training



## Linear separators



## The ring



## Polygons



## Sample complexity



## VC of finite H



## Summary


