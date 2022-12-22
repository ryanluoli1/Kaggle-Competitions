# American Express - Default Prediction

Link: https://www.kaggle.com/competitions/amex-default-prediction


## Achievements

1. Silver Medal
2. Ranked Top 2%


## Introduction

The goal of this competition is to **predict credit defualt** based on **time-series behavioral data** and **anonymized customer profile information**. Credit default prediction allows lenders to **optimize lending decisions**, which leads to a better customer experience and sound business economics. 


## Task and Evaluation

For **each customer_ID** in the test set, we are asked to predict a **probability** that the customer will end up with credit default.

The predictions are evaluated using a **metric $M$** which is the **mean of 2 measures** of rank ordering:

$$M = 0.5×(G+D)$$

1. **Normalized Gini Coefficient** (G):  $G = 2 × AUC - 1$, $max(G)=1$ and $min(G)=-1$
2. **Default Rate captured at 4%** (D): percentage of the positive labels captured within the highest-ranked 4% of the predictions, represents a sensitivity/recall statistic

The overall metric $M$ has a **maximum of 1** and we aim to achieve a value **as high as possible**.

Note: **negative samples** are given a weight of 20 to adjust for **downsampling**.


## Data Overview

The **training set** consists of 11.4m samples (behavioural data) for 920k unique customers. The **test set** consists of 5.53m samples for 460k unique customers. 

The **dimension** of the datasets is 190 and all the features are **anonymized** and normalized. The **target variable** is binary where **y=1** represents a default outcome. (A customer is considered to be **default** if he/she does not pay due amount within 120 days after the last statemnet date.)

Within the 460k unique customers in the **training set**, we have 340k non-default customers and 119k default customers, leanding to a **default rate** of approximately 26%. Note: the **non-default** customers were **subsampled** for balancing the data (the actual default rate is around 1.7%).

The **features** are monthly customer profile data:

- **13 continuous time-series entris** of behavioural data for each customer
- **D Variables**: Delinquency 
- **S Variables**: Spend
- **P Variables**: Payment 
- **B Variables**: Balance
- **R Variables**: Risk 

However, we notice the following:

- around **20%** of the customers in the training set have **less than 13 entries** of behavioural data (might be **new customers**)
- the **last entry** in the training has date 2018.03 but the last entry in the test set has date 2019.04 (they are **not fully overlapped**)
- many features are **sparse**


## Feature Engineering Strategies

