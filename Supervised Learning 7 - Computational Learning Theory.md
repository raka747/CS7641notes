# Supervised Learning 7 - Computational Learning Theory

## Introduction

Different learners produce different outputs for classifying data.

> Voronoi diagram diagram that shows the splits in space/plane

### Learning Theory

Three questions or issues:

1. Define learning problems
2. Show specific algorithms work
3. Show these problems are fundamentally hard

Tools for analyzing learning problems are similar to tools for analyzing algorithms in computing.

Some of the resources useful in analyzing learning algorithms are time and space just like normal algorithms. Furthermore, learning algorithms are measured in terms of the number of samples or data they need to be effective.

## Inductive Learning

Inductive learning is learning from examples. There are several useful quantities to define when talking about inductive learning:

- Probability of successful training - (1 - delta)
- Number of examples to train on - m
- Complexity of hypothesis class - Complexity of H. Double edged sword. A class simple hypothesis class can prevent you from expressing truly complex concepts. Whereas a class of complex hypotheses can potentially easily overfit the data requiring a lot of data to truly define the relationships.
- Accuracy to which target concept is approximated - epsilon
- Manner in which training examples presented - two in particular batch (all handed to the learner at once), or online (one at a time)
- Manner in which training examples selected

## Selecting Training Examples

There are several ways to select training examples:
1. Learner ask questions for the teacher - c(x)?
2. Teacher gives examples to help the learner - Teacher  chooses x, tells c(x)
3. From nature (fixed distribution) - x chosen from D and c(x) comes along
4. Evil - worst distribution

### Teaching via 20 questions

If the teacher is trying to teach the student it can ask 1 question to the learner.

If the learner is choosing the questions then the # of questions is roughly log_2|H| assuming you can ask yes/no questions that split the remaining hypotheses in half.

## Teacher with Constrained Queries

The 20Q scenario is kind of misleading because in that scenario the teacher is allowed tp ask any question in the universe of questions but it isn't realistic.

A more classical scenario:

X: x_1, x_2, ... x_k (k bit input)
H: conjunctions of literals or negation
Hypothesis: x_1 and x_3 and not x_5

### Reconstructing hypothesis

| x_1 | x_2 | x_3 | x_4 | x_5 | h | 
| --- | --- | --- | --- | --- | - | 
| 1   | 0   | 1   | 1   | 0   | 1 | 
| 0   | 0   | 0   | 1   | 0   | 1 | 
| 1   | 1   | 1   | 1   | 0   | 0 | 
| 1   | 0   | 1   | 0   | 0   | 0 | 
| 1   | 0   | 1   | 1   | 1   | 0 | 

With a nice teacher you need 2 examples to show what's irrelevant. Then 1 example per relevant example (max k). So despite having 3^k hypotheses, only 2 + k examples need to teach a concept. 

## Learner with Constrained Queries



## Learner with Mistake Bounds



## Definitions



## Version Spaces



## Error of h



## PAC Learning



## PAC Learnable



## Epsilon Exhausted



## Haussler Theorem



## Summary

