# RL3 - Game Theory

## What is Game Theory?

Various definitions:

- Mathematics of conflicts or conflicts of interest when making optimal interests
- Single agents -> Multiple agents (up until this point kind of assuming other agents are a part of the world)
- Economics (& politics)
- Increasingly a part of AI

Ways of thinking when you're not the only thing thinking with intention i.e. there are other agents acting either against or with you.

## A simple game

Two agents A & B. Game Tree, 2  nodes representing states, edges representing actions. Leaves = A's reward & B's - reward.

This is a 2 player  zero sum finite deterministic game of perfect information.

This is the simplest possible game. In MDP we had policies. In Game Theory we have strategies.

Ultimately though, a game can be captured in a matrix of all strategies a and b can choose along the axes of the matrix and the outcome of the games per those strategies as the cells of the matrix.

## Minimax

A must consider the worst case counter and B must consider the worst case as well. So ultimately A attempts to maximizes considering B is minimax - hence the minimax algorithm. Alpha beta is a more efficient way of finding the exact same solution of minimax. 

## Fundamental Result

Theorem: In a 2-player, zero-sum, deterministic game of perfect information minimax (=maximin)... and there always exists an optimal pure strategy for each player.

Optimal is rational. I'm attempting to maximize my reward and everyone else is attempting to maximize their reward and everyone know this about everyone.

## Game Tree

More complex scenario: 2-player, zero-sum, non-deterministic game of perfect information. In this scenario there is chance involved, so it is slightly more complicated.

The matrix doesn't enable to perform an exact reconstruction of the precise tree that produced the matrix however it ultimately doesn't matter as far as determining which strategy will be picked


## Von Neumann

Von Neumann's Theorem applies again: via minimax = maximin and there always exists an optimal pure strategy for each player.

## Mini-poker

An even more complex scenario: 2-player, zero-sum, non-deterministic game of hidden information

Mini-poker game description:
- A is dealt a card, red or black 50%
- A may resign if red: -20 for A
- Else A holds
    - B resigns: + 10
    - B sees:
        - if red: -40
        - if black + 30
- If A is dealt a  back card and holds
    - Black can resign: +10
    - B can see: +30

This can be expressed in a matrix taking into account the expected  outcomes. However whether you do minimax (from A's perspective) or maximin (from B's perspective) yields different results for the outcome of the game. And this breaks Von Neumann's theorem. Ultimately consistency can be exploited by the opposite player, so pure strategies are no longer viable.

## Mixed Strategies

A mixed strategy implies a distribution over strategies. i.e.  in the above game P probability of being a holder.

## Lines and Center Game

When using a mixed strategy between 2 options for both players one can examine one of the players as deterministic and calculate the outcome as a function of the other probabilistic player's probability of picking a strategy. The maximin of the two functions of the two deterministic possibilities gives the ultimate outcome of the scenario or game.

## Snitch

Relaxing even more things! 2-player, non-zero-sum, non-deterministic game of hidden information.

Prisoner's dilemma: 2 criminals caught and put in separate jails. Each person is given the option to snitch on the other guy.

The Matrix:

|                | B Cooperates     | B Defects  | 
| A cooperates   | (-1, -1)         | (-9, 0)    |
| A defects      | (0, -9)          | (-6, -6)   |




## A Beautiful Equilibrium



## 2 Step



## Summary


