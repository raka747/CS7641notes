# Supervise Learning 3 - Neural Networks

## Introduction
We use neural networks... aka Brains!!!

### Biology

A neuron is comprised of a cell body, axon, and synapses. When the cell body decides to fire it sends a spike/electrical impulse along the axon that is transmitted to other neruron via the synapses.

### Artifical (Perceptrons)

A first approximation of a neuron can be relatively is used for neurons and networks of neurons to compute things. The neurons can be tuned and trained to fire under different conditions. The neuron theta takes  inputs (x_1, x_2, x_3, ...) and has weights (w_1, w_2, w_3, ...). The neuron boils down to sum_i (x_i * w_i)  if the sum >= theta or the threshold, the neuron fires (y = 1) otherwise the it doesn't (y = 0). This type of neuron is referred to as a ** perceptron **

The perceptron (in a simple 2 input scenario) creates a half-plane as the 2 inputs describe a linear function between 2 variables.


## Booleans as perceptrons

Perceptron can be used to describe boolean functions. Let x_1 \in {0, 1} and x_2 \in {0, 1} then a perceptron with w_1 = 1/2, w_2 = 1/2, and theta = 3/4 describes an AND function (there are in fact infinit functions that can describe AND)

w_1 = 1, w_2 = 1, theta = 1 describes OR (again infinite combinations can produce an OR function)

One input perceptrons can also be used to describe NOT i.e. w_1 = -1, theta = 0.

XOR is possibel but requires 2 perceptrons. On way is to use an "and" perceptron that feeds its output into a second perceptron with the x_1 weight of 1, AND weight of -2 and x_2 weight of 1 with a theta of (essentially an OR function with the AND scenario negating the OR.)

## Training perceptrons


## Gradient Decent


## Learning rules


## Sigmoid


## Neural "Networks"


## Optimizing weights


## Restriction Bias


## Preference Bias


## Summary

