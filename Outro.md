# Outro

## Supervised Learning

### Deep neural nets or deep learning

New techniques for getting signals through multiple layers. Not clear that you could do better with many layers back in the 80s.

New set of techniques to get signal through all of the layers (bunch of different tricks)

### Big Data

Big data - algorithm challenges from gigantic datasets, linear too slow...

Computation changes the way science is done through models

### Semi-supervised learning

Slightly different problem. Labeled some pages but still a large amount of data with no labels. Extract structure from semi-structured data and combine with the structured labeled date.

### The assumptions of balanced labels

Implicit in a lot of the work is about half is labeled positive and the other half is labeled negative. But if you have data that is 97% negative, getting 97% accuracy isn't impressive and the cost of false negative is really high. You can re-weight error etc. but one method is cascade learning.

Cascade learning filters out only negatives and leaves a smaller set of all of the positives and still lots of negatives. Repeat this until you eventually have a set of 50-50 positives and negatives (similar to boosting). Apply learner to 50-50 split data

## Unsupervised

### TF-IDF

Term frequency inverse document frequency - lots of measures for measures of similarity between query and documents. Simple but powerful method is the weight that you should put on a term appearing in a document (TF). However you down weight it based on how frequently the term appears across all documents (DF).

### Spectral Clustering

Doesn't get stuck in local optima

### Cross entropy

Interesting Rand Opt that works well

## Reinforcement Learning

### Function approximation

Can you apply this to something other than a grid world?

Use other parts of the class i.e. SL and UL to learn about the world. Feature selection is abstraction (abstract states and actions)

### POMDPs

Partially observable Markov decision process

MDPs agent always has complete state awareness but usually you don't have complete state awareness

Separation between what agent's perception of state is and what the actual world is

### Behavioral Economics

Behavioral game theory incorporating game theory into economics

### Inverse RL

start from observations of behavior - guess reward function (guess motivation and behaviors of the acting agent)
