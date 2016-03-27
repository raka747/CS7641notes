# UL2 - Clustering

## Unsupervised Learning



## Basic Clustering Problem

One of the classic unsupervised problems is taking a set of objects and putting them in groups.

Given:
- A set of objects x
- Inter-objects distance D(x,y) = D(y, x) x, y \in X (objects do not need to be in a metric space, distances do not depend triangle problem)

Output:
- Partition P_D (x) = P_D(y) if x and y in the same cluster

Trivial partitions include \forall x P_D(x) = 1 (everything is the same) and \forall x P_D(x) = x (everything is different)

## Single Linkage Clustering


