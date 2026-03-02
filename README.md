# Cost-Sensitive Churn Prediction: Not All Clients Are Equal

### Identifying Value-at-Risk through LTV-Weighted Machine Learning

---

## Project Overview
In retail banking, standard churn models treat every client as an equal unit. This project challenges that approach by implementing a **Cost-Sensitive Learning** framework. By integrating **Lifetime Value (LTV)** directly into the model's loss function, we prioritize the retention of high-value segments, ensuring that the business focuses its resources where the economic impact is greatest.

---

## Business Problem
The cost of acquiring a new client is significantly higher than retaining an existing one. However, the cost of a **False Negative** (missing a high-value churner) can be 50x higher than a **False Positive** (offering a retention discount to a stable client). This model addresses this asymmetry to maximize the ROI of retention campaigns.

---

## Methodological Approach

### 1. Behavioral Signal Engineering
Instead of relying on static demographics, this model utilizes **Balance Volatility**. Inspired by GARCH models in financial time series, we detect cash-flow instability as an early warning signal of account closure before the client actually leaves.

### 2. Cost-Sensitive Training (XGBoost)
We implemented sample weighting where each observation's influence on the gradient descent is proportional to its LTV:
* High-LTV clients have a higher weight in the loss function.
* The model is forced to minimize errors specifically on the most profitable segments.

### 3. Threshold Optimization
The default 0.5 probability threshold is ignored in favor of an **Economic Threshold Optimization**. We selected the threshold that minimizes the total LTV lost while maintaining a minimum precision constraint of 50% for the retention team.



---

## Model Results and Business Impact

* **Model Performance:** AUC-ROC of **0.761**, reflecting a realistic and robust performance under real-world noise levels ($\sigma=0.25$).
* **Capital Protection:** Successfully identified and protected over **€1.15M** in LTV.
* **Economic Efficiency:** The optimized threshold saved **€436,443** in undetected churn compared to a standard 0.5 threshold model.
* **ROI:** The model shows a theoretical return of **579x** when comparing protected LTV against the operational cost of retention offers.

---

## Strategic Recommendations

Based on the model's output, the retention strategy is segmented as follows:
* **High-Value at Risk:** Direct personal intervention and bespoke financial advisory.
* **Mid-Value at Risk:** Automated personalized retention offers and fee waivers.
* **Low-Value at Risk:** Digital nurturing campaigns and low-cost automated touchpoints.

---

## Future Research: The Path to Causality
The natural progression of this project is moving from predictive to prescriptive analytics. Using **Double Machine Learning (DML)**, the next phase aims to estimate the causal effect of specific interventions, answering not just *who* will leave, but exactly *what* action will make them stay. This is the core subject of my current MSc research.

---

## Author
**Julia Anglada Lomaeva**
* MSc in Statistics | Creative Data Scientist
* Background in Business Administration 
* [LinkedIn](https://linkedin.com/in/juliaanlo/)
* [Link to Project Notebook](https://colab.research.google.com/drive/1MCZRyxrofZRExaHIOWEJZ3gad5nwsaFf#scrollTo=qL8zCK4tEvzy)
