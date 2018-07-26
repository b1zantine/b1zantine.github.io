---
layout: section
title: Segmented Univariate Analysis
home: pgdmlai-notes
---

In the segmented univariate analysis, useful insights are extracted by conducting univariate analysis on segments on data.Though the simple univariate analysis is tremendously useful in many cases, the real strength of univariate analysis often lies in segmented univariate analysis.

Segmented univariate analysis allows you to compare subsets of data, which is a powerful technique because it helps you understand how a relevant metric varies across different segments.

The way we approach this is by to figure out how to segment/group the variable into smaller buckets that we can compare.

> [Mashable](https://mashable.com){:target="_blank"} Posts Data :  [__Download__](../assets/data/mashable-posts.csv)

In the mashable posts data, some of the ways segmented univariate analysis that could be done is as follows.

1. On average, a higher number of articles are shared on weekdays than weekends

2. Among the weekdays, articles published on Wednesdays get shared more than on any other weekday

3. Articles of the type (or channel) 'lifestyle' and 'social media' are shared more than the other types on average

In this case, the categorical variables used for grouping were ‘channel type’, ‘day of week’, etc.  Across these categories or groups, you had then conducted segmented univariate analysis to compare the average number of shares across days, channel types etc.


#### Basis of Segmentation

The entire segmentation process can be divided into four parts:

1. Take raw data
2. Group by dimensions
3. Summarise using a relevant metric such as mean, median, etc.
4. Compare the aggregated metric across groups/categories


But what if you have a large number of variables in your dataset. It looks very repetitive task to perform the same analysis on the large bunch of variables. One way of solving this problem is to make a table with the categorical variables on one axis and the numeric variables (or measures/facts) on the other.


<mark>Checkout this analysis based on National Achievement Survey</mark> : [Student Performance Drivers](https://gramener.com/nas/){:target="_blank"}.



#### Comparison of Averages

**One should be careful while comparing averages, especially if the difference in average values is small.** This difference could be bacause of randomness.


**For example:** Consider that the difference in the average marks of boys and girls is approximately __0.2__, which is quite small. There can be two possibilities:

1. The difference is due to randomness and gender does not actually influence the average marks at all.
2. The gender of a student causes a small difference in the average marks.

How do you determine if the difference is not due to randomness?


Now, consider the following dataset of student marks (6 boys and 6 girls) where every girl scored 1 mark higher than every boy in the class. There is no confusion if the girls scored higher than boys are not.

| Boy | Girl |
| --- | ---- |
| 60  | 61   |
| 60  | 61   |
| 60  | 61   |
| 60  | 61   |
| 60  | 61   |
| 60  | 61   |
| ========== |
| **Average = 60** | **Average = 61** |


On the other hand, consider the following distribution.

| Boy | Girl |
| --- | ---- |
| 40  | 41   |
| 45  | 46   |
| 50  | 51   |
| 55  | 56   |
| 60  | 61   |
| 65  | 66   |
| ========== |
| **Average = 52.5** | **Average = 53.5** |

In this case, the boys are scoring anywhere between 40 - 65 and the girls are scoring anywhere between 41 - 66. Since the ranges are so similar, we cannot confidently say that girls score higher than boys. There is nothing significant enough to prove it.


> “Don’t blindly believe in the averages of the buckets — you need to observe the distribution of each bucket closely and ask yourself if the difference in means is significant enough to draw a conclusion. If the difference in means is small, you may not be able to draw inferences. In such cases, a technique called **hypothesis testing** is used to ascertain whether the difference in means is significant or due to randomness.“


#### Comparison of Other Metrics

Once the variables are identified based on the business problem for analysing the segments, the next step is to know the distribution of segments and compare the average of each segment. But this is not the only way of comparing segments. There are various metrics which you can use to understand and explain your data easily.

