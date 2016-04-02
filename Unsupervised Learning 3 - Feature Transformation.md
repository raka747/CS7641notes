# UL4 - Feature Transformation

The problem of pre-processing a set of features is to create a new (smaller? more compact?) feature set, while retaining as much (relevant? useful?) information as possible

Feature selection is a subset of feature transformation in that it is going strictly from a set of features to a subset of features. Feature transformation

x ~ F^N -> F^M with M < N (usually)
the transformation is some matrix P^T x that is a linear combination of the original features


Feature selection: {x_1, x_2, x_3, x_4} -> {x_1, x_2}

Feature transformation {x_1, x_2, x_3, x_4} -> {2x_1 + x_2}
