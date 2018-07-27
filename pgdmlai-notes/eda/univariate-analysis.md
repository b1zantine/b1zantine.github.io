---
layout: section
title: Univariate Analysis
home: pgdmlai-notes
use_math: true
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

Now, imagine someone $$\text{(say a client)}$$ gives you only an unordered categorical variable $$\text{(and nothing else!)}$$, such as a column of size 4000 named 'country_of_person' with 130 unique countries and asks you 'can you extract anything useful from just this one variable?'. 

Since, the data that the column can contain is from a predefined category set, we can count the frequency each category and rank it based on the frequency.

This type of distribution is called [__"rank-frequency distribution"__](https://en.wikipedia.org/wiki/Rank-size_distribution){:target="_blank"}. 

Rank-frequency plots enable you to extract meaning even from seemingly trivial unordered categorical variables such as country, name of an artist, name of a github user etc.

This distribution follows the [__power law__](https://en.wikipedia.org/wiki/Power_law){:target="_blank"}. When plotted on a linear scale, they follow an *exponential curve*. When they are plotted on a <mark>log-log</mark> scale, they tend to follow a *straight line*.

Real-world observations such as [**Zipf's law**](https://en.wikipedia.org/wiki/Zipf%27s_law){:target="_blank"}, the [**Yule distribution**](https://en.wikipedia.org/wiki/Yule_distribution){:target="_blank"}, or the [**Pareto distribution**](https://en.wikipedia.org/wiki/Pareto_distribution){:target="_blank"} follows **power law**. 

__Why plotting on a log-log scale helps?__

The objective of using a log scale is to make the plot readable by changing the scale. For example, the first ranked item had a frequency of 29000, the second ranked had 3500, the seventh had 700 and most others had very low frequencies such as 100, 80, 21 etc.  The range of frequencies is too large to fit on the plot.

Plotting on a log scale compresses the values to a smaller scale which makes the plot easy to read.

This happens because $$log(x)$$ is a much smaller number than x. For example, $$log(10) = 1$$, $$log(100) = 2$$, $$log(1000) = 3$$ and so on. Thus, $$log(29000)$$ is now approx. 4.5, $$log(3500)$$ is approx. 3.5 and so on. What was earlier varying from 29000 to 1 is now compressed between 4.5 and 0, making the values easier to read on a plot.

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

Runs', which should ideally be a numeric variable, contains some entries such as DNB $$\text{(Did Not Bat), 8* (Not out at 8 runs)}$$ etc. These has to be cleaned to prevent quality issues. 

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

---

#### Quantitative Variables


Numeric variables can be treated as ordered categorical variables. For analysis, you can deliberately convert numeric variables into ordered categorical, for example, if you have incomes of a few thousand people ranging from $$ \text{\$5,000 to \$100,000} $$, you can categorise them into bins such as [5000, 10000], [10000,15000] and [15000, 20000].

This is called **'binning'**.

Apart from this, we can use summary metrics to do univariate analysis on a single field.


| Terms | Description|
| ----- | ---------- |
| First $$\text{(Q1)}$$ and Third $$\text{(Q3)}$$ Quantile | Q1: Value at 25th percentile of the range; Q2: Value at 75th percentile of the range |
| Median | Middle value of a data set,ie value at 50th percentile |
| Mean | Average value of a dataset |
| Mode | Value that occurs most often in the dataset |
| Variance | Measure of the deviation of the data points from the mean of the set |
| Standard Deviation | Measure of the deviation of the data points from the mean of the set. $$ SD = { \sqrt {Variance} } $$ |


While mean gives an average of all the values, median gives a typical value that could be used to represent the entire group. <mark>As a simple rule of thumb, always question someone if someone uses the mean, since median is almost always a better measure of ‘representativeness’</mark>.


> __which metric to use?__

> Consider the example — there are a group of middle-class IT employees and Bill Gates in a room. If you want to get a rough sense of the income made by a typical IT employee, which metric would you choose?

> The average, calculated taking Bill Gates’ income into account, would be an overwhelmingly large number far from the income of any other IT employee in the room. On the other hand, the median will not consider Bill Gates’ income and would be more representative.


**Mode** on the other hand is used only for categorical data. In unordered categorical variables, any order or difference between values is not defined. So, using median and mean make no sense here.

The **interquartile range $$\text{(IQR)}$$** is a measure of variability, based on dividing a data set into quartiles.
Quartiles divide a rank-ordered data set into four equal parts. The values that divide each part are called the first, second, and third quartiles; and they are denoted by Q1, Q2, and Q3, respectively.

* Q1 is the "middle" value in the first half of the rank-ordered data set.
* Q2 is the median value in the set.
* Q3 is the "middle" value in the second half of the rank-ordered data set.

**The interquartile range is equal to Q3 minus Q1.**

Standard deviation and interquartile difference are both used to represent the spread of the data.

_Interquartile difference is a much better metric than standard deviation if there are outliers in the data. This is because the standard deviation will be influenced by outliers while the interquartile difference will simply ignore them._

For Quantitative Variables, we can use **box plots** to understand the spread of the data.

* Why median is better than mean in some cases?

        Median is better than Mean when we have outliers in the dataset.

* Why Standard Deviation exaggerates the spread in some cases?

        Again the same reason as above. When there are outliersin the dataset, the SD value might get shot up and fails to convey the actual spread of the data.

* How to communicate the amount of spread?

        To communicate the amount of spread, the _quartiles_ can be used instead. The difference between Q3 and Q1 gives better picture. Box plots can be used to visualize it. 


A good way to visualise quartiles is to use a box plot. The 25th percentile is represented by the bottom horizontal line of the box, the 75th is the top line of the box, and the median is the line between them.


<figure>
 <img class="small-img" src="../assets/images/box-plot.png" alt="Box Plot">
 <figcaption>Box Plot</figcaption>
</figure>

---


#### Summary

1. **Metadata description** describes the data in a structured way. You should make it a habit of creating a metadata description for whatever data set you are working on. Not only will it serve as a reference point for you, it will also help other people understand the data better and save time.

2. **Distribution plots** reveal interesting insights about the data. You can observe various visible patterns in the plots and try to understand how they came to be.

3. **Summary metrics** are used to obtain a quantitative summary of the data. Not all metrics can be used everywhere. Thus, it is important to understand the data and then choose what metric to use to summarise the data.