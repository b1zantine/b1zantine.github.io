---
layout: section
title: The CRISP-DM Framework
home: pgdmlai-notes
use_math: true
---

Real world Analaytics Problem solving involves multiple steps like data cleaning, preparation, modelling, model evaluation etc. Completing a typical analytics project may take several months, and thus it is important to have a structure for it. 

 
The structure for analytics problem solving is called the **CRISP-DM** framework - **Cross Industry Standard Process for Data Mining**.

It involves a series of steps.
1. [Business Understanding](#business-understanding)
2. [Data Understanding](#understanding-raw-data)
3. [Data Preparation](#data-preparation)
4. [Data Modelling](#data-modelling)
5. [Model Evaluation](#model-evaluation-and-deployment)
6. [Model Deployment](#model-evaluation-and-deployment)

<figure>
 <img class="med-img" src="./CRISP-DM_Process_Diagram.png" alt="CRISP-DM Process Diagram"/>
 <figcaption>CRISP-DM Process Diagram</figcaption>
</figure>

It is important to note that steps in CRISP-DM framework are __not necessarily sequential__ in nature. For example, your data understanding can improve your understanding of business itself. But it all starts with business understanding.

---

## Business Understanding

#### Understanding the Business Goal

It is important that we should be able to articulate the **business objectives** from the broad problem statement so that the next steps in the CRISP-DM framework can be performed effectively.

In summary, to understand the business problem, one has to undertake the following steps of analyzes.

1. Determine the business objectives clearly
2. Determine the goals of data analysis

> **Example:** A retail firm wants to predict weekly sales of a particular store for the next 3 months for 'Men's Wear' category so they can plan their stock better

#### Owning an IPL Team

Let's try to understand what *business understanding* truly means with an example of Indian Premier League.

One of the business problems for IPL team owners is **buying the right players**. Interestingly, **match-winners** are not always the right players, but rather the ones who **helps team owners make money**.

The formula is simple. 

$profits = revenue - cost$

Let's take a look at the components of revenues and costs.

###### Revenue

**Media Rights: 60%**
The cricket board of India, BCCI, collects revenue from broadcasters like Sony and shares a part with the teams. This forms about 60% of the total revenue and teams always get it no matter what players they choose. 

**Sponsorship: 25-30%**
Sponsors pay more when they get higher viewership -which means **star players** and the **ones who entertain** help teams make more money.

**Ticket Sales: 6-8%**
Most of the ticket money goes to team owners.

**Prize Money: 5-10% (if applicable)**
Strangely enough, though, prize money is not a large part of the overall revenue.


Firstly, the business objective is to buy players who help generate revenue, not necessarily the ones who make the most runs. Since one of the largest components of revenue is sponsorships, this will have huge implications on what data you collect and analyse.


##### Costs

**Franchise Fee: 60%**
There’s the cost of owning an IPL team, the money that the team owner pays to the BCCI for the honour of owning a team in the IPL. This cost is fixed and amounts to about 60% of the total cost.

**Player Costs: 30-35%**
This amounts to roughly 30-35% of the total cost and **depends upon the choice of players**.

**Maintenance costs: 5-10%**
This is the cost of running the day-to-day activities, staff salaries etc. This does not depend on the choice of players. 

To sum up, the business objective is to identify low-moderate cost players who can generate high sponsorship revenue. This understanding will significantly change the data, the analysis and the final choice of players. 

---
## Understanding Raw Data

There are four parts to understanding the data.

1. Collect relevant data
2. Describe data
3. Explore data
4. Verify data quality

First we need to collect enough data. Data could be __structured__ or __unstructured__. Next, we need to understand. To achieve that describing the data is important. We can create a **data dictionary** and **summarize** data to understand what type of analysis we can do with the data. To explore the data, we can **create graphs** to understand it visually. Then, the quality of the data needs to be verified so find the __completeness__, __correctness__, __errors__ and __missing values__ in the data.

---
## Data Preparation

This is one of the most crucial steps in Data Anaylsis. Data analysts spend around **50-80% of the time on data cleaning and preparation**.

Usually, data is collected from various sources and can be multiple formats and files. Collating all these data together and select only the required columns and rows based on business understanding is a major step in data preparation. After collating the data, we need to address the missing values and outliers. It is considered the most crucial step because the model will be built on the data sets created here. 

To summarize, the following are the steps involved.
1. Select relevant data
2. Integrate data
3. Clean data
4. Construct data: Derive new features
5. Format data

---
## Data Modelling

It is the heart of data analytics. One can think of a model as a black box which takes relevant data as input and gives an output you are interested in.

Data Modelling in the CRISP-DM framework two tasks.

1. Understand the problem domain and choose the appropriate family of models.
2. From the chosen family of models, select the appropriate algorithm.

---
## Model Evaluation and Deployment

In data analytics, evaluation is when you put everything you have done to litmus tests. If the results obtained from model evaluation are not satisfactory, you __reiterate__ the whole process.

Evaluation is necessary to ensure that your model is robust and effective. Finally, implementation is the natural fruition of a project life-cycle.

Modelling -> Evaluation -> Deployment


---
### Additional Resources 

* https://itsalocke.com/blog/crisp-dm-and-why-you-should-know-about-it/
