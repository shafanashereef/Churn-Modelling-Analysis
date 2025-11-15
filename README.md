# 🏦 **Customer Churn Modelling Analysis**

## 📖 Introduction

Customer churn refers to when customers stop using a company's
services.\
In the banking industry, predicting churn is vital because retaining
existing customers is more cost-effective than acquiring new ones.

This project analyzes a bank's customer dataset to understand the
factors that influence churn and predict which customers are likely to
leave.\
Using demographic, financial, and behavioral data, we aim to identify
key churn drivers, segment customers, and provide insights to improve
customer retention. ion.n.

## Problem Statement

The bank is experiencing customer attrition and wants to understand why
customers are leaving.\
The goal is to identify at-risk customers and the factors contributing
to churn so that effective retention strategies can be developed.

## 🎯 Objectives

1.  **Identify Key Drivers of Customer Churn**\
    Determine the major demographic, financial, and behavioral
    factors---such as age, credit score, balance, and activity
    status---that influence customer attrition.

2.  **Analyze Customer Segments**\
    Examine churn trends across different AgeGroups (Young, Middle-Aged,
    Senior) and RiskLevels (Low, Medium, High) to uncover patterns among
    various customer segments.

3.  **Develop Predictive Models for Churn**\
    Build and evaluate machine learning models to predict the likelihood
    of customer churn and assess model performance for accuracy and
    reliability.

4.  **Provide Actionable Business Insights**\
    Generate data-driven recommendations to help the company improve
    customer retention, focusing on high-risk and inactive customer
    groups.

## 🧾 Data Description

The dataset contains information about 10,000 bank customers and is used
to predict customer churn --- whether a customer leaves the bank
(`Exited = 1`) or stays (`Exited = 0`).

### **Features Overview**

  -----------------------------------------------------------------------
  Column                        Description
  ----------------------------- -----------------------------------------
  **RowNumber**                 Record index (not analytically relevant).

  **CustomerId**                Unique identifier for each customer.

  **Surname**                   Customer's last name.

  **CreditScore**               Numerical score representing the
                                customer's creditworthiness.

  **Geography**                 Country where the customer resides.

  **Gender**                    Gender of the customer.

  **Age**                       Age of the customer in years.

  **Tenure**                    Number of years the customer has been
                                with the bank.

  **Balance**                   Account balance (converted from float to
                                int).

  **NumOfProducts**             Number of bank products the customer
                                holds.

  **HasCrCard**                 1 if the customer has a credit card,
                                otherwise 0.

  **IsActiveMember**            1 if the customer is active, otherwise 0.

  **EstimatedSalary**           Estimated annual salary of the customer.

  **Exited**                    Target variable --- 1 if the customer
                                exited, 0 otherwise.
  -----------------------------------------------------------------------

### Import Libraries & Load Data

### Information of Dataset

-   Columns = 14
-   Rows = 10000
-   Data types
    -   float = 2
    -   int64 = 9
    -   object = 3

### Data Cleaning & Feature Engineering

#### Checking duplicates

##### No duplicated values

#### Checking null values

##### No null values

#### Convert datatypes

#### Add Columns

### Exploratory Data Analysis (EDA)

### Objective 1: Identify Key Drivers of Customer Churn

### 1. Churn Distribution

Shows the proportion of customers who stayed vs. exited --- helps
understand churn imbalance.

## Interpretation

-   The chart shows a **strong imbalance**: most customers **stay
    (\~8000)**, while a smaller group **churns (\~2000)**.
-   This means the churn rate is roughly **20--25%**, which is
    significant for business impact.
-   The imbalance will affect modeling, so techniques like **class
    weighting or resampling** will be needed.

### 2. Churn Rate by Gender

Helps determine whether gender influences churn likelihood.

## Interpretation

-   **Females show a higher churn rate (\~25%)** compared to
-   **Males (\~18%)**.

This suggests **gender does have some influence on churn**, with women
leaving at a slightly higher rate.

### 3. Churn Rate by Geography

Analyzes regional impact on churn behavior.

## Interpretation

-   **Germany has the highest churn rate (\~32%)**, significantly above
    the other regions.
-   **Spain shows a moderate churn rate (\~17%)**.
-   **France has the lowest churn rate (\~15%)**.

This indicates that **geography strongly influences churn**, with German
customers being far more likely to leave.

### 4. Age vs. Churn

Older customers may show different churn tendencies --- visualize using
boxplot.

## Interpretation

**Older customers are more likely to churn**. The boxplot shows that the
**median and overall age** of customers who exited is **higher** than
those who stayed. Non-churners tend to be younger, while churners are
concentrated in older age ranges. Outliers exist in both groups but
don't change the trend.

### 5. Credit Score vs. Churn

Check if low credit score customers churn more often.

## Interpretation

Credit scores look very similar between customers who stayed and those
who exited. There's **no strong difference** in median score or spread,
suggesting that **credit score does not significantly influence churn**
in this dataset.

### 6. Balance vs. Churn

Understand whether customers with higher/lower balances are more likely
to churn.

## Interpretation

Customers who churn tend to have **higher account balances** than those
who remain. The churn group's median and overall distribution are
shifted upward, suggesting that **higher-balance customers are more
likely to exit** in this dataset.

### 7. Activity and Credit Card Status vs. Churn

Compare churn rates based on membership activity and credit card
ownership.

## Interpretation

### Churn by Active Membership

-   Non-active members have a **much higher churn rate** than active
    members.
-   **Active membership strongly reduces churn**, suggesting engagement
    is key to retention.

### Churn by Credit Card Ownership

-   Customers without a credit card churn **slightly more** than those
    who have one.
-   The effect is **small**, meaning credit card ownership is not a
    strong churn predictor.

### 8. Correlation Heatmap (Numerical Variables)

Identify which numeric variables have stronger relationships with churn.

## Interpretation

-   **Age (0.29)** has the strongest positive correlation with churn ---
    older customers are more likely to leave.
-   **IsActiveMember (-0.37)** has the strongest negative correlation
    --- active members churn far less.
-   **Balance (\~0.12)**, **NumOfProducts (-0.32)**, and **Tenure
    (-0.01)** show weak to moderate relationships.
-   **CreditScore**, **HasCrCard**, and **EstimatedSalary** have
    **almost no correlation** with churn.

### Bottom Line

The most influential numeric features related to churn are:

-   #### IsActiveMember (strong negative)

-   #### Age (moderate positive)

-   #### NumOfProducts (moderate negative)

Most other numerical variables show minimal relationship to churn.

## Overall Findings: Key Drivers of Customer Churn

-   **Customer Activity**: Inactive customers are much more likely to
    churn (strong negative correlation \~--0.37). Engagement is the
    strongest predictor of attrition.
-   **Age**: Older customers churn more often (positive correlation
    \~0.29).
-   **Geography**: Churn varies by region---highest in Germany(\~32%),
    moderate in Spain(\~17%), lowest in France(\~15%).
-   **Number of Products**: Customers with fewer products are more
    likely to leave (negative correlation \~--0.32).
-   **Account Balance**: Higher balances are associated with slightly
    higher churn (moderate positive correlation \~0.12).
-   **Gender**: Females churn slightly more (25% vs. 18% for males), but
    the overall effect is small.
-   **Credit Card Ownership**: Non-credit-card holders churn slightly
    more; minimal impact.
-   **Other Variables**: Credit score, estimated salary, and tenure show
    little to no correlation with churn and are not significant drivers.

### Objective 2: Analyze Customer Segments

Goal: Examine churn patterns across customer groups defined by AgeGroup
(Young, Middle-Aged, Senior) and RiskLevel (Low, Medium, High).

These visualizations will help you understand which segments are more
prone to churn, providing insights for targeted retention strategies.

### 1. Churn Rate by Age Group

Shows how churn varies across customer age categories.

## Interpretation

-   **Young customers** churn the least --- their churn rate is very
    low.
-   **Middle-aged customers** churn more than young customers.
-   **Seniors** have the **highest churn rate**, slightly above the
    middle-aged group.

### 2. Churn Rate by Risk Level

Visualizes the impact of CreditScore-based RiskLevel on churn.

## Interpretation

-   **Low-risk customers churn the most**, slightly above 0.22.
-   **Medium-risk customers** are close behind, around 0.21.
-   **High-risk customers churn the least**, around 0.20.

This is counterintuitive: high-risk customers usually churn more, but
here they may have **fewer alternatives** and remain with the company,
while low-risk customers can more easily switch to another provider.

Overall, **credit risk level is not a strong standalone predictor of
churn**.

### 3. Combined Analysis: Age Group vs. Risk Level

Helps identify the most vulnerable customer segments by both AgeGroup
and RiskLevel.

## Interpretation: Churn by Age Group × Risk Level

-   **Young customers** have the **lowest churn**, regardless of risk
    level.
-   **Middle-aged customers** show **higher churn**, with Low and Medium
    risk slightly higher than High risk.
-   **Seniors have the highest churn overall**, especially in the
    **Low-risk** group.

### 4. Age Group vs. Active Membership

Examines how activity status varies within each age group and how it
affects churn.

## Interpretation: Churn by Age Group × Active Membership

-   **Active members (1)** consistently churn **far less** than inactive
    members (0) across all age groups.
-   **Inactive seniors** have by far the **highest churn rate (≈0.8)**
    --- the most vulnerable segment.
-   **Inactive middle-aged customers** also show high churn, while
    active middle-aged customers churn moderately.
-   **Young customers** churn the least overall, especially those who
    are active.

### 5. Cross-tab Visualization: AgeGroup vs. Geography

Check if certain regions and age groups have higher churn rates.

## Interpretation

**Germany has the highest churn rates across all age groups, especially
among Seniors**. **Spain has the lowest churn overall**, with the Young
group showing the best retention. **Seniors consistently churn the most
in every country**, while **Young customers churn the least**. France
sits in the middle with moderate churn levels.

### 6. Count of Customers by Segment

Gives an overview of the number of customers in each AgeGroup and
RiskLevel for context.

## Interpretation

### Customer Distribution by Age Group:

-   Most customers are **Middle-Aged**, followed by **Young**.
-   **Seniors make up a tiny portion** of the customer base.

### Customer Distribution by Risk Level:

-   The **High-risk segment is the largest**, far exceeding Medium and
    Low.
-   **Medium-risk** customers form a mid-sized group.
-   **Low-risk** customers are the fewest.

## Overall Findings: Churn Analysis Across Customer Segments

-   Young customers churn the least; seniors churn the most, with
    middle-aged customers in between.
-   Low-risk customers churn slightly more than medium- and high-risk
    customers, making risk level a weak predictor.
-   Young customers show low churn across all risk levels; seniors show
    the highest churn, especially in the low-risk group.
-   Active customers churn far less across every age group; inactive
    seniors have the highest churn (\~0.8).
-   Germany has the highest churn in all age groups, Spain the lowest;
    seniors churn the most in every region.
-   Most customers are middle-aged; seniors are the smallest group.
    High-risk customers form the largest risk segment.

### Objective 3: Develop Predictive Insights for Churn

Goal: Understand which customer attributes (e.g., Age, Balance,
CreditScore, Activity, etc.) are most associated with churn behavior.

### 1. Correlation Heatmap

Shows how strongly numerical features are related to churn.

## Interpretation

-   **Age** has the strongest positive correlation with churn --- older
    customers churn more.
-   **Number of Products** has the strongest negative correlation ---
    customers with more products churn less.
-   **Balance** shows a small negative correlation --- higher balances
    slightly reduce churn.
-   **IsActiveMember** has a weak negative correlation --- active
    members churn less.
-   Other variables (CreditScore, Tenure, EstimatedSalary) show **very
    weak or no correlation** with churn.

### 2. Average Feature Comparison by Churn Status

Compare average values of key features for churned vs. retained
customers.

## Interpretion

Customers who **churned (Exited = 1)** tend to be **older**, have a
**slightly lower credit score**, hold **fewer products**, and have a
**higher average balance** compared to those who stayed. Their
**estimated salary is also slightly higher**, but the difference is
small.

### 3. Active vs. Inactive Members --- Churn Rate

Examine how customer activity impacts churn.

## Interpretation

The chart shows that inactive members have a higher churn rate than
active members. **Inactive members** (red bar) are taller, indicating a
**greater proportion of them exit**. **Active members** (blue bar) have
a **lower churn rate**, suggesting they are more likely to remain.

### 4. Number of Products vs. Churn

Customers with too few or too many products may churn differently.

## Interpretation:

-   The **proportion of customers who exited** (churned) is highest for
    those with **4 products**, represented by the red bar.
-   Customers with **1 or 2 products** have a lower churn rate, as seen
    in the blue bars.
-   This suggests that having more products is linked to a higher churn
    rate, while fewer products might be associated with lower churn.

### 5. Balance vs. Churn

Visualize how account balance differs between churned and retained
customers.

## Interpretation:

-   **Customers who stayed** have a wider spread, indicating that
    customers who remained have a more varied account balance.
-   **Churned or exited customers** are smaller and skewed toward higher
    balances, suggesting that customers with higher balances are more
    likely to leave.
-   There is a significant difference in the **median balances**, with
    those who churned having higher balances on average compared to
    those who stayed.

### 6. Age vs. Churn

Understand how churn varies with customer age.

## Interpretation

-   **Churned customers** (red) peak in their 30s.
-   **Stayed customers** (blue) are more common in the 40s and 50s.

### 7. Geography vs. Churn

Analyze which regions have higher churn tendencies.

## Interpretation

The bar chart shows churn rates across three countries: \* **Germany has
the highest churn rate** --- noticeably higher than the others. \*
**France and Spain have lower churn rates**, with France being the
lowest.

## Overall Findings: Predictive Insights for Churn

-   Older customers are more likely to churn, while customers in their
    40s and 50s tend to stay.
-   Inactive customers have a much higher churn rate than active
    customers.
-   Customers with fewer products churn less, while those with many
    products (especially 4) churn the most.
-   Customers who churn usually have higher account balances than those
    who stay.
-   Credit score, salary, and tenure show very weak or no relationship
    with churn.
-   Germany has the highest churn rate, while France and Spain show
    lower churn.
-   Overall, churned customers tend to be older, less active, have fewer
    commonly used products, and hold higher balances.

### Objective 4: Provide Actionable Business Insights

Goal: Translate analytical findings into meaningful business
recommendations to help reduce customer churn and improve retention.

### 1. Overall Churn Overview

First, visualize the churn percentage across the dataset to set context.

## Interpretation:

The chart shows the overall customer churn rate:

-   **About 20.37%** of customers have **exited**.
-   The majority (\~80%) **stayed**.
-   The bar plot reflects this imbalance clearly: far more customers
    remained than churned.

### 2. Age Group and Risk Level --- Churn Insights

Target churn-prone segments based on customer demographics and risk.

## Interpretation

-   **Churn increases with age**: Seniors have the **highest churn
    rates**, Middle-Aged are moderate, and Young customers churn the
    least.
-   **Risk level matters**: Across all age groups, **High-risk customers
    churn most**, followed by Medium, then Low.
-   **Biggest concern**: **High-risk Seniors** show the highest churn
    overall --- key target for retention efforts.
-   **Most stable group**: **Low-risk Young** customers have the lowest
    churn rates.

### 3. Activity Level and Churn

Customer engagement (activity) is often a strong churn driver.

## Interpretation

-   **Inactive members (0)** churn at a **much higher rate**, close to
    **30%**.
-   **Active members (1)** churn significantly less, around **15%**.
-   **Key insight**: Being an active member is strongly associated with
    **lower churn**, indicating that engagement is a major retention
    driver.

### 4. Number of Products and Churn

Helps understand if product diversification influences churn.

## Interpretation

-   **Churn increases with the number of products**: Customers with **1
    product** have the **lowest churn rate**, around **10%**.
-   **Churn is highest for customers with 4 products**, peaking at
    around **45%**.
-   **Key insight**: While diversification (owning more products) might
    seem beneficial, it actually correlates with **higher churn**. This
    suggests that more products may indicate a customer at risk of
    leaving.

### 5. Balance and CreditScore -- Financial Behavior

Link financial stability to churn likelihood.

## Interpretation

**The plot shows no clear relationship between credit score and account
balance, and churners appear across all ranges of both variables**.
Churn and non-churn customers are widely mixed, meaning **neither credit
score nor balance alone is a strong predictor of churn**.

### 6. Visual Summary (Dashboard View)

Combine key churn drivers visually.

## Interpretation

### Churn by Age Group:

Older customers have the highest churn rate, while younger customers
have a significantly lower churn rate.

### Churn by Risk Level:

Medium- and high-risk customers tend to churn more frequently than
low-risk customers.

### Churn by Activity:

Inactive customers churn at a much higher rate than active customers.

### Churn by Product Count:

Customers with only **1 product** are the most likely to churn, while
those with **multiple products** are less likely to churn, suggesting
that higher engagement reduces churn.

## Overall Findings: Provide Actionable Business Insights

-   Churn affects about 20% of customers, meaning most customers stay
    but a significant minority leave.
-   Older customers churn more than younger ones; seniors are the most
    vulnerable segment.
-   High-risk seniors show the highest churn rates and should be top
    priority for retention efforts.
-   Inactive customers churn at nearly double the rate of active
    customers, making engagement a key churn driver.
-   Customers with only 1 product have the lowest churn, while customers
    with many products---especially 4---have the highest churn.
-   Credit score and balance show no clear pattern with churn and are
    weak predictors on their own.
-   Younger, low-risk, and active customers are the most stable and
    least likely to churn.

## 📊 Overall Findings

### 1. Identify Key Drivers of Customer Churn

-   Inactivity is the strongest predictor of churn.
-   Older customers are more likely to churn than younger ones.
-   Customers with fewer products churn more; product count shows a
    strong impact.
-   Higher account balances are slightly linked to higher churn.
-   Geography matters: highest churn in Germany, lowest in France and
    Spain.
-   Gender, credit card ownership, credit score, salary, and tenure have
    little or no effect on churn.

### 2. Analyze Customer Segments (AgeGroup & RiskLevel)

-   Young customers churn the least; seniors churn the most.
-   Risk level is weak as a predictor, but low-risk groups sometimes
    show slightly higher churn.
-   Senior low-risk customers have especially high churn.
-   Inactive seniors have extremely high churn (\~0.8).
-   Germany shows the highest churn across all age groups; Spain shows
    the lowest.
-   Middle-aged customers form the largest group; seniors are the
    smallest.

### 3. Develop Predictive Models for Churn

-   Models confirm key patterns: age, activity level, product count, and
    balance are important predictors.
-   Customers who churn tend to be older, inactive, and have fewer core
    products.
-   Customers with high balances appear more likely to churn.
-   Credit score, salary, and tenure remain weak predictors.
-   Germany consistently appears as a high-risk geography for churn.

### 4. Provide Actionable Business Insights

-   About 20% of customers churn, showing a clear retention opportunity.
-   Seniors and high-risk seniors are the most vulnerable segments and
    need targeted strategies.
-   Inactive customers should be prioritized for re-engagement programs.
-   Customers with very few or too many products need monitoring, as
    both ends show higher churn risk.
-   Younger, low-risk, and active customers are the most stable and
    lowest churn segment.

## 📌 Recommendations

### 1. Recommendations for Identifying Key Drivers of Churn

-   Prioritize customer activity tracking and implement alerts for
    inactive accounts.
-   Introduce age-targeted retention programs, especially for senior
    customers.
-   Focus on Germany-specific retention campaigns due to consistently
    high churn.
-   Encourage customers to adopt additional products, but monitor
    customers with very high product counts.
-   Provide special attention to high-balance customers, as they show a
    slightly higher churn tendency.
-   De-prioritize credit score, salary, tenure, and gender in churn
    models --- they do not meaningfully drive churn.

### 2. Recommendations for Customer Segment Analysis (AgeGroup & RiskLevel)

-   Build dedicated retention strategies for seniors, especially
    high-risk and inactive seniors.
-   Maintain engagement strategies for middle-aged customers, as they
    form the largest segment.
-   Strengthen loyalty programs for high-risk groups, but avoid relying
    heavily on risk level alone.
-   For regions:
    -   Germany: Deploy aggressive retention initiatives.
    -   France & Spain: Maintain current strategies but monitor senior
        segments.
-   Target inactive customers across all age groups with reactivation
    campaigns.

### 3. Recommendations for Predictive Modeling

-   Use activity status, age, geography, balance, and number of products
    as core features in predictive models.
-   Train models with interaction terms (e.g., age × activity, geography
    × products) to better detect high-risk subgroups.
-   Implement churn prediction scoring to identify customers who need
    intervention early.
-   Refresh models regularly using new customer behavior data to
    maintain accuracy.
-   Use model outputs to segment customers into high, medium, and low
    churn-risk tiers for targeted actions.

### 4. Recommendations for Actionable Business Insights

-   Build tailored retention plans for high-risk seniors and inactive
    customers, the most vulnerable segments.
-   Launch re-engagement campaigns (emails, offers, personalized
    outreach) for inactive customers.
-   Encourage product adoption strategically (e.g., bundles), while
    monitoring customers holding 4+ products for dissatisfaction.
-   Provide concierge or premium support for high-balance customers.
-   Improve customer experience and loyalty programs in Germany, where
    churn is highest.
-   Maintain and strengthen loyalty initiatives for younger, active, and
    low-risk customers, who are most stable.

## 🎯 Final Overall Insight

-   Churn is mainly driven by **low engagement**, **age**, and **product
    usage patterns**.
-   **Inactive customers**, especially seniors, have the highest churn
    risk.
-   Geography influences churn, with **Germany** consistently showing
    the highest rates.
-   Customers with **very few** or **very many products** are more
    likely to churn.
-   **Credit score**, **salary**, and **tenure** have little meaningful
    impact on churn.
-   Churned customers are typically **older**, **less active**, and tend
    to have **higher account balances**.
-   Retention efforts should focus on **inactive**, **senior**, and
    **high-balance** customers for the greatest impact.

## 🎯 Final Actionable Insight

-   Prioritize re-engagement of **inactive customers**, as inactivity is
    the strongest churn driver.
-   Focus retention efforts on **senior customers**, who consistently
    show the highest churn.
-   Pay special attention to **high-risk seniors** and **inactive
    seniors**, the most vulnerable segment.
-   Strengthen retention strategies in **Germany**, the region with the
    highest churn rates.
-   Encourage balanced **product usage** and monitor customers with
    **very high product counts** (e.g., 4 products), who show higher
    churn.
-   Provide personalized support to **high-balance customers**, who have
    a higher tendency to churn.
-   Continue nurturing **young**, **active**, and **low-risk
    customers**, who are the most stable group.
