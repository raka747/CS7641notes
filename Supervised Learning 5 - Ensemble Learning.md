# Supervise Learning 5 - Ensemble Learning

## Introduction

Identify simple rules that identify a small cases of classification, but not always completely accurate. But it can be difficult to combine a bunch of small individual rules to make a more complicated holistic ensemble of rules to tackle a problem.

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

That is to say the probability that a particular example of x comes up also has an impact on error not just how likely the learner is to get X wrong.

### Weak Learning

A Weak Learner is a learner that no matter what the distribution is, you always get an error rate that is better than chance (or 1/2)

```tex
\forall_\mathbb{D}[\cdot] \leq \frac{1}{2}-\epsilon
```

## Boosting in code

* Given training {(x_i, y_i)} and y_i in {-1, +1}
* For t = 1 to T
  * construct D_t
  * find a week classifier h_t(x) with small error \epsilon_t = P_{D_t}[h_t(x_i) = y_i]
* Output H_final

### Distribution

Distribution starts off even between all test cases.

For each distribution after, if the prediction was correct its probability in the distribution generally decreases. If the learner gets the prediction wrong, the probability in the distribution increases, but it ultimately depends on the rest of the distribution and how the learner performed, but as long as one hypothesis the probabilities that were correct decrease. 

```tex
\begin{align}
\mathbb{D}_1(i) &= \frac{1}{n} \\
\mathbb{D}_{t+1}(i) &= \frac{\mathbb{D}e^{-\alpha_ty_ih_t(x_i)}}{Z_t} \textup{ where} \\
\alpha_t &= \frac{1}{2} ln \frac{1 - \epsilon_t}{\epsilon_t}
\end{align}
```

### Final Hypotheses

Alpha is a measure of how well the hypothesis actually performed so the final hypotheses, so this can be used as weight in the final hypothesis.

```tex
H_{final}(x) = sgn(\sum_t {\alpha_th_t(x)})
```

### Intuition

Kind of the intuitive reason that boosting works and produces progressively  that the overall error necessarily has to stay the same or go down each iteration of boosting due to how the distribution changes in response to getting cases wrong and constantly having to find a weak learner.

## Summary

- Ensembles are good - If it's good to learn once. It's good to learn multiple times!
- Even simple ensembles like boosting is good i.e. Bagging
- Combining several simple learners can form a complex learner and take learners that are just barely good and turn it into something that is really good.
- Ensembles tend to be fast, and its ensembles agnostic to the actual weak learners that comprises it
- Weak learners
- Error Distrobutions
- Ensemble learners in practice tend to not be susceptible overfitting