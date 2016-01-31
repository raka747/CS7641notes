# Supervise Learning 3 - Neural Networks

## Introduction
We use neural networks... aka Brains!!!

### Biology

A neuron is comprised of a cell body, axon, and synapses. When the cell body decides to fire it sends a spike/electrical impulse along the axon that is transmitted to other neuron via the synapses.

### Artificial (Perceptrons)

A first approximation of a neuron can be relatively is used for neurons and networks of neurons to compute things. The neurons can be tuned and trained to fire under different conditions. The neuron theta takes  inputs (x_1, x_2, x_3, ...) and has weights (w_1, w_2, w_3, ...). The neuron boils down to sum_i (x_i * w_i)  if the sum >= theta or the threshold, the neuron fires (y = 1) otherwise the it doesn't (y = 0). This type of neuron is referred to as a **perceptron**

The perceptron (in a simple 2 input scenario) creates a half-plane as the 2 inputs describe a linear function between 2 variables.


## Booleans as perceptrons

Perceptron can be used to describe boolean functions. Let x_1 \in {0, 1} and x_2 \in {0, 1} then a perceptron with w_1 = 1/2, w_2 = 1/2, and theta = 3/4 describes an AND function (there are in fact infinite functions that can describe AND)

w_1 = 1, w_2 = 1, theta = 1 describes OR (again infinite combinations can produce an OR function)

One input perceptrons can also be used to describe NOT i.e. w_1 = -1, theta = 0.

XOR is possible but requires 2 perceptrons. On way is to use an "and" perceptron that feeds its output into a second perceptron with the x_1 weight of 1, AND weight of -2 and x_2 weight of 1 with a theta of (essentially an OR function with the AND scenario negating the OR.)

## Training perceptrons

The goal is to find weights that map inputs to outputs. Algorithms include:
* perception rule (threshold values)
* Gradient descent/ delta rule (unthresholded values)

### Perceptron Rule -> Single unit

data set of unit bias, x, and y \in {0,1}. In this arrangement - \theta is just another weight

```tex
\begin{align}
y &: \textup{target} \\
\hat{y} &: \textup{output} \\
\eta &: \textup{learning rate}\\
x &: \textup{input}
\end{align}

```

For x,y repeat updating the rules while there is still an error:

```tex
w_i = w_i + \Delta w_i \newline
\Delta w_i = \eta (y - \hat{y}) x_i \newline
\hat{y} = (\sum_i{w_ix_i} \geq 0 )
```
Since:

| y     | \hat{y}   | y - \hat{y}   |
| ----- | --------- | ------------- |
| 0     | 0         | 0             |
| 0     | 1         | -1            |
| 1     | 0         | 1             |
| 1     | 1         | 0             |


the weight gets adjusted by a small amount (the learning rate) only when the output of the weight and the actual output are different. And the difference pushes the output in the right direction.

If there is an actual line that separates the output, it is **linearly separable**. If the data set is linearly separable, the perceptron rule will find it after a finite iterations.

The problem is if the data is not linearly separable. It's generally not easy to tell if the data is linearly separable. In 2 dimensions it can be easy to see but in higher orders it's a lot more difficult. If the algorithm isn't done running we aren't sure if we just haven't run the algorithm long enough or it's not actually linearly solveable... hope someone solves the halting problem.

## Gradient Decent

Gradient Descent is an algorithm that can accomodate data that isn't linearly separable. In order to do this we imagine the output is not thresholded.

```tex
\begin{align}
a &= \sum_i{x_iw_i} \\
\hat{y} &= {a \geq 0} \\
E(w) &= \frac{1}{2} \sum_{x,y \in D} {(y-a)^2} \\
\frac{\delta E}{\delta w_i} &= \frac{\delta}{\delta w_i} \frac{1}{2} \sum_{x,y \in D} {(y-a)^2} \\
&= \sum_{x,y \in D} {(y-a)} \frac{\delta}{\delta w_i}-\sum_i {x_iw_i} \\
&= \sum_{x,y \in D} {(y-a)} (-x_i)
\end{align}
```

(4) follows due to chain rule and substituting da/dw_i with the \sum_i{x_iw_i}
(5) follows due to paratial derivative only impacting the x_i term corresponding to the w_i term

This very much resembles the perceptron rule (1 perceptron: guaranteed!, 2 gradient decent: calculus!): 

```tex
\begin{align}
\Delta w_i &= \eta (y-\hat{y})x_i \\
\Delta w_i &= \eta (y-a)x_i
\end{align}
```


## Learning rules


## Sigmoid


## Neural "Networks"


## Optimizing weights


## Restriction Bias


## Preference Bias


## Summary

