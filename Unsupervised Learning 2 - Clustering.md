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



## K-means clustering

