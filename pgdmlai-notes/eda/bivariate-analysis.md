---
layout: section
title: Bivariate Analysis
home: pgdmlai-notes
---

---

How to analyse **pairs of continuous variables** at a time? 

For example, how the sales figure depends on the marketing spends? Or, for that matter, how two continuous variables depend on each other? Is there any way or concept to identify the relationship between two variables?

#### Continuous Variables

Usually, when trying to analyze two variables, we tend to find the correlation between them.

**Correlation** is a number between **-1 and 1** which quantifies the extent to which two variables ‘correlate’ with each other.

- If **one increases** as the **other increases**, the correlation is **positive**

- If **one decreases** as the **other increases**, the correlation is **negative**

- If one **stays constant** as the **other varies**, the correlation is **zero**

 
In general, a positive correlation means that two variables will increase together and decrease together, e.g. an increase in rain is accompanied by an increase in humidity. A negative correlation means that if one variable increases the other decreases, e.g. in some cases, as the price of a commodity decreases its demand increases.


A perfect positive correlation means that the correlation coefficient is exactly 1. This implies that as one variable moves, either up or down, the other one moves in the same direction. A perfect negative correlation means that two variables move in opposite directions, while a zero correlation implies no relationship at all. 


<figure>
 <img class="med-img" src="../assets/images/correlation-scatter.jpg" alt="Correlation">
 <figcaption>Correlation (Source: http://www.pythagorasandthat.co.uk/scatter-graphs)</figcaption>
</figure>


##### Correlation matrix

The data set attached below contains the exchange prices of various currencies in the month of July 2016. This data set is taken from the [International Monetary Fund website](https://www.imf.org/external/np/fin/data/param_rms_mth.aspx){:target="_blank"}.

> Currencies Data:  [__Download__](../assets/data/currencies.csv)

The following currencies are being analyzed: Euro, Japanese Yen, U.K. Pound Sterling, US Dollar, Australian Dollar, Indian Rupee.

{% highlight python %}
fig, ax = plt.subplots(figsize=(10,10))
corr = df[["Indian Rupee", "Australian Dollar", "U.S. Dollar", "Japanese Yen", "Euro"]].corr()
sns.heatmap(corr, xticklabels=corr.columns.values, yticklabels=corr.columns.values, annot=True, ax=ax)
plt.show()
{% endhighlight %}

<figure>
 <img class="med-img" src="../assets/images/currencies_correlation_heatmap.png" alt="Correlation between Currencies">
 <figcaption>Correlation matrix</figcaption>
</figure>

---

#### Categorical Variables

The categorical bivariate analysis is essentially an extension of the **segmented univariate** analysis to another categorical variable. In **segmented univariate analysis**, you compare metrics such as ‘**mean of X**’ across various segments of a categorical variable, e.g. mean marks of a student are higher for ‘degree and above’ than other levels of the mother’s education; or the median income of educated parents is higher than that of uneducated ones, etc.

 
In the **categorical bivariate analysis**, you extend this comparison to other categorical variables and ask — is this true for all categories of another variable, say, men and women? Take another categorical variable, such as state, and ask — is the median income of educated parents higher than that of uneducated ones **in all states**?

Thus, you are drilling down into another categorical variable and getting closer to the true patterns in the data. In fact, you may also go to the next level and ask — is the median income of educated parents higher than that of uneducated ones (variable 1)  in all states (variable 2) for all age groups (variable 3)? This is what you may call **‘trivariate analysis’**, and though it gives you a more granular version of the truth, it gets a bit complex to make sense of and explain to others (and hence it is not usually done in EDA).

_Thus, remember that doing only conducting segmented univariate analysis may deceive you into thinking that a certain phenomenon is true without asking the question — is it true for all sub-populations or is it true only when you aggregate information across the entire population?_


So in general, there are two fundamental aspects of analysing categorical variables:

1. To see the distribution of two categorical variables. For example, if you want to compare the number of boys and girls who play games, you can make a ‘cross table’ as given below:

    <figure>
    <img class="full-img" src="../assets/images/Cross_table.png" alt="Cross Table">
    <figcaption>Cross Table</figcaption>
    </figure>

    _From this table, firstly, you can compare boys and girls across a fixed level of ‘play games’, e.g. a higher number of boys play games every day than girls, a higher number of girls never play games than boys, etc. And secondly, you can compare the levels of ‘play games’ across a fixed value of gender, e.g. most boys play every day and very few play once a month or never._

2. To see the distribution of two categorical variables with one continuous variable. For example, you saw how a student’s percentage in science is distributed based on the father’s occupation (categorical variable 1) and the poverty level (categorical variable 2).

Usually, more than two variables are not analyzed at a time, though there are ways to do that. Machine learning models are essentially a way to do that. 