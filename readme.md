# Predictive Modeling for High-Growth Firms: A Risk-Adjusted Machine Learning Framework

## 📌 Project Executive Summary
**The Business Challenge:** In economic development and venture capital, identifying "high-growth" firms (defined here as companies with a Compound Annual Growth Rate **(CAGR) > 20%**) is a high-stakes challenge. Standard statistical models often fail because they treat "missing a winner" and "betting on a loser" as equal mistakes.

**The Solution:** This project developed a data-driven framework using the Bisnode financial dataset to predict growth potential. The innovation lies in the **Economic Logic**: I implemented a custom **1:3 Asymmetric Loss Function**, which mathematically acknowledges that missing a "unicorn" firm is three times more expensive than investing in a firm that fails to grow.

**The Impact:** By shifting from standard accuracy to **Risk-Minimized Decision Making**, the final model identified an optimal investment threshold of **0.25**. This framework allows an organization to proactively target the top ~270 firms in the dataset with the highest risk-adjusted probability of success.

---

## 🚀 Key Results
* **Winning Model:** **Random Forest** (outperformed LASSO and Logistic Regression with a CV AUC of **0.69**).
* **Business Utility:** Reduced the "Expected Loss" significantly by optimizing the decision threshold to **0.25**.
* **Sector Intelligence:** Discovered that growth signals are significantly clearer in the **Services** sector (Min Expected Loss: 0.37) compared to **Manufacturing** (Min Expected Loss: 0.49), leading to a recommendation for more aggressive targeting in Services.

---

## 🛠️ Technical Workflow

### 1. Data Strategy: Signal vs. Noise
* **Sample Filtering:** Processed 10,000+ firm observations, excluding "shell companies" (sales < €1,000) to ensure the model learned from viable economic entities.
* **Feature Engineering:**
    * **Financials:** Applied **log transformations** and **Winsorization** to mitigate the impact of extreme outliers in revenue and assets.
    * **Human Capital:** Integrated non-financial predictors, including **CEO age and experience**, capturing leadership drivers that often precede financial takeoff.
    * **Normalization:** Created Profit & Loss (P&L) and Balance Sheet (BS) ratios to standardize comparisons across different firm sizes.

### 2. Model Development & Evaluation
I conducted a "model competition" between five manual Logistic Regression models, an automated LASSO model, and a Random Forest:
* **Random Forest** proved superior by capturing non-linear interactions, such as the combined effect of a CEO's experience and firm liquidity.

* **Calibration:** The model was validated using **Calibration Curves** to ensure predicted probabilities matched actual growth outcomes, providing an "honest" risk assessment.

### 3. Threshold Optimization (The Decision Rule)
Instead of using the standard 0.5 probability cutoff, I analyzed the **Loss Curve** to find the "sweet spot" for business logic.
* **Optimal Threshold:** **0.25**.
* **Rationale:** At this lower threshold, we capture more high-growth firms that standard models would miss, minimizing the financial penalty of "False Negatives."

---

## 💻 Tech Stack
* **Language:** Python
* **Libraries:** `pandas`, `numpy`, `scikit-learn` (RandomForestClassifier, LogisticRegression, Lasso), `matplotlib`, `seaborn`.

---
