# Trojan Horse Fashion Subscription Service - Predictive Modeling Using Logistic Regression

## Business Context

**Trojan Horse** is a fictional personalized fashion service for men, offering high-end fashion accessories through a subscription model. Similar to services like Trunk Club, BirchBox, and StitchFix, Trojan Horse delivers curated fashion items to its members each month. The goal is to offer convenience by selecting items that match the individual style preferences of each customer.

However, Trojan Horse currently faces challenges with selecting potential buyers in its marketing strategy, where the company selects 50,000 customers from a 500,000-member base to ship each month, based solely on past purchase history within specific style categories. Unfortunately, if the products are randomly mailed, this will result in the baseline profit of $77,200 with only a 10% purchase rate, leading to high return costs and inefficiency in its shipments.

- The profit per product after mailing cost is $45.5
- The cost of mailing product to not a buyer is $-4
  
## Business Challenge

The key challenge is to optimize the customer selection process by predicting which customers are most likely to purchase the shipped box. Using the existing method, many shipments are wasted on customers who do not buy, which leads to unnecessary shipping and return costs.

The goal of this project is to design a more data-driven approach using **logistic regression** to predict customer purchase behavior. By improving the targeting strategy, Trojan Horse can minimize unnecessary shipments, reduce return costs, and increase overall profitability.

## Target Problem

The main objective is to build a model that will:

- Predict which customers are likely to buy the box using the Trojan Horse database.
- Increase profitability by optimizing customer targeting, reducing shipments to those unlikely to purchase.
  
This will allow Trojan Horse to focus its marketing efforts on high-probability customers, thus improving both the efficiency of its campaigns and its overall profit margin.

## Data and Features

The following historical customer data is available for analysis:

- **Gender**: 0 = Male, 1 = Female
- **Monetary (M)**: Total money spent at Trojan Horse over the past 5 years
- **Recency (R)**: Months since last purchase
- **Frequency (F)**: Total number of purchases
- **First Purchase Date (FirstPurch)**: Months since first purchase
- **Style Categories**: Number of purchases in specific categories like Surfer, BusinessExecutive, Yuppie, Hipster, ClassicGentleman, Rugged, etc.

The model utilizes this data to predict which customers will purchase the box based on their demographic and behavioral characteristics.

## Analytics and Approach

To address the problem, we split data into 70% of training data (1400) and 30% of testing data (600) to train **logistic regression** for developing a predictive model. We employed **SequentialFeatureSelector** to identify the most important features based on their impact on the **roc_auc** score.

Key features selected by **SequentialFeatureSelector**:
- **Gender**
- **Recency** (months since last purchase)
- **Frequency** (total number of purchases)
- **Style Categories** (e.g., Hipster, ClassicGentleman, Rugged)

The logistic regression model helped quantify the relationships between these features and the likelihood of a customer purchasing the box.

### Model Equation
The final model equation is:
$Log(P1/P0) = -0.8276 - 0.8984 * Gender - 0.1127 * R - 0.4222 * Hipster + 0.9617 * ClassicGentleman + 0.4364 * Rugged$

## Results and Conclusion

### 1. Statistical Interpretation of the Model:
- The model explains about 15% (pseudo R-square = 0.15) of the variance in the dependent variable.
- **SequentialFeatureSelector**: We used this technique to select the best 5 features based on **roc_auc** and forward selection.

**Model Equation:**
$Log(P1/P0) = -0.8276 - 0.8984 * Gender - 0.1127 * R - 0.4222 * Hipster + 0.9617 * ClassicGentleman + 0.4364 * Rugged$

- **Gender (0 = Male, 1 = Female)**: A negative coefficient (-0.8984) indicates that being female is associated with lower odds of purchasing the box.
- **Recency (R)**: A negative coefficient (-0.1127) indicates that customers who made a purchase more recently are more likely to be profitable.
- **Hipster Segment**: A negative coefficient (-0.4222) suggests that this group is less profitable.
- **ClassicGentleman & Rugged Segments**: Positive coefficients (0.9617 and 0.4364, respectively) suggest that customers in these categories are more profitable.

### 2. Importance of Analyzing Model Prediction:
- While the model initially achieved a high prediction accuracy of 72%, this did not translate into strong business results. The model’s strict cutoff rate rejected almost 98% of customers, leading to minimal profits of $352.
- This illustrates that **high predictive accuracy** alone doesn’t guarantee business success. Aligning the model’s decisions with **business goals** is crucial.

### 3. Applying the Model in a Business Scenario:
- By adjusting the cutoff rate to match the **average success rate**, we reduced prediction accuracy to 24%. However, this adjustment significantly improved profitability, increasing it to **$1,576**, a **347.7% improvement** over the original model.
- **Predicted Outcomes** for selecting 50,000 potential buyers:
  - Predicted number of purchases: **12,000**
  - Predicted number of returns: **38,000**
  - Predicted profit: **$394,000**, a **410% increase** compared to the baseline profit of $77,200 when mailing randomly.

## Future Work

If the proof-of-concept model shows significant improvements, Trojan Horse’s management may consider scaling the model for full implementation, ultimately increasing profits and efficiency in their marketing campaigns.


---

## **Key Technologies Used:**
- **Python**
- **Logistic Regression**
- **SequentialFeatureSelector**
- **Pandas**
- **Scikit-learn**
- **Matplotlib** (for visualization)
  
## Project Files

- `data/`: Contains the training and testing datasets used in the analysis.
- `model/`: Contains the logistic regression model and feature selection script.
- `analysis/`: Includes the detailed analysis and results from the model.
- `visualizations/`: Contains charts and graphs showing the effectiveness of the model.

