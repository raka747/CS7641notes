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

Clustering tends to not have one consistent definition so it's very algorithm driven. Algorithms can be analyzed separately.

Single LInkage Clustering (SLC) is a Hierarchical Agglomerative Cluster (HAC) of algorithm

1. Consider each object a cluster (n objects)
2. Define inter cluster distance as the distance between the two points in the two clusters
3. Merge two closest clusters
4. Repeat n-k time so to make k clusters.

Clusters can be represented with a tree structure. This can be used to retroactively examine what the clustering structure would be like if a a different number of clusters were used.

Single link clustering uses the two closest points. Average, Median, and Furthest Link Clustering exist that use the average, median, or furthest distance.

Domain knowledge can be imparted by using appropriate distance and choosing whether closest, average, or furthest distance is most appropriate.

### Running time of SLC

Run time of SLC is n^3

Intuition: if k is small and k is big the problems isn't thata hard so it probably doesn't directly depend on k

1. Repeaat k times (n/2)
    a. look at all distances to find the closest pair (O(n^2)) that have different labels

### Issues with SLC

Depending on the examples given and the distances you can wind up with "stringy" points where a single link between two seemingly obvious clusters gets created leading to non-intuitive clusters (from a human perspective)

## K-means clustering

K-means avoids the "stringy" issue with SLC and has some other nice properties but there are trade-offs.

Algorithm:

1. Pick K centers (at random)
2. Each center "claims" its closest points
3. Recompute the centers by averaging the clustered points
4. Repeat 2-4 until convergence.

"Center" doesn't necessarily need to be a point in the dataset

### K-means in Euclidean Space

```
Define:
P^t(x) : Partition/cluster of objext x
C^t_i : Set of all points in cluster i = {x s.t. P(x)=i}
center^t_i = \sum_{y \in c^t_i} y / |C_i|

Algorithm
center^0_i
Partition: P^t(x) = argmin_i ||X - center^{t-1}_i||^2_2
Centers: center^t_i=\sum_{y\inC^t_i} y / |C_i|
```

### K-means as optimization

For optimization problems we want to define a notion of a configuration, score, and neighborhood. If k-means is an optimization problem:

- Configurations - The configuration is which points belong to which partition. And related to that is the idea of the center of the partition.
- Scores - Ideally you want to not lose data so an idea for a score is how much error is introduced as a result of expressing the points as a cluster around the mean rather than as a point. E(P, center) = \sum || center_{P(x)} - x||_2^2
- Neighborhood - P, center = {(P', center)} \union {(P, center')} union of sets where the parition is adjusted or where the center is adjusted.
