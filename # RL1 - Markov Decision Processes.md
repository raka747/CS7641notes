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

The biggest assumption is stationary. This implies two assumptions of grid world:

- Infinite horizons - previously we assumed we can take an infinite number of steps, so we may take longer safer routes to wind up at a horizon. If we only have a limited number of steps left we may take a shorter riskier path to the goal. Time horizons also change the policy for the state given the time horizon.
- Utility of sequences - if U(s_0, s_1, s_2, ...) > U(s_0, s_1', s_2', ...) then U(s_1, s_2, ...) > U(s_1', s_2', ...). If the utility of one sequence is greater than another sequence and they both start from the same starting state, then the greater than relationship still exists if both sequences had the starting state removed. This stationary preference leads to a notion that utility can calculated by summing rewards.

In math this implies U(s_0, s_1, ...) = \sum_{t=0}^{\inf} R(s_t)

But this doesn't work. For example a sequence of receiving only a reward of 1 every time step vs a sequence of receiving 1 and occasionally 2 reward every time step results in equivalent rewards when taken to infinity. This is paradoxical because there is the intuition that occasionally receiving a reward of 2 should be better than never receiving the reward.

In order to change this we can change our utility function to U(s_0, s_1, ...) = \sum_{t=0}^{\inf} gamma^t R(s_t) where 0 <= gamma < 1. This causes the gamma^t to fall to 0.

This leads to U(s) <= \sum_{t=0}^{\inf} gamma^t R_MAX = R_MAX / (1 - gamma). Buy including this tuition this enables us to maintain infinite horizons and utility of sequences but enables a finite a bound on rewards

## Assumptions

Proof on R_MAX / (1 - gamma)

```
\sum_{t=0}^{\inf} {\gamma^t R_MAX}
= R_MAX * \sum_{t=0}^{\inf} {\gamma^t} 

let x = \sum_{t=0}^{\inf} {\gamma^t} 
x = \gamma^0 + \gamma * x
x - \gamma * x = 1
x ( 1 - \gamma) = 1
x = 1 / (1 - \gamma)
Therefore:
R_MAX / (1 - gamma)
```

## Policies

```
Trying to find:
pi * = argmax_pi E[\sum_t {\gamma^tR(s_t)} | pi]

Utility is defined as:
U^pi (s) = E[\sum_t {\gamma^tR(s_t)} | pi, s_0 = s]

E[] - Expected value
```

Note that R(s) != U^pi(s) because reward is the immediate feedback. Utility is long term as expected reward. This enables us to account for delayed reward.

```
This leads to the optimal policy:
pi * (s) = argmax_a \sum_s' T(s, a, s') U(s')

Note that U(s) is congruent to U^pi* (S)

U(s) = R(s) + \gamma max_a \sum_s' T(s, a, s') U(s')
```

This equation is Bellman's Equation. The most important equation

## Finding Policies

```
U(s) = R(s) + \gamma max_a \sum_s' T(s, a, s') U(s')
```

Has n equations (for the n states) and also has n unknowns! However the max is a non-linear function so it can't be solved with a standard regression / linear algebra method.

Algorithm to find utilities:
1. Start with arbitrary utilities
2. Update utilities based on neighbors
3. Repeat until convergence (step 2)

So at each step 2 we calculate R(s) + \gamma max_a \sum_s' T(s, a, s') \hat{U}(s') where \hat{U} is our current estimate of the utility for state s'

How does this converge? Because the initial \hat{U} were all made up? It's able to converge because the R(s) is a true reward and by repeating these estimates R(s) is getting propagated to neighboring states enabling better prediction of \hat{U}

This algorithm is called **value iteration**.

Repeating value iteration over grid world allows the utility to propagate from the absorber states to the other cells but it's also important to note that ultimately utility is nice but it's more information then necessary since policy is just looking for the max utility.

Alternative:

1. Start with pi_0 <- guess
2. Evaluate: Given pi_t calculate U_t = U^{p}i_t}
3. Improve pi_{t+1} = argmax_a \sum{T(s, a, s') U_t(s')}

We can calculate this because U_t(s) = R(s) + \gamma \sum_s' T(s, pi_t(s), s') U(s')

This transforms the situation to n linear equations with n unknowns which can be solved with matrices!

This is still possibly quite expensive to do matrix inversion on n states so it maybe clever to mix the methods depending on which one can converge faster or be calculated faster.

This is called **policy iteration**

## Summary

MDPs
Consists of states, rewards, actions, transitions, (discount - some consider part of the problem, some consider part of the algorithm)
Policies
Value functions (utilities) - utilities are long term as opposed to short term rewards
Discounting - allows us tackle finite world within infinite horizon
Stationarity
All tied together in Bellman equation - which can be solved using value iteration and policy iteration
