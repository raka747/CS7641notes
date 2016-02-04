# Supervise Learning 5 - Support Vector Machines

## Introduction

Given a linearly seperable data set there be potentially infinite ways of seperating data. How would you draw the best line of fit? You would want the line that provides the biggest buffer between any of your data. A line that gets closer to the data can be thought of trusting the data too much or overfitting. This example of overfitting is a bit different than what we've previously seen.

## Support Vector Machines

So going with a set of linearly seperable data set
 
y = mx + b <- 2 dimmensional version
y = w^Tx + b <- More general formula for hyperplanes and works for multiple dimensions of parameters

y is label {-1, +1} (note: not quite the same as the y in y = mx + b)
w^T and b are parameters of the plane

So we want to find the seperator that is the furtherst from the data sets but is still consistent. In order to do wo we can plug in two points on the boundaries x_1 and x_2 that satisfy:

w^Tx_1 + b = 1
x^Tx_2 + b = -1

The difference between these 2 equations is:

w^T(x_1 - x_2) = 2

And this difference represents a vector between the two boundries. In order to determine the distance between the two boundries you can divide ||w|| from both sides to get

w^T/||w|| (x_1 - x_2) = 2/||w|| 

as w^T/||w|| is a unit vector in the direction of w. Furthermore since w has the property of describing the hyperplane boundry, it itself is perpendicular to the boundry (like x_1 - x_2). So, w^T/||w|| (x_1 - x_2) gives us the length of the projection (x_1 - x_2) onto w (but isn't really a projection since they are in the same direction). and the dot product is 2/||w|| which gives us the length of x_1 - x_2.

In order to maximize the length of x_1 - x_2 we want the smallest ||w|| possible.

w^T/||w|| (x_1 - x_2)  is m or the **margin**.

## Optimal Seperator



## Linearly Married



## Kernal



## Summary



## Boosting and overfitting


