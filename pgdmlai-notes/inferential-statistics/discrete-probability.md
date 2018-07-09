---
layout: section
title: Discrete Probability - Binomial Distribution
home: pgdmlai-notes
use_math: true
---
---
Let's quickly review two important rules in probability. 

##### Additional Rule
Consider two events $A$ and $B$.

$$ P(A\text{ or }B) = P(A) + P(B) - P(A\text{ and }B) $$

When the two events $A$ and $B$ are _mutually exclusive_, 

$$ P(\text{A or B}) = P(A) + P(B) $$

##### Multiplication Rule
Consider two events $A$ and $B$. If the two events are _independent_,

$$ P(A\text{ or }B) = P(A) . P(B) $$

---

In the [previous section](../basic-probability/), we discussed a game of picking balls from a bag containing 3 red balls and 2 blue balls.

Let (R) denote the red ball and (B) denote the blue ball. 
Let (X) be the number of red balls.

The possible values for X are :

| $X=0$ | $X=1$ | $X=2$ | $X=3$ | $X=4$ |
|:-----:|:-----:|:-----:|:-----:|:-----:|
| BBBB  | RBBB  | RRBB  | RRRB  | RRRR  |
|       | BRBB  | RBRB  | RRBR  |       |
|       | BBRB  | RBBR  | RBRR  |       |
|       | BBBR  | BRRB  | BRRR  |       |
|       |       | BRBR  |       |       |
|       |       | BBRR  |       |       |


We calculated the probabilities by engaging 75 participants and using them to calculate the probability distribution.


|   $X (Number of Red balls)$   |   $P(x)$  |
|:-----------------------------:|:---------:|
| 0                             | 0.027     |
| 1                             | 0.160     |
| 2                             | 0.347     |
| 3                             | 0.333     |
| 4                             | 0.133     |


What if we do not have the resources to collect enough data? How about calculating the probability distribution using some pen and paper?

We can use the muliplication rule to calculate it. 

In a single trial, the probability of getting a red ball $P(R) = 3/5 = 0.6$ and the probability of getting a blue ball is $P(B) = 2/5 = 0.4$. 

Also, $ P(BRRR) = P(B) * P(R) * P(R) * P(R) = 0.4 \times 0.6 \times 0.6 \times 0.6 = 0.0864$

Therefore the probability of getting 3 red balls would be

$$
  \begin{align*}
    P(\text{3 Red balls}) = P(X=3) = P(BRRR) + P(RBRR) + P(RRBR) + P(RRRB) \\\\
    = 4 \times 0.0864 = 0.3456
  \end{align*}
$$


|   $X (Number of Red balls)$   |   $P(x)$  |
|:-----------------------------:|:---------:|
| 0                             | 0.0256    |
| 1                             | 0.1536    |
| 2                             | 0.3456    |
| 3                             | 0.3456    |
| 4                             | 0.1296    |

<figure>
 <img class="med-img" src="../assets/Upgrad_Game_Theoretical_vs_Observed_Distribution.png" alt="Theoretical vs. Observed Distribution"/>
 <figcaption>Image Source : <a href="https://upgrad.com">Upgrad.com</a></figcaption>
</figure>


There is slight difference between theoretical and observed distribution values, because, in case of the observed distribution, the number of samples $(75)$ is relatively small and when the number of samples is large enough, the values will reach closer to the theoretical probability distribution values. 


|   $X$   |   $P(X)$                          |
|:-------:|:---------------------------------:|
| 0       | $(0.4)^4$                         |
| 1       | $4 \times (0.6) \times (0.4)^3$   |
| 2       | $6 \times (0.6)^2 \times (0.4)^2$ |
| 3       | $4 \times (0.6)^3 \times (0.4)$   |
| 4       | $(0.6)^4$                         |


Let's consider $p$ be the probability of picking up a red ball in one trial and $1-p$ be the probability of picking up a blue ball. 

|   $X$   |   $P(X)$      |
|:-------:|:-------------:|
| 0       | $(1-p)^4$     |
| 1       | $4p(1-p)^3$   |
| 2       | $6p^2(1-p)^2$ |
| 3       | $4p^3(1-p)$   |
| 4       | $p^4$         |


Generalizing it even further.

Let $n$ be the number of trials and $r$ be number of trials where red ball was picked. Therefore the number of combinations you can pick $r$ red balls is $^nC_r$.

|   $X$   |   $P(X)$                   |
|:-------:|:--------------------------:|
| 0       | $nC_0 (p)^0 (1-p)^{n}$     |
| 1       | $nC_1 (p)^1 (1-p)^{n-1}$   |
| 2       | $nC_2 (p)^2 (1-p)^{n-2}$   |
| 3       | $nC_3 (p)^3 (1-p)^{n-3}$   |
| .       | .                          |
| .       | .                          |
| n       | $nC_n (p)^n (1-p)^{0}$     |


Thus, the **binomial probability equation** is derived.


$$P(X = r) =\text{ }^nC_r (p)^r (1-p)^{n-r} $$

Where $n$ is **no. of trials**, $p$ is **probability of success** and $r$ is **no. of successes** after $n$ trials.


However, there are some conditions that need to be followed in order for us to be able to apply the formula.

1. **Total number** of trials is <mark>fixed</mark> at $n$
2. Each trial is **binary**, i.e., has only **two possible outcomes** - success or failure
3. **Probability of success** is same in all trials, denoted by $p$

---
##### Cumulative Probability Distribution


The **cumulative probability of X**, denoted by $F(x)$, is defined as the **probability of the variable being less than or equal to $x$**.

In mathematical terms, you would write cumulative probability $F(x) = P(X \leq x)$. For example, $F(4) = P(X \leq 4)$, $F(3) = P(X \leq 3)$.


|   $X$   |   $F(X) = P(X \leq x)$      |
|:-------:|:---------------------------:|
| 0       | 0.0256                      |
| 1       | 0.1792                      |
| 2       | 0.5248                      |
| 3       | 0.8704                      |
| 4       | 1.0000                      |