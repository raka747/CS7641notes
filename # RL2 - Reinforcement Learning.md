# RL1 - Reinforcement Learning

Think of RL as a API (Application Programmer Interface)

model (T, R) -> Planner -> Policy

Transitions \<s, a, r, s''>* -> Learner -> Policy

Solving an MDP takes models and turns them into policies.

On the other hand Learners take transitions and learn a policy which makes it learning, specifically reinforcment learning.

Why is it named reinforcement learning? Way back when psychologist discovered that if you present an animal with a stimulus that and reward the action this strengthens the response to this stimulus. Not really reinforcement... more like reward maximization.

## API

There are several additional variations to the reinforcement learning API

transitions -> modeler -> model

model -> simulator -> transitions

This leads to the idea of different possible ways of gluing the APIs together to do reinforcement learning:

RL-based planner???: Model -> Simulator -> Transitions -> Learner -> Policy

Model-based RL: Transitions -> Modeler -> Model -> Planner -> Policy

## Approaches to RL



## A new kind of Value function



## Q Learning



## Estimating Q from Transitions



## Learning incrementally



## Q Learning Convergence



## Choosing Actions



## Greedy Exploration


