# Supervise Learning 5 - Ensemble Learning

## Introduction

Identify simple rules that identify a small cases of classification, but not always completely accurate. But it can be difficult to combine a bunch of small individual rules to make a more complicated wholistic ensemble of rules to tackle a problem.

There are similarities to Neural nets and decision trees. The difference is typically neural nets you have the network built and the nodes are trying to learn the right weights and with a decision tree you're building up rules as you go along. With ensemble learning you're building up rules as well.

## Simple rules

1. Learn over a subset of the data... repeat
2. Combine for a complex rule

We focus on a smaller subset because it can be harder to learn a simple rule if you're looking at too much data.

## Simple algorithm: Bagging

1. Learn over a subset of data - Uniformly randomly pick data and apply a learner
2. Combine - Average the results

The bags are random subsets. Also called bootstrap aggregation.


## Boosting High level

Rather than choosing uniformly randomly over the data. Instead of focusing randomly, focus on the examples that are "hard" or that we are not good at.

1. Learn over a subset of data - "Hardest" examples
2. Combine - Weighted means

### Errors

Number of mismatches have been the metric for error but it implicit that each example is just as likely. A more general form of error is:

```tex
P_{\mathbb{D}}[h(x)=c(x))]
``` 

That is to say the probability that a particular example of x comes up also has ana impact on error not just how likely the learner is to get X wrong.

## Weak Learning



## Boosting in code



## Final Hypotheses



## Good answers



## Summary