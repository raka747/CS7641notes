# UL4 - Feature Transformation

The problem of pre-processing a set of features is to create a new (smaller? more compact?) feature set, while retaining as much (relevant? useful?) information as possible

Feature selection is a subset of feature transformation in that it is going strictly from a set of features to a subset of features. Feature transformation

x ~ F^N -> F^M with M < N (usually)
the transformation is some matrix P^T x that is a linear combination of the original features


Feature selection: {x_1, x_2, x_3, x_4} -> {x_1, x_2}

Feature transformation {x_1, x_2, x_3, x_4} -> {2x_1 + x_2}

### Why?

We've been doing feature transformation all along and individual learning algorithms like layers of perceptrons and kernel functions have their own method of methods of feature transformation. So why do feature transformation on top of these?

Information Retrieval - the ad hoc problem (or the Google problem) given the and unknown (ad hoc) query you have to retrieve a relevant set of documents from a database containing many documents. Challenge is you can't do a lot of analysis on the storage up front because you don't know what the queries will be.

### What are our features?

The features in the ad hoc information retrieval problems are? Words are the most basic feature one might use i.e. counts of words and plurals, singulars etc.

Problems:

- Lots of words
- Words can have multiple meaning (polysemy) gives false positives
- Many words mean the same thing (synonomy) doesn't show things due to false negatives

Feature selection doesn't help

## Words like Tesla



## Principal components analysis



## Independent components analysis



## Cocktail party problem



## Matrix



## PCA vs ICA



## Alternatives



## Summary



