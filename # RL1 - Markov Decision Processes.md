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

In a supervised learning scenario you would receive \<s, a\> and try to learn the right a to take given a state s. In a Markov decision world we see \<s, a, r\> and this ends up being a very different problem to find the optimal policy (pi*) to produce actions to take.

Policies differs from plans. Policies can tell you what to do no matter state you are in whereas a plan is a concrete set of actions to take over the next series of time steps.

## Rewards

What makes MDP's different from SL?

- Not just rewards
- Delayed rewards. 
- Minor changes matter

Actions move you to states that can lead to other actions and after some time you "learn" the final outcome is positive or negative. A positive outcome could be due to good actions all throughout or mostly mediocre actions with a few brilliant actions. Part of the MDP problem is determining the exact actions that lead to positive outcomes.

This is called the **credit assignment** problem or also the **Temporal Credit Assignment** problem due to the often temporal nature of state, action, reward triples.

### Rewards in Grid world

Rewards can be used to structure the problem. i.e. a small negative reward for each state other than the goal state and lose state in grid world will motivate the agent to move towards the absorption states.

Changes in reward policy can cause changes to the policy. i.e a strong positive reward for every state will cause the agent to avoid any end state. A strong negative reward for every state will cause the agent to prioritize any end state even if it has a small negative reward.

## Sequences of Rewards

Assumptions of grid world:

- Infinite horizons - previously we assumed we can take an infinite number of steps, so we may take longer safer routes to wind up at a horizon. If we only have a limited number of steps left we may take a shorter riskier path to the goal. Time horizons also change the policy for the state given the time horizon.
- Utility of sequences - if U(s_0, s_1, s_2, ...) > U(s_0, s_1', s_2', ...) then U(s_1, s_2, ...) > U(s_1', s_2', ...). If the utility of one sequence is greater than another sequence and they both start from the same starting state, then the greater than relationship still exists if both sequences had the starting state removed. This stationary preference leads to a notion that utility can calculated by summing rewards.

## Assumptions



## Policies



## Finding Policies



## Summary


