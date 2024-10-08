# Zarconia-a-strategy-game-of-dice
You are tasked with analyzing the outcomes of a complex game of dice called Zarconia. Zarconia involves rolling a pair of ten-sided dice 
(possible outcomes ranging from 1 to 10), and players accumulate scores based on a combination of the two dice rolls, with additional rules for bonuses and penalties.

## Objective
Develop a Python script to perform a Monte Carlo simulation for the Zarconia dice game. The goal is to understand the distribution of total scores and assess
the impact of different game parameters.

## Game Rules
1. During the "first turn", a player rolls two ten-sided dices, each dice has faces labeled from 1 to 10
2. The basis score is the sum of the two dice rolls
3. If the dices show consecutive numbers (eg., 3 and 4, or 8 and 9), the player receives a bonus equal to the sum of the consecutive numbers. If a 1 and 10 are rolled, they are considered consecutive, thus the player receives a bonus of 11 points.
4. If the two dices show identical numbers, the player incurs a penalty equal to the square of that number
5. During the "second turn", players can choose to re-roll one, or both, of the dices once, but must keep the second result of this re-roll.

   Assume that players have no information about the dice roll outcomes of the opponents during the entire game.

## Challenge No. 1
Under the assumption that no one chooses to reroll in the second turn, calculate the expected score of one game. Show some statistics and metrics on the distribution of the outcome of this game.
### Solution:
The implementation of a Monte Carlo method to calculate the expectation value of the score under the prescribed assumptions above is straightforward. In the source code, "zarconia_monte_carlo.py", we have implemented a function called "strategy1_score" which does this.
But more interestingly, one can derive a simple mathematical expression for the expectation value of the score, $E[s]$. Naturally,
```math
E[s] = \sum^N_{x,y=1} P(x,y)*[x + y + \text{bonus}(x,y) - \text{penalty}(x,y)]
```
where $N$ is the highest number on the dice, $x$ and $y$ are the outcomes after rolling the two dices, and $\text{bonus}(x,y)$ and $\text{penalty}(x,y)$ are the functions yielding the bonus and penalty scores, respectively. In particular,
```math
\text{bonus}(x,y) = \begin{cases}
x + y \ , & \text{if } \|x-y\| \in \{1, N-1\} \\
0 \, & \text{otherwise}
\end{cases}
```
```math
\text{penalty}(x,y) = \begin{cases}
x^2 \ , & \text{if } x=y \\
0 \, & \text{otherwise}
\end{cases}
```
Simplifying the expression for $E[s]$ yields,
```math
E[s] = \left(\frac{N+1}{N}\right)\cdot\left( \frac{4N+11}{6}\right) - \frac{3}{2}\cdot \delta_{N,2}
```
where $\delta_{N,2}$ is the Kronecker delta. We have given a detailed derivation in the document "Notes_Zarconia_game.pdf".

For N=10, the analytical expression for the expectation score is 9.35, which is close to the Monte Carlo result (i.e. 9.33).
