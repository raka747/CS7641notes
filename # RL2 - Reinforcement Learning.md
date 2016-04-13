# RL1 - Reinforcement Learning

Think of RL as a API (Application Programmer Interface)

model (T, R) -> Planner -> Policy

Transitions \<s, a, r, s'>* -> Learner -> Policy

Solving an MDP takes models and turns them into policies.

On the other hand Learners take transitions and learn a policy which makes it learning, specifically reinforcment learning.

Why is it named reinforcement learning? Way back when psychologist discovered that if you present an animal with a stimulus that and reward the action this strengthens the response to this stimulus. Not really reinforcement... more like reward maximization.

## API

There are several additional variations to the reinforcement learning API

transitions -> modeler -> model

model -> simulator -> transitions

This leads to the idea of different possible ways of gluing the APIs together to do reinforcement learning:

RL-based planner*???: Model -> Simulator -> Transitions -> Learner -> Policy

Model-based RL: Transitions -> Modeler -> Model -> Planner -> Policy

* No common name in the field but a famous example is TDGammon by Tesauro that used a simulator to learn to play Backgammon

## Approaches to RL

policy: s -> pi -> a

Policy search algorithms: Directly use what you learn but learning is indirect and hence difficult due to the temporal credit assignment problem. The data set doesn't contain the actions you should take.

utility / value: s -> u -> v

Value-function based algorithms. It's possible to learn more about the world and estimate the utility as far as learning goes but it can be tricky turning this into a policy via a max function and some usage of the Bellman's equations.

s, a -> T, R -> s', r

Model based algorithm. If we can learn T (transition models) and R (rewards) then we can solve the Bellman's equations to get utility and then argmax that to get policy. This is the most direct as far learning goes but it's computationally indirect to turn the results of the learning into a policy.

Focus on the middle scenario: value based approaches!

## A new kind of Value function

The old value function

```
U(s) = R(s) + \gamma max_a \sum_{s'} {T(s, a, s') U(s')}
\pi(s) = argmax_a \sum_{s'} {T(s, a, s') U(s')}
```

Utility = reward + discounted future reward. Policy chooses the action that leads to the highest expected utility.

Q function (sometimes quality):

```
Q(s, a) = R(s) + \gamma \sum_{s'} {T(s, a, s')max_a' Q(s', a')
```

Value for arriving in S, leaving via a, proceeding optimally thereafter. Similar to Utility which is reard of the state + optimal utility thereafter, however Q ties you to action a.

U and pi can be definied via Q:

```
U(s) = max_a Q(s, a)
pi(s) = argmax_a Q(s, a)
```

## Q Learning

Q learning estimates the value of the Q function based on transitions and reward. However because it's reinforcement learning and not an MDP, we don't have R.

```
\<s, a, r, s'\>: \hat{Q}(s, a) <-^{\alpha} r + \gamma max_{a'} \hat{Q} (s', a')
```

The transition is the starting in stat s, taking action a and winding up with reward r and in state s'

We update Q by some learning rate alpha based on the imeediate reward r and discounted estimated value of the next state (\hat{Q}) because max_{a'} \hat{Q} (s', a') overall is the utility of the next state and the overall update represents the utility of the state.

Note that:

```
V <-^{\alpha} x

is equivalent to:
v <- (1 - \alpha) v + \alpha x
```

### Learning incrmentally

V_t <-^{\alpha_t} X_t

where x_t is a random variable and alpha_t has the properties that

```
\sum_{t=1}^{inf} \alpha_t = inf and
\sum_{t=1}^{inf} \alpha_t^2 < inf

which works for say alpha_t = 1 / t (1/t -> ln(t), 1/t^2 = pi^2 / 6)
```

Over time v converges to the expected value of x

## X Q from Transitions



## Learning incrementally



## Q Learning Convergence



## Choosing Actions



## Greedy Exploration


