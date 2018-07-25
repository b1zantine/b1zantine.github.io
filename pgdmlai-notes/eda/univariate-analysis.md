---
layout: section
title: Univariate Analysis
home: pgdmlai-notes
---


As the term **“univariate”** suggests, it deals with analysing variables one at a time. It is important to separately understand each variable before moving on to analysing multiple variables together.


Given a data set, the first step is to understand what it contains. Information about a data set can be gained simply by looking at its metadata. Metadata, in simple terms, is the data that describes the each variable in detail. Information such as the size of the data set, how and when the data set was created, what the rows and variables represent, etc. are captured in metadata. 

--- 

##### Types of Variables

Variables can be broadly classified into

1. __Quantitative / numeric variables__

    The most common type is quantitative variables. These are simply numeric variables which can be added up, multiplied, divided etc. For example, salary, number of bank accounts, runs scored by a batsman, the mileage of a car etc.

2. __Categorical variables__

    1. __Ordered__ ones have some kind of ordering. 
        Some examples are
        * Salary = High-Medium-low
        * Month = Jan-Feb-Mar etc.

    2. __Unordered__ ones do not have the notion of high-low, more-less etc. 
        Example:
        * Type of loan taken by a person = home, personal, auto etc.
        * Organisation of a person = Sales, marketing, HR etc.


--- 

#### UnOrdered Categorical Variables

Now, imagine someone (say a client) gives you only an unordered categorical variable (and nothing else!), such as a column of size 4000 named 'country_of_person' with 130 unique countries and asks you 'can you extract anything useful from just this one variable?'. 

Since, the data that the column can contain is from a predefined category set, we can count the frequency each category and rank it based on the frequency.

This type of distribution is called [__"rank-frequency distribution"__](https://en.wikipedia.org/wiki/Rank-size_distribution){:target="_blank"}. 

Rank-frequency plots enable you to extract meaning even from seemingly trivial unordered categorical variables such as country, name of an artist, name of a github user etc.

This distribution follows the [__power law__](https://en.wikipedia.org/wiki/Power_law){:target="_blank"}. When plotted on a linear scale, they follow an *exponential curve*. When they are plotted on a <mark>log-log</mark> scale, they tend to follow a *straight line*.

Real-world observations such as [**Zipf's law**](https://en.wikipedia.org/wiki/Zipf%27s_law){:target="_blank"}, the [**Yule distribution**](https://en.wikipedia.org/wiki/Yule_distribution){:target="_blank"}, or the [**Pareto distribution**](https://en.wikipedia.org/wiki/Pareto_distribution){:target="_blank"} follows **power law**. 

__Why plotting on a log-log scale helps?__

The objective of using a log scale is to make the plot readable by changing the scale. For example, the first ranked item had a frequency of 29000, the second ranked had 3500, the seventh had 700 and most others had very low frequencies such as 100, 80, 21 etc.  The range of frequencies is too large to fit on the plot.

Plotting on a log scale compresses the values to a smaller scale which makes the plot easy to read.

This happens because log(x) is a much smaller number than x. For example, log(10) = 1, log(100) = 2, log(1000) = 3 and so on. Thus, log(29000) is now approx. 4.5, log(3500) is approx. 3.5 and so on. What was earlier varying from 29000 to 1 is now compressed between 4.5 and 0, making the values easier to read on a plot.

> Employment Data :  [__Download__](../assets/data/employment-data.csv)

<figure>
 <img class="med-img" src="../assets/images/rank-freq-linear.png" alt="Rank-Frequency Plot (linear)">
 <figcaption>Employee Location : Rank-Frequency Plot (linear)</figcaption>
</figure>

<figure>
 <img class="med-img" src="../assets/images/rank-freq-log-log.png" alt="Rank-Frequency Plot (log-log)">
 <figcaption>Employee Location : Rank-Frequency Plot (log-log)</figcaption>
</figure>

--- 

#### Ordered Categorical Variables

A simple histogram can reveal interesting insights. This is an extremely important takeaway — _whenever you have a continuous or an ordered categorical variable, make sure to plot a histogram or a bar chart and observe any unexpected trends in it._

__Tendulkar Batting - Univariate Analysis__

The dataset given below contains Sachin Tendulkar's ODI batting statistics from about 1989 to 2012. 

> Tendulkar ODI data (csv) :  [__Download__](../assets/data/tendulkar_ODI.csv)

The variables 'Runs' and 'X4s' respectively represent the number of runs scored and number of 4s hit by him in each match. These are two ordered categorical variables that we will analyze here.

Runs', which should ideally be a numeric variable, contains some entries such as DNB (Did Not Bat), 8* (Not out at 8 runs) etc. These has to be cleaned to prevent quality issues. 

Similarly, in 'X4s', there are some missing entries represented by "-". While cleaning "-" are converted to "0". 

> Univariate Analysis on Tendulkar ODI data (ipynb)  :  [__Download__](../assets/notebook/tendulkar_quiz.ipynb)


**Runs Scored by Tendulkar**: Plot a bar chart showing runs scored on the x-axis and frequency/count on the y-axis. In which bucket has he scored runs the most often?

<figure>
 <img class="med-img" src="../assets/images/tendulkar_runs_hist.png" alt="Histogram: Runs scored by Tendulkar">
 <figcaption>Histogram: Runs scored by Tendulkar</figcaption>
</figure>

From the above plot, we can clearly conclude that the answer would be **0-10 runs**.


**Number of Fours**: What is the most common value of the variable X, where X represents the number of 4s hit by him?

<figure>
 <img class="med-img" src="../assets/images/tendulkar_4s_hist.png" alt="Histogram: 4s scored by Tendulkar">
 <figcaption>Histogram: 4s scored by Tendulkar</figcaption>
</figure>

From the above plot, the answer is clearly **0**.

