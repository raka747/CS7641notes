# RL1 - Markov Decision Processes

## Decision Making & Reinforcement Learning

Three types of learning:
- Supervised Learning: Function approximation. Given x and y, fund a function f(x) to map x to y
- Unsupervised learning: Given x, find f(x) that gives you a compact description i.e. clustering or description
- Reinforcement learning: Superficially resembles supervised learning in that given "pairs" of data. But instead of x and y, given x's and z's to find a function f that achieves y. Reinforcement learning is one method of achieving decision making

## The world

Gridworld is a commonly used problem setting for reinforcement learning problems. Consists of:
- Start cell
- Normal cells
- Walls and blocked of cells
- Goal cell(s)
- "Lose" cell(s)

## Markov Decision Processes

The problem framework:
- States: S - The set of every possible "state" the agent can be in
- Model: T(s, a, s') ~ Pr(s'|s, a) - The model describes the rules of the world. A function of the current state, the action, and a possible future state produces the probability that you end up in state s' given you were in state s and took action a
- Actions: A(s), A - The set things the agent can do in a particular state. Maybe considered a function of the state.
- Reward(s), R(s, a), R(s, a, s') - Reward is a scalar value you receive for being in a state. Reward encompasses the notion of domain knowledge. Reward can be a function of being in a state, or a function of being in a state and taking an action, or a function of being in a state, taking an action, and winding up in another state. Mathematically these three are equivalent.

The solution:
- Policy: pi(s) -> a takes in a state and produces the action the agent should take
- pi* - The policy that optimizes the reward or expected reward

Markovian property - only the present matters! The model produces Pr(s'|s, a) which only is based on s and not a collection of multiple previous s's.

Even if something isn't necessarily Markovian it can be turned into something Markovian by ensuring that the current state "remembers" everything it needs to know from previous states.

Things are stationary - the rules or model does not change. The states aren't stationary, but the rules behind the world are stationary.

In a supervised learning scenario you would receive <s, a> and try to learn the right a to take given a state s. In a Markov decision world we see <s, a, r> and this ends up being a very different problem to find the optimal policy (pi*) to produce actions to take.

## Rewards



## Sequences of Rewards



## Assumptions



## Policies



## Finding Policies



## Summary


