# Supervised Learning 7 - Computational Learning Theory

## Introduction

Different learners produce different outputs for classifying data.

> Voronoi diagram diagram that shows the splits in space/plane

### Learning Theory

Three questions or issues:

1. Define learning gproblems
2. Show specific algorithms work
3. Show these problems are fundamentally hard

Tools for analyzing learning problems are similara to tools for analyzing algorithms in computing.

Some of the resources useful in analyzing learning algoriths are time and space just like normal algorithms. Furthermore, learning algorithms are measured in terms of the number of samaples or data they need to be effective.

## Inductive Learning

Inductive learning is learning from examples. There are several useful quantities to define when talking about inductive learning:

- Probability of successful training - (1 - delta)
- Number of examples to train on - m
- Complexity of hypothesis class - Complexity of H. Double edged sword. A class simple hypothesis class can prevent you from expressing truly complex concepts. Whereas a class of complex hypothesese can potentially easily overfit the data requiring a lot of data to truly define the relationships.
- Accuracy to which target concept is approximated - epsilon
- Manner in which training examples presented - two in particular batch (all handed to the learner at once), or online (one at a time)
- Manner in which training examples selected

## Selecting Training Examples

There are several ways to select traininng examples:
1. Learner ask questions for the teacher - c(x)?
2. Teacher gives examples to help the learner - Teacher  chooses x, tells c(x)
3. From nature (fixed distribution) - x chosen from D and c(x) comes along
4. Evil - worst distribution

## Teacher with Constrained Queries



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

