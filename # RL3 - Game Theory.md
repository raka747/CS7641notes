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

## Von Neumann



## Minipoker



## Mixed Strategies



## Lines



## Center Game



## Snitch



## A Beautiful Equilibrium



## 2 Step



## Summary


