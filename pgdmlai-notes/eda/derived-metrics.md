---
layout: section
title: Derived Metrics
home: pgdmlai-notes
---


#### What are Derived Metrics ?

Sometimes, you would not get the most valuable insights by analysing the data available to you. You often need to create new variables using the existing ones to get meaningful insights.

New variables could be created based on your business understanding or they can be suggested by your clients.

##### Example 1: Restaurant sales

The ‘day of the week’ was a derived variable which was not provided in the original data set (only the date was provided). Using this new variable (day of the week), you can ‘drill down’ to compare the total sales on each day of the week and present the results on the calendar, as shown in figure 1 below.

<figure>
 <img class="full-img" src="../assets/images/restaurant_sales.png" alt="Restaurant Sales">
 <figcaption>Restaurant Sales</figcaption>
</figure>

_There was loss of sales in the counter (PoS:R1) in Wednesdays but there was corresponding increase in the sales in the counter (PoS: R2). When investigated with the restaurant, the person responsible for the counter "PoS: R1" takes the a half day off and he was not replaced by the management and so the customers move to the counter "PoS : R2". However, there is net loss in the profit on Wednesdays due to this._


##### Example 2: Marks Distribution

By plotting the marks against the ‘month of birth’ (derived variable), it was observed that the children who were born after June would have missed the cutoff by a few days and gotten admission at the age of 5. The ones born after June (e.g. July, August, etc) were intellectually and emotionally more mature than their peers because of their higher age, resulting in better performance.

<figure>
 <img class="full-img" src="../assets/images/marks_distribution.png" alt="Marks Distribution">
 <figcaption>Marks Distribution</figcaption>
</figure>


#### Types of Derived Metrics

Broadly, there are three different types of derived metrics:

1. Type-driven metrics
2. Business-driven metrics
3. Data-driven metrics

---

##### Type-Driven Metrics

These metrics can be derived by understanding the variable’s typology. You have already learnt one simple way of classifying variables/attributes — **categorical (ordered, unordered)** and **quantitative** or numeric. Similarly, there are various other ways of classification, one of which is **Steven's typology**.


Steven’s typology classifies variables into four types — nominal, ordinal, interval and ratio __(NOIR , shortform to remember)__:

- **Nominal variables:** Categorical variables, where the categories **differ only by their names**; there is **no order** among categories, e.g. colour (red, blue, green), gender (male, female), department (HR, analytics, sales)
    - These are the most basic form of categorical variables

- **Ordinal variables:** Categories follow a certain **order**, but the **mathematical difference between categories is not meaningful**, e.g. education level (primary school, high school, college), height (high, medium, low), performance (bad, good, excellent), etc.
    - Ordinal variables are nominal as well

- **Interval variables:** Categories follow a certain order, and the **mathematical difference between categories is meaningful** but division or multiplication is not, e.g. temperature in degrees celsius ( the difference between 40 and 30 degrees C is meaningful, but 30 degrees x 40 degrees is not), dates (the difference between two dates is the number of days between them, but 25th May / 5th June is meaningless), etc.
    - Interval variables are **both nominal and ordinal**

- **Ratio variables:** Apart from the mathematical difference, the ratio (division/multiplication) is possible, e.g. sales in dollars ($100 is twice $50), marks of students (50 is half of 100), etc.
    - Ratio variables are **nominal, ordinal and interval type**



Understanding types of variables enables you to derive new metrics of types different from the same column.

For example, age in years is a ratio attribute, but you can convert it into an ordinal type by binning it into categories such as children (< 13 years), teenagers (13-19 years), young adults (20-25 years), etc. This enables you to ask questions, e.g. do teenagers do X better than children, are young adults more likely to do X than the other two types, etc. Here, X is an action you are interested in measuring. 

> **Additional Reading** : [Difference between ordinal, interval and ratio variables](https://www.graphpad.com/support/faqid/1089/){:target:"_blank"}

---

##### Business Metrics

Deriving metrics from the business perspective is not an easy task. It requires a decent domain experience. Without understanding the domain correctly, deriving insights becomes difficult and prone to errors. 

**Examples of metrics derived using Business Understanding:**

1. Student Marks
    - PASS / FAIL
    - CGPA cutoff

2. Banking
    - Number of transactios in a month
    - Minimum Average Balance maintained? Yes / No
    - No. of cards issued equal to target?

3. Cricket
    - Century scored or not?

---

##### Data-Driven Metrics

Data-driven metrics can be created based on the variables present in the existing data set. 

**For example:** if you have two variables in your data set such as "weight" and "height" which shows a high correlation. So, instead of analysing "weight" and "height" variables separately, you can think of deriving a new metric "Body Mass Index (BMI)". Once you get the BMI, you can easily categorise people based on their fitness, e.g. a BMI below 18.5 should be considered as an underweight category, while BMI above 30.0 is considered as obese, by standard norms. This is how data-driven metrics can help you discover hidden patterns out of the data.