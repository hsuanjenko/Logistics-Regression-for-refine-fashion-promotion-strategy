# Trojan Horse Fashion Subscription Service - Predictive Modeling

## **Business Context:**
Trojan Horse is a personalized fashion subscription service for men, delivering high-end fashion accessories similar to services like Trunk Club, BirchBox, and StitchFix. The company ships curated fashion boxes to 10% of its 500,000-member base each month (around 50,000 customers). Members have 10 days to decide whether to purchase the items, and the company incurs shipping and return costs for any unsold or returned products.

Currently, Trojan Horse selects customers for shipment based on past purchase history and style categories. However, with an average purchase rate of only 10%, this approach leads to inefficiency, higher return costs, and reduced profitability.

## **Target Problem:**
The goal of this project is to build a more accurate, data-driven model using logistic regression to predict which customers are most likely to purchase the items in their monthly shipment. This model will enable Trojan Horse to:
- Reduce unnecessary shipments.
- Minimize return costs.
- Optimize profitability by focusing on customers with higher purchase probabilities.

## **Analytics and Approach:**
To address the problem, we implemented a **logistic regression model** and used **SequentialFeatureSelector** to select the five most important features based on **roc_auc** and forward selection.

### Key Features Used:
- **Gender**: Male (0) or Female (1)
- **Recency (R)**: Months since the last purchase
- **Frequency (F)**: Total number of purchases
- **Style Categories**: Number of purchases in style categories like Hipster, ClassicGentleman, Rugged, etc.

These features were chosen based on their ability to influence purchase behavior, and the model helped predict the likelihood of a customer making a purchase based on these characteristics.

## **Conclusion:**
The logistic regression model provided the following insights:
- **Recency (R)**: Customers who made a purchase more recently are more likely to buy again. A lower recency value correlates with higher purchase likelihood.
- **Style Segments**: Customers from the **ClassicGentleman** and **Rugged** segments are more profitable and should be prioritized for shipments.
- **Hipster Segment**: Customers in this segment, with a negative coefficient, are less likely to purchase and may not be worth targeting for higher profitability.

By leveraging this predictive model, Trojan Horse can make more informed decisions about customer targeting, reduce costs related to returns, and improve profitability by focusing on high-value customers.

---

## **Key Technologies Used:**
- **Python**
- **Logistic Regression**
- **SequentialFeatureSelector**
- **Pandas**
- **Scikit-learn**
- **Matplotlib** (for visualization)

---

### **How to Run the Code:**
1. Clone this repository.
2. Install required dependencies using:
   ```bash
   pip install -r requirements.txt
