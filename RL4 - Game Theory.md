# RL4 - Game Theory

## Iterated Prisoner's Dilemma

Normal prisoner's dilemma has the following matrix:

|                | B Cooperates     | B Defects  | 
| -------------- | ---------------- | ---------- |
| A cooperates   | (-1, -1)         | (-9, 0)    |
| A defects      | (0, -9)          | (-6, -6)   |

In one game the only rational thing to do is to defect. Even if they are given finite and known multiple turns to interact then they will still ultimately defect because in the final game the best option will be to defect and that unravels to all of the previous games. 

What happens if there are unknown number of rounds left? It seems like it should be similar to the above situation, however that isn't the case.

## The Uncertain End

The probability the game continues is gamma.

This setup resembles MDP.

Gamma resembles discount factor.

## Tit-for-Tat

Tit-for-Tat strategy is to Cooperate first and then do the what the other person did in the previous turn.

## Facing TfT

Against always defect: TfT cooperates then switches to always defecting

Against TfT: Both always cooperate

Against always cooperates: TfT always cooperates

## Finite State Strategy

Finite state machine can represent strategies.

Facing a TfT strategy, it may still be beneficial to not cooperate or TfT. i.e. if the IPD game if gamma is < 1/6 then the game is likely enough to end that you can defect without retaliation.

## Best Responses in IPD

With TfT in IPD you can have multiple Nash Equilibriums.

## Folk Theorem

General idea: In repeated games, the possibility of retaliation opens the door for cooperation

What's a "Folk Theorem"? In mathematics, results known, at least to experts in the filed and considered to have established status, but not published in complete form.

In game theory though, folk theorem (it refers to a particular folk theorem) refers to a particular result: describes the set of payoffs that can result from Nash strategies in repeated games.

## Repeated Games

General idea: In repeated games, the possibility of retaliation opens the door for cooperation

2 player plot can visualize the outcomes. The 2 players are the axis of the graphs and the players' joint outcomes are points in a 2-D graph.

The matrix is all you need but represents in a different way. Kind of washes out some information i.e. how some strategies relate to one another.

The convex hull between the points represents all of the different achievable average outcomes across an IPD. The outcomes are not necessarily Nash or beneficial to either player - simply represents the range of possibilities.

## Minmax Profile

Pair of payoffs, one for each player, that represent the payoffs that can be achieved by a player defending itself from a malicious adversary (trying to lower my score). Zero sum game!

Back & Stravinsky, Battle of Sexes, Backstreet & Sting:

Suppose Curly and Smooth get out and they celebrate by going to one of two concerts, but they lost touch and aren't able to communicate. If they both go to separate concerts they'll be sad (0, 0) outcome. But Curly prefers Sting (1, 2) and Smooth prefers Backstreet (2, 1)

|    | B                | S          | 
| -- | ---------------- | ---------- |
| B  | (1, 2)           | (0, 0)     |
| A  | (0, 0)           | (2, 1)     |

In this case, taking into account mixed strategies and a malicious adversary, either player can guarantee an expected reward of at least 2/3. Take the expected value given a mixed strategy and minimize.

Minmax: pure

Security level: mixed

## Security Level Profile

Minmax of PD is (-6, -6) because malicious is gonna defect and your best option is to defect as well.

Region above and to the right of the minmax point is the (preferable) acceptable region - it is better than what you can guarantee against someone acting maliciously.

## Folksy Theorem

Any feasible payoff profile that strictly dominates the minmax / security level profile can be realized as a Nash Equilibrium payoff profile, with sufficiently large discount factor.

Proof: If it strictly dominates the minmax profile, can use it as a threat. Better off doing what you are told.

## Grim Trigger

State of mutual benefit and state of dealing vengeance.

Cooperation keeps you in the state of mutual benefit, but if you cross the line you enter the state of dealing out of vengeance and stay in that state forever.

Nash Equilibrium!

## Implausible Threats

A plausible threat is one that is subgame perfect: Always best response independent of history.

TfT vs Grim:

Nash? Yes!

Subgame perfect? Given an alternative history, that isn't necessarily consistent with Grim and TfT, Grim would produce suboptimal results.

## TfT vs TfT

TfT vs TfT is not subgame perfect either. If D/C were initialized into TfT vs TfT then they will proceed to alternate C and D which would cause an average score of -4.5

If D/D was initialized they will have an average score of -6.

The optimal would be to cooperate and average out a reward of -1.

## Pavlov

TfT: Repeat what opponent did.

Pavlov: Cooperate if agree, defect if disagree.

## Pavlov vs Pavlov

Pavlov is nash! Both start of cooperating and stay cooperating.

## Pavlov is Subgame Perfect

You can give it any starting sequence (CC, CD, DC, DD) and it will eventually transition to CC state. This means it's subgame perfect!

Pavlov leads to plausible threats!

## Computational Folk Theorem

Given a 2 player, bimatrix game (each player has a separate reward structure), you can build pavlov-like machines for any game. And using Pavlov you can construct subgame perfect nash equilibrium for any game in polynomial time.

- Pavlov if possible
- If Pavlov is not possible the game is Zero-sum like (solve an LP)
- At most one player improves

## Stochastic Games and Multiagent  RL

MDP : RL :: Stochastic game : Multiagent RL

Game:

- 3x3 grid
- Each player can go N, S, E, W, X
- First to reach goal get $100
- Both arrive, both win
- Semi wall (50% go through, above each starting cell)

|    | $                |            | 
| -- | ---------------- | ---------- |
|    |                  |            |
| A  |                  | B          |

Nash? pair of policies such that neither would prefer to switch

They can go both N through the semi-wall and each gets a reward 2/3 of the time.

But this isn't a Nash equlibrium. One of the agents can switch to going to the center and get a reward 100% of the time. This is in Nash!

## Stochastic Games

Stochastic game:

- S: states s
- A_i: Actions for player_i a, b a \in A_1 b \in A_2
- T: Transitions T(s, (a, b), s')
- R_i: Rewards for player i R_1(s, (a, b)), R_2(s, (a, b))
- \gamma: Discount \gamma

Described by Shapley. Actually published before Bellman published on MDP.

## Models & Stochastic Games

Stochastic games is a generalization of other models:

If R_1 = -R_2 it becomes a zero-sum game

If T(s, (a, b), s') = T(s, (a, b'), s') for all b' and R_2(s, (a, b)) = 0, and R_1(s, (a, b)) = R_1(s, (a, b')) for all b' then it becomes an MDP

If |S| = 1 then it becomes a repeated game.


## Zero-Sum Stochastic Games



## General Sum Games



## Lots of Ideas



## Summary



