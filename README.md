# Telco Customer Churn: Retention Strategy Executive Summary

## 1. Project Objective & Business Challenge
The goal of this initiative was to design a data-driven customer retention framework. Historically, retention campaigns either over-target users who would have stayed anyway, or waste budget on customers with low projected lifetime value (CLTV). 

Management required a strategy that enforces two strict financial constraints:
1. **Maximum Budget:** $200,000 max spend at $50 per intervention.
2. **Financial Efficiency:** A minimum Return on Investment (ROI) of 2.0x.

## 2. Methodology: Predictive ML Meets Financial Mathematics
To solve this, we combined Machine Learning with expected-value business logic:

1. **Probability Calibration (XGBoost):**
   We trained an XGBoost classification algorithm to identify churn risks. Crucially, the model's raw probability outputs were mathematically calibrated against a real-world holdout dataset to provide true, undiscarded likelihoods of churn, avoiding "over-prediction" bias common in algorithmic modeling.

2. **Expected Incremental Profit (EIP) Framework:**
   Instead of just targeting the highest churn risks or the highest CLTV users, we targeted based on **Expected Incremental Profit**. For every candidate, we calculated:
   *(Calibrated Churn Probability × 8% Assumed Save Rate × CLTV) - $50 Intervention Cost*

   *Note: We stress-tested our assumption down to an 8% intervention success rate to align with conservative Telco industry benchmarks.*

## 3. Recommended Optimization Strategy
By rank-ordering all eligible customers descending by their calculated EIP, we strictly filtered out any customer yielding a negative expected profit. 

**Our final optimized portfolio yields the following projected metrics:**

| Metric | Business KPI |
| :--- | :--- |
| **Customers Targeted** | 829 Users |
| **Total Intervention Budget** | $41,450.00 |
| **Projected Incremental Profit** | $76,440.87 |
| **Projected ROI** | 2.84x |

### Constraint Validations
- **Budget Constraint:** Handled. The $41,450 projected spend leaves $158,550 of the $200k max budget unexposed, preventing over-commitment to low-profit interventions.
- **ROI Constraint:** Exceeded. The 2.84x realized ROI easily passes the >= 2.0x managerial limit.

## 4. Financial Impact (Optimized vs Baseline)
If we were to blindly spend the exact same $41,450 budget by targeting the customers with the *highest historical CLTV* (a common legacy business heuristic), the results would be measurably inferior:

| Strategy | Total Spend | Expected Profit | ROI |
| :--- | :--- | :--- | :--- |
| **AI-Optimized (EIP Ranking)** | $41,450 | **$76,441** | **2.84x** |
| Baseline (Top CLTV Ranking) | $41,450 | $63,108 | 2.52x |

**The Bottom Line:** By deploying the machine learning framework to target via Expected Incremental Profit, the company achieves **an additional $13,333 (+21% lift)** in pure profit generated from the exact same block of marketing spend.
