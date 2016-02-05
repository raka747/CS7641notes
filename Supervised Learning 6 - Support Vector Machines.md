# Supervise Learning 5 - Support Vector Machines

## Introduction

Given a linearly separable data set there be potentially infinite ways of separating data. How would you draw the best line of fit? You would want the line that provides the biggest buffer between any of your data. A line that gets closer to the data can be thought of trusting the data too much or overfitting. This example of overfitting is a bit different than what we've previously seen.

## Support Vector Machines

So going with a set of linearly separable data set
 
y = mx + b <- 2 dimensional version
y = w^Tx + b <- More general formula for hyperplanes and works for multiple dimensions of parameters

y is label {-1, +1} (note: not quite the same as the y in y = mx + b)
w^T and b are parameters of the plane

So we want to find the separator that is the furthest from the data sets but is still consistent. In order to do wo we can plug in two points on the boundaries x_1 and x_2 that satisfy:

w^Tx_1 + b = 1
x^Tx_2 + b = -1

The difference between these 2 equations is:

w^T(x_1 - x_2) = 2

And this difference represents a vector between the two boundaries. In order to determine the distance between the two boundaries you can divide ||w|| from both sides to get

w^T/||w|| (x_1 - x_2) = 2/||w|| 

as w^T/||w|| is a unit vector in the direction of w. Furthermore since w has the property of describing the hyperplane boundary, it itself is perpendicular to the boundary (like x_1 - x_2). So, w^T/||w|| (x_1 - x_2) gives us the length of the projection (x_1 - x_2) onto w (but isn't really a projection since they are in the same direction). and the dot product is 2/||w|| which gives us the length of x_1 - x_2.

In order to maximize the length of x_1 - x_2 we want the smallest ||w|| possible.

w^T/||w|| (x_1 - x_2)  is m or the **margin**. You want to find something that maximizes the margin subject to the condition that you classify everything.

**Classifying everything correctly** isn't mathematical but it is equivalent to y_i(w^Tx_c + b) >= 1 \forall i. This is true because y_i is the label and (w^Tx_c + b) is the hypothesis and both are {-1, 1} so if the hypothesis "matches" the label the sign of both are the same which means they multiply to be >= 1.

Maximizing 2/||w|| ends up being hard but is equivalent to maximizing 1/2 ||w||^2. Inversing it changes it from min to max. Squaring it is monotonic so doesn't change the problem, but it makes it easier by turning it into a quadratic programming problem. The standard form of the quadratic programming problem maximize is:

```tex
W(\alpha) = \sum_i{\alpha_i} - \frac{1}{2} \sum_{iu}{\alpha_i \alpha_j y_iy_jx_i^Tx_j} \newline
\textup{where } \alpha_i \geq0,\sum_i{\alpha_iy_i} = 0
```

Namely that the sum of alpha for each label minus the half the sum of the product of their alphas and labels.

## Optimal Separator

Once you have solved the quadratic programming problem you can retrieve based on w = \sum_i {\alpha_iy_ix_i}. b can be easily recovered by plugging in an x and y with the w.

Most of the alaphas are 0 in practice. This ends up meaning that many of the input vectors do not matter. Hence the name that the machine only needs a few support vectors (the ones with non-zero alphas). This is intuitive because the points near the edge really determine the boundary and can't be used to define the counters have no influence.

This is similar to kNN. It's not quite a lazy learner, instead it's as though you put a minimal effort to understand the bare minimum number of points to keep to give you good nearest neighbours.

The x's in the equation that we're trying to represent are the dot product and that gives us a notion of the similarity since dot product represents the magnitude of the projection. Orthogonal projection gives dot product of 0 and if the vectors are pointing in a similar direction it gives a larger magnitude.

## Linearly Married

In some instances you don't have linearly separable data. In some cases this can be due to "noise" with most of the data being linearly separable and in some cases ignore or negate certain examples.

However in other cases the data is separable, but not linearly - so they are linearly married. A way around this is to "change" the data points without changing the data points. Use a function phi(q) to change say a 2 dimension point <q_1, q_2> to a three dimensional point:

```tex
\Phi (q) = <q_1^2, q_2^2, \sqrt{2}q_q_2 >
```

Note, no extra information has been added. Also note that the way this information is ultimately utilized by is in a dot product x^Tx in w(\alpha).

```tex
\begin{align}
x^Ty &\to \\
\Phi(x)^T\Phi(y) &= <x_1^2, x_2^2, \sqrt{2}x_1x_2>^T<y_1^2,y_2^2,\sqrt{2}y_1y_2> \\
&= (x_1y_1 + x_2y_2)^2 \\
&= (x^Ty)^2
\end{align}
```

This is essentially the equation of circle meaning we've changed the notion of "being similar" has transformed from falling above or below a hyper line by changing similar to mean falling in or out of a circle.

Furthermore, this particular projection technique of using phi doesn't require the mapping to actually occur since the ultimate term is (x^Ty)^2 when the original notion of similarity is x^ty. This technique is called the **kernel trick**

## Kernel

```tex
W(\alpha) = \sum_i{\alpha_i} - \frac{1}{2} \sum_{iu}{\alpha_i \alpha_j y_iy_jx_i^Tx_j}
```

Is our new function and K(x_i,x_j) is our new notion of similarity. Furthermore, it is how we inject domain knowledge.

Kernel functions can be anything i.e. K = (x^Ty)2 or K = x^Ty both of which are special cases of a general kernel function (x^Ty+c)^P. This is similar to polynomial regression of kernels. 

```tex
\begin{align} 
K &= e^{-(\left \| x-y \right \|^2/2\sigma^2)} \\
K &= tanh(\alpha x^Ty+\theta)
\end{align}
```

The first is radial kernel and the latter is a kernel that resembles a sigmoid. A good Kernel really allows you to capture domain knowledge.

The **Mercer Condition** is the condition for kernel functions in that they represent distance in some way

## Summary

- Margins and their relationship to generalization and overfitting
- We want to find the margin that is largest
- Optimization problem for finding max margins and quadratic programs allow us to easily solve these problems
- Support vectors
- Linear isn't always enough so we can project into a higher dimension but really just x^Ty -> K(x,y)


## Boosting and overfitting

Boosting doesn't tend to overfit. Instead of a training rate that constantly decreases error and a test error that initially decreases but at some point increases.

Normally we track error which is the measure of the probability that you get the incorrect answer.

Another notion that is captured by boosting and other learning algorithms that measures how sure you are in the answer. In kNN, having 5 NN agree would cause relatively high confidence where as 3 agree and 2 disagree would be lower confidence. Or in regression having a high variance would be low confidence and low variance would be high confidence.

The final hypothesis is:

```tex
H_{final}(x) = sgn\left (\frac {\sum_t \alpha_th_t(x)}{\sum{\alpha_t}}  \right )
```

Because it's normalized, the values end up between -1 and 1 and the absolute value gives you a measure of the confidence. What ends up happening if you continue to add weak learners i that the answers that are near the boundary start to move away from the boundary meaning the confidence keeps going up (while the error still stays roughly constant).

As you  add more weak learners you get more confidence and a larger margin.

Boosting tends to overfit if the weak learner uses an algorithm that can overfit


