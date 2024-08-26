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
