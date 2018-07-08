---
layout: section
title: Probability - Basics
home: pgdmlai-notes
use_math: true
---

Let's play a game.

_A bag contains 3 red and 2 blue balls. The player has to pick 4 balls. Each time the player takes a ball from the bag, the color of the ball is noted and the ball is put back into the bag. If the player picks up a red ball in all his 4 attempts, he gets ₹150, otherwise, he loses ₹10._

In the long run, is this game profitable for the players or for the house? Or will everybody break even in the long run?

To answer this question, we have to 
1. Find all the possible combinations
2. Find the probability of each combination
3. Use the probability to estimate the profit/loss per player

---
##### Random Variable

Formally, a random variable is a function that **assigns a real number to each outcome in the probability space**. The random variable $X$ basically converts outcomes of experiments to something measurable.

Let (R) denote the red ball and (B) denote the blue ball. 
Let (X) be the number of red balls.


$$
BRRR  ---->  X = 3\\
BRBR  ---->  X = 2
$$


The possible values for X are :

| $X=0$ | $X=1$ | $X=2$ | $X=3$ | $X=4$ |
|:-----:|:-----:|:-----:|:-----:|:-----:|
| BBBB  | RBBB  | RRBB  | RRRB  | RRRR  |
|       | BRBB  | RBRB  | RRBR  |       |
|       | BBRB  | RBBR  | RBRR  |       |
|       | BBBR  | BRRB  | BRRR  |       |
|       |       | BRBR  |       |       |
|       |       | BBRR  |       |       |

A total of 75 players participated in the game and following is the histogram of their outcomes. 

<figure>
 <img class="med-img" src="../assets/Upgrad_Game_Histogram.png" alt="Histogram of the outcomes"/>
 <figcaption>Image Source : <a href="https://upgrad.com">Upgrad.com</a></figcaption>
</figure>


$$ Probability = \frac{\text{Favorable Outcomes}}{\text{Total Outcomes}} $$

$$ Probability \text{ (for X=2)} = \frac{\text{Frequency of 2}}{\text{Total Frequency (75)}} $$

$$ = \frac{26}{75}  \approx 0.35 $$

---
##### Probability Distribution

A _Probability Distribution_ is ANY form of representation that tells us the probability for all possible values of X. It could be any of the following:
- A Table
- A Chart
- An Equation


|   $X$   |   $P(x)$  |
|:-------:|:---------:|
| 0       | 0.027     |
| 1       | 0.160     |
| 2       | 0.347     |
| 3       | 0.333     |
| 4       | 0.133     |

---
##### Expected Value 

The expectation of a random variable is a number that attempts to capture the center of that random variable's distribution. It can be interpreted as the long-run average of many independent samples from the given distribution. More precisely, it is defined as the probability-weighted sum of all possible values in the random variable's support,

$$ \text{E}[X] = \sum_{x \in \mathcal{X}}xP(x) $$

The *Expected value* for a variable $X$ is the value of $X$ we would “expect” to get after performing the experiment once. It is also called the *expectation*, *average*, and *mean* value. Mathematically speaking, for a random variable $X$ that can take values $x_1, x_2, x_3, ..........., x_n$, the expected value (EV) is given by:

$$ \text{EV}(X) = x_1 * P(X=x_1) + x_2 * P(X=x_2) + x_3 * P(X=x_3) + ....... + x_n * P(X=x_n)$$

Let's consider the total number of players to be **1000**.

$$ 
    \text{Number of players with 0 Red ball(s)}  = 1000 \times 0.027 = 27\\
    \text{Number of players with 1 Red ball(s)}  = 1000 \times 0.160 = 160\\
    \text{Number of players with 2 Red ball(s)} = 1000 \times 0.347 = 347\\
    \text{Number of players with 3 Red ball(s)} = 1000 \times 0.333 = 333\\
    \text{Number of players with 2 Red ball(s)} = 1000 \times 0.133 = 133\\
$$


$$ 
    \text{Total number of red balls} = 0 \times 27 + 1 \times 160 + 2 \times 347 + 3 \times 333 + 4 \times 133 = 2385
$$ 


$$
    \text{Average no. of red balls for 1 game} = \frac{2385}{1000} = 2.385
$$

For our red ball game, the expected value came out to be **2.385**. What does that mean? How does that even help us with our original question, which was how much money, on average, are the players expected to make?


To find out if the house would win or lose money in the long run, we would need a _different Random Variable_. A better random variable would be amount of money a player wins.

Let $X$ be the money won by a player after playing the game once. $X$ can take two values : $+150$ and $-10$.

$$ 
    P(X=+150) = P(\text{4 red balls}) = 0.133 \\
    P(X=-10) = P(\text{0,1,2 or 3 red balls}) = 0.027 + 0.160 + 0.347 + 0.333 = 0.867\\
    EV = (150 \times 0.133) + (-10 \times 0.867) = 11.28
$$

A player in average wins ₹11.28 per game. This would prove to be great loss the house in the long run. To make profit, the expected value should be negative, which signifies the player loses money. To make profit, we can either reduce the winning amount or increase the penalty amount. 

---

##### Variance 

Whereas expectation provides a measure of centrality, the variance of a random variable quantifies the spread of that random variable's distribution. The variance is the average value of the squared difference between the random variable and its expectation,

$$ \text{Var}(X) = \text{E}[(X - \text{E}[X])^2] $$