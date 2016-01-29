# Supervise Learning 1 - Decision Trees

## Basic terms
- *Instances* - Inputs
- *Concept* - Function for mapping Instances (inputs) to Labels (outputs)
- *Target* - The "target" concept (or "answer" concept) for mapping inputs to outputs
- *Sample* - Training set
- *Candidate* - proposed concept for mapping inputs to outputs
- *Testing Set* - Similar to the training set but with with the purpose of testing the candidate mapping. Needs to be different to prove that you can generalize

## Decision Trees
Binary classification (ex. Standing in front of a restaurant. Do you want to go in?)

### Representation 
lolol find an img

### Algorithm
ID3 is particular algorithm for determining the "best" attributes to split on in creating a decision Tree

```
gain(s, a) = 
Entropy(s) - sum_v |s_v| / |s| Entropy(s_v)
```

Entropy is a measure of randomness


```
sum_v p(v) log(p(v))
```

Another way of thinking of it is measurement of "knowing" the outcome

Ideally you choose splits that minimize entropy or maximize Gain


### Bias

restriction bias: H

preference bias: h \in H

Preferences of ID3
- Good splits at the top - prefer the one that has the best split at the top
- Prefers shorter trees rather than longer trees (kind of a result of previous)
- Prefer correct versus incorrect

### Other considerations
- You can have continuous attributes. In order to deal with this you can create discrete buckets. # Buckets will increase branching factor
- When to stop? You want to avoid "classifying" everything correctly so avoid overusing attributes or overfitting. 
- You can use cross validation to avoid overfitting. Naive cross validation could be producing sever Samples and cross validate. A more efficient alternative is grow the tree and test against the validation set and stop growing the tree after you've passed a certain threshold of goodness. This might have concerns in a depth vs breadth first search
- Another option you can use is pruning outputs. In pruning build the full tree as though overfitting wasn't an issue and prune the branches that are unnecessary.
- Regression (when you don't have discrete labels) - splitting, variance are ways of measure output. Output average or local fit - kind of voting. Resembles pruning

## Summary
- Decision Tree
- ID3: A top down learning algorithm
- Expressiveness of DTs
- Bias of ID3
- "Best" Attributes (gain(s, a))
- Dealing with overfitting