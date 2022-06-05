# Case Study Final

## Introduction

Business Problem: Payment defaults are detrimental to the business and are a significant cost factor. 

Therefore, there need to be ways and signals for creditors to reduce risk and avoid default-prone customers. This case study shows exploratory data analysis that seeks trends and movements to determine default-prone customers. A further machine learning section aims to analyze and ultimately predict future customers on whether they are default-prone.

## Limitations

Analysis and prediction will mostly be made on clients rather than entities and contracts. There are confounding factors that might affect the accuracy of the analysis, insight, and prediction due to unknown information about the entities and contracts.

1. We do not know about the entities' other liabilities, cash on hand, or revenue. As a result, entities with other liabilities or an already declining business could be heavily affected by problem such as loan acceleration, leading to heavy losses for the creditors.
2. Is the loan secured or unsecured? Is the loan short-term or long-term? Behavior and probability of default for entities could change as a result of whether collateral is at stake. As well as the length of the contract, the date range of the date does not allow us to extract this information.
3. What market sector? Energy and transportation stands as two of the highest global corporate default rates. Knowing and accounting for volatility of a market sector is very important

Knowing these factors does not guarantee improvement in accuracy. However, confluence of factors allows possible further questioning, exploration and analysis for improvement of accuracy of our model.

## Exploratory Data Analysis

Initial analysis revealed that there are a total of 1281 unique clients and 1287 unique entity. [591, 165, 1262, 797, 473] has more than one company where 591 has three. 

### Percentage of Companies with Default History

![Untitled](Case%20Study%20Final%20e1e682c11e6b44ceba95e27f88d0f0de/Untitled.png)

### Effects of Total Liability of a Client to Default

In this section, we want to know whether or not the total amount of what the client has to pay back, regardless of the number of companies they have, affects whether or not they will default.

![Untitled](Case%20Study%20Final%20e1e682c11e6b44ceba95e27f88d0f0de/Untitled%201.png)

                                                                                                  *Boxplot of outlier removed data*

Within the time frame of the date. The liability distribution between entities that defaulted and paid back all their loans did not differ. Thus, the amount of liability does not affect the default rate.

A further logistic regression is ran on the extracted data.

![Untitled](Case%20Study%20Final%20e1e682c11e6b44ceba95e27f88d0f0de/Untitled%202.png)

This shows there are no predictability of liability on default rate on its own. 

However analysis done on data with outliers with a robust scaler shows otherwise

![Untitled](Case%20Study%20Final%20e1e682c11e6b44ceba95e27f88d0f0de/Untitled%203.png)

It is obvious that two points are outliers that are heavily effecting the regression. It is hard to really call the outlier values for default really outliers in this case as it could truly represent the distribution.

Note: These logistic regression are just checks and have not been optimised at all.

### Default Rate by Entity Type

In this section we want to know if a certain entity is much more likely to default than another.

![Untitled](Case%20Study%20Final%20e1e682c11e6b44ceba95e27f88d0f0de/Untitled%204.png)

### Default Percentage of Entities

![Untitled](Case%20Study%20Final%20e1e682c11e6b44ceba95e27f88d0f0de/Untitled%205.png)

![Untitled](Case%20Study%20Final%20e1e682c11e6b44ceba95e27f88d0f0de/Untitled%206.png)

One of the key problem with the diagram is that even though hybrid trust has a 100% default rate, any hard conclusion on this result and any entity with low sample size need to be taken with a grain of salt since there are only one hybrid trust in the whole dataset. 

### Amount of Each Default Entities

A natural question to ask after the previous result is “who are the largest contributors to defaulting?”

![Untitled](Case%20Study%20Final%20e1e682c11e6b44ceba95e27f88d0f0de/Untitled%207.png)

Of all the entities that has defaulted at least once (368). Australia private companies makes up the largest at 53.5% (197) and individual/sole trader makes up the second largest at 40.8% (150).

Amount being defaulted

![Untitled](Case%20Study%20Final%20e1e682c11e6b44ceba95e27f88d0f0de/Untitled%208.png)

Even though there is only a 10% difference between the number of defaulting Australian private company compare to individual/sole trader. The total amount that Australian private company has defaulted is a total of $7,837,580.09 while  individual/sole trader has defaulted $2,394,188.19. 

This result further the need for data on entities and their contract type in order to target Australian private companies and individual/sole trader since they make up the majority of the business’s customer base as well as the highest default in terms of dollar amount. 

### Rank of Australian Private Companies in Amounts that Defaulted

![Untitled](Case%20Study%20Final%20e1e682c11e6b44ceba95e27f88d0f0de/Untitled%209.png)

![Untitled](Case%20Study%20Final%20e1e682c11e6b44ceba95e27f88d0f0de/Untitled%2010.png)

![Untitled](Case%20Study%20Final%20e1e682c11e6b44ceba95e27f88d0f0de/Untitled%2011.png)

Entities established in 2000, 2014, 2015 seems to have the highest default amount 

### Individual/Sole Trader that Defaulted

![Untitled](Case%20Study%20Final%20e1e682c11e6b44ceba95e27f88d0f0de/Untitled%2012.png)

![Untitled](Case%20Study%20Final%20e1e682c11e6b44ceba95e27f88d0f0de/Untitled%2013.png)

![Untitled](Case%20Study%20Final%20e1e682c11e6b44ceba95e27f88d0f0de/Untitled%2014.png)

The same story can be said for individuals/sole trader with slight deviation in rank.

### Default Rate by Year

Further analysis on the year that the entity is established is needed in order to properly interpret previous results. 

![Untitled](Case%20Study%20Final%20e1e682c11e6b44ceba95e27f88d0f0de/Untitled%2015.png)

A simple count plot reveals that 2000, 2014, 2015 has the highest default numbers, this explains why we see the most default amount by these years. 

Default Rate by Year

![Untitled](Case%20Study%20Final%20e1e682c11e6b44ceba95e27f88d0f0de/Untitled%2016.png)

Default Amount by Year

![Untitled](Case%20Study%20Final%20e1e682c11e6b44ceba95e27f88d0f0de/Untitled%2017.png)

![Untitled](Case%20Study%20Final%20e1e682c11e6b44ceba95e27f88d0f0de/Untitled%2018.png)

### Effects of Payment Intervals

In this part, we want to answer whether irregular payment interval affects whether a client defaults or not. Irregular payment could be due to many reasons, such as late repayment or overdrafts that result in short interval repayments for high-interest loans first rather than a stable monthly or bi-weekly loan payment. However, it is hard to tell why there might be a difference without sufficient data.

![Untitled](Case%20Study%20Final%20e1e682c11e6b44ceba95e27f88d0f0de/Untitled%2019.png)

There is a clear difference between clients who have defaulted or not. In the case of default-prone clients, their payment interval is 15.743822 days on average. At the same time, clients who have not defaulted makes interval payment every 22.447979 days on average.

## Modeling

### Feature Engineering

Data

- There are a total of 1281 rows matching the 1281 unique client ids.
- Both `entity_type` and `entity_year_established` these variable have been ordinal encoded.
    - For clients with two of the same company (eg. Australian Public Company) column value will show up as 2
    - This is the same for client’s company’s established year
- `avg_txn_interval` average payment intervals for each client regardless of contract and company.
- `payment_amt` total amount of payment and defaults for a client.
- `payment_code` Initially DEFAULT = False has now been encoded to DEFAULT = False = 1. Where defaulting is our primary class while 0 means client has not default once.

### Train test split

Training and test set was split on a stratified split. This means the ratio of default and payment customers stays the same for training and testing sets.

![Untitled](Case%20Study%20Final%20e1e682c11e6b44ceba95e27f88d0f0de/Untitled%2020.png)

![Untitled](Case%20Study%20Final%20e1e682c11e6b44ceba95e27f88d0f0de/Untitled%2021.png)

### Method for Prediction Models

1. Determine parameter that needs tuning for optimisation
2. Run randomized search using stratified 5 fold cross validation in order to find the best parameters for our model
3. Test on unseen testing data set to see the results

### Decision Tree

### Feature Importance

Decision classifier placed `avg_txn_interval` with 78% importance in predicating whether some has defaulted or not. 

![Untitled](Case%20Study%20Final%20e1e682c11e6b44ceba95e27f88d0f0de/Untitled%2022.png)

### Classification Report

When running 5 instance on the test set decision tree classifier is able to achieve average of 46.1% recall rate 

![Untitled](Case%20Study%20Final%20e1e682c11e6b44ceba95e27f88d0f0de/Untitled%2023.png)

On a good run it was able to achieve as high as 73% 

![Untitled](Case%20Study%20Final%20e1e682c11e6b44ceba95e27f88d0f0de/Untitled%2024.png)

Decision tree performance very poorly when it comes to general detecting of default clients. Recall scores are varying on difference runs. 

### Random Forest

### Feature Importance

![Untitled](Case%20Study%20Final%20e1e682c11e6b44ceba95e27f88d0f0de/Untitled%2025.png)

### Classification Report

![Untitled](Case%20Study%20Final%20e1e682c11e6b44ceba95e27f88d0f0de/Untitled%2026.png)

Random forest performed a lot better with overall accuracy of 82% and a very stable recall score over different runs of 57%.

### XGBoost

### Feature Importance

![Untitled](Case%20Study%20Final%20e1e682c11e6b44ceba95e27f88d0f0de/Untitled%2027.png)

### Classification Report

![Untitled](Case%20Study%20Final%20e1e682c11e6b44ceba95e27f88d0f0de/Untitled%2028.png)

XGBoost produced far better improvement of a stable 81% accuracy and especially 95.6% recall on defaults. 

## Conclusion

The key takeaway from that analysis is that most default clients are private companies and individual/sole traders. In addition, average transaction interval is a crucial determinate of default and shows apparent effects on default rates of clients.

The best model in the modeling section can achieve a default recall rate of 95.6%; the trade-off is that the default precision is 76%, leading to possible clients who pay back all their loans being classified as default-prone.

The business impact of turning away possible good clients would need to be solved through optimization and clear business objective. For example, do we want to reduce risk? Or do we want to maximize revenue? Thus, there requires further questioning and analysis for even better decisions.

## Improvements

- Interactive dashboard
- For imbalance class we could try SMOTE to oversample
- Better feature engineering for contract e.g. whether two contracts overlap or not. For the same company or different company of the client
