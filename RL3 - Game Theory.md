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
| -------------- | ---------------- | ---------- |
| A cooperates   | (-1, -1)         | (-9, 0)    |
| A defects      | (0, -9)          | (-6, -6)   |

The "best" outcome on average for both prisoners is to both cooperate and between both of them they spend the least time in prison.

Based on the above "costs" or "rewards" it makes sense however it always makes sense to always defect instead of cooperate. If the other person cooperates defecting is the difference between spending one month in jail or spending no time in jail. If B defects, it's the option to spend 9 months in jail versus 6 months in jail. This dominance of defecting always being the better option results in the "worst" outcome though.

## A Beautiful Equilibrium

N players with strategies S_1, S_2, ... S_n

S_1* \in S_1, S_2* \in S_2, ..., S_1n* \in S_n

are a Nash equilibrium iff for all S_i* = argmax_si utility_i(S_1*, S_2*, ... S_n*)

no reason for anyone to change strategies.

This can applies to pure and mixed strategies.

Some theorems as a result of Nash Equilibrium:
- In the n-player pure strategy game, if equilibrium of strictly dominated strategies eliminates all but one combination, that combination is the Nash Equilibrium (done iteratively possibly)
- Any Nash Equilibrium will survive elimination of strictly dominated strategies
- If n (number of players) is finite and for all i, S_i is finite (finite number of strategies for each player) there exists a (mixed) Nash Equilibrium

## 2 Step

Two step prisoner's dilemma. If you encounter multiple prisoner's dilemmas, then perhaps it's in your interest to cooperate as a signal to the other player that you're the type to cooperate so that the overall cost to you is reduced (i.e. 2x -1 cost instead of 2x -6 cost)

In order to flesh out this you could possibly make an extended matrix to account steps and for people's behaviors in other steps.

However... It doesn't matter. In the final game there is only one game left and all of the previous games are sunk costs. Therefore it is determined that the players will end up in the -6, -6 step. And since we know the outcome of the final game therefore the n-1 game is the "final" game. Therefore proof by induction dictates that we'll always deduct.

If you have an n repeated game then the n repeated Nash equilibrium is solution.

If you're in a Nash equilibrium you won't leave the Nash equilibrium but it's possible to have multiple Nash equilibriums but determining which equilibrium you'll wind up in is beyond the scope of the course.

## Summary

- Game Theory is depressing
- Change the game i.e. if the utilities were different then the equilibrium that was discussed might change
- Mechanism design - changing utility to encourage different behaviors
- Game as a tree
- Game as a matrix - the matrix is all that is needed
- Minimax
- Hidden/Perfect
- (Non) zero sum
- (Non) deterministic
- Strategies: Pure vs Mixed
- Prisoner's Dilemma
- Nash
