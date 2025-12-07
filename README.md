# Dairy Goods Sales Revenue Driver Analysis
Capstone Project 2 – Springboard Data Science Career Track  
Author: *Your Name*  
Date: *Month Year*

---

## 📌 Project Overview
This project analyzes the Dairy Goods Sales dataset (2019–2022) to identify the **key operational and commercial drivers of total revenue** in dairy production.  
Instead of forecasting revenue, the goal is **diagnostic insight**:  
> Which factors most strongly influence Approx. Total Revenue (INR)?  

Using a combination of exploratory data analysis, feature engineering, and machine learning interpretability techniques, this project provides actionable insights for production planning, demand management, and pricing strategy.

---

## 🎯 Problem Statement
Dairy producers face complex challenges balancing freshness, pricing, production, inventory, and distribution. Despite having rich operational data, they often lack a systematic understanding of which factors have the greatest impact on revenue.

This project answers:

**How can dairy producers leverage historical sales and operational data to identify the key factors influencing total revenue, and use these insights to guide pricing and operational decisions?**

---

## 📂 Dataset Description
The dataset includes **4,037** sales and production records across:

- 10 dairy product types  
- 11 brands  
- 15 customer locations  
- 3 sales channels  

Key variables include:
- Product attributes  
- Price per unit  
- Quantity sold, stock, and reorder behavior  
- Shelf life, production date, expiration date  
- Farm-level attributes (land area, number of cows)  
- Final revenue: **Approx. Total Revenue (INR)**

---

## 🧹 Data Wrangling
Key cleaning steps included:

- Validated date fields and ensured consistency  
- Removed mathematically dependent leakage features  
- Verified no missing values  
- Confirmed negative *Days_to_Expire_At_Sale* values were valid  
- Aggregated duplicate rows by categorical keys  
- Extracted year, month, quarter from transaction date  

---

## 📊 Exploratory Data Analysis (Highlights)
- Revenue is heavily right-skewed with several high-value transactions  
- Shelf-life dynamics and production efficiency show stronger relationships with revenue than brand or channel  
- ANOVA shows meaningful differences by product type and storage condition  
- Correlation heatmap reveals expected leakage among revenue-related variables  
- PCA suggests operational metrics drive most variance in the dataset  

Key Visuals:
- Revenue distribution histogram  
- Correlation heatmap  
- Scatterplot: Quantity_per_Cow vs Revenue  
- PCA map of numeric features  

---

## 🧪 Feature Engineering
A set of meaningful operational ratios was engineered, including:

### **Productivity & Efficiency**
- `Quantity_per_Cow`  
- `Production_Density`  
- `Sales_Efficiency`  

### **Demand & Stock Movement**
- `Reorder_Intensity`  
- `Reorder_to_Stock_Ratio`  

### **Shelf-Life & Pricing**
- `Price_to_ShelfLife_Ratio`  
- `Production_to_ShelfLife`  

These engineered variables created a richer signal for modeling and interpretation.

---

## ⚙️ Modeling Approach
Three supervised regression models were trained and evaluated:

1. **Linear Regression** (baseline)  
2. **Random Forest Regressor**  
3. **Gradient Boosting Regressor (Final Model)**  

Data preprocessing included:

- StandardScaler for numeric features  
- One-hot encoding for categorical variables  
- 80/20 train–test split  

---

## 📈 Model Metrics (Final Model)
Final Model: **Gradient Boosting Regressor**

| Metric | Value |
|--------|--------|
| Cross-validated MAE | ~2588 |
| Test MAE | 2452.44 |
| Test R² | 0.92 |
| Hyperparameters | n_estimators=300, learning_rate=0.1, max_depth=4 |

Reason for selection:
- Lowest MAE  
- Strong generalization  
- Captures nonlinear operational behaviors  
- Produces interpretable feature importance rankings  

(See `model_metrics.csv` for the official summary.)

---

## 🔑 Key Drivers of Revenue
Gradient Boosting identified a clear hierarchy of revenue influences:

### **1️⃣ Quantity_per_Cow**  
Strongest predictor. Represents per-animal productivity.

### **2️⃣ Reorder_Intensity**  
Indicates demand strength and product velocity.

### **3️⃣ Price_to_ShelfLife_Ratio**  
Captures perishability-aligned pricing effectiveness.

Supporting drivers:
- Sales_Efficiency  
- Shelf Life  
- Reorder Quantity  
- Number of Cows  
- Land Productivity  

These findings suggest revenue is driven by **operational and demand efficiency**, not by brand or channel effects.

---

## 💡 Recommendations
Based directly on model insights:

### **1. Improve per-cow productivity**  
Enhance feeding strategy, herd management, and operational efficiency.

### **2. Prioritize high Reorder_Intensity products**  
Strong demand → allocate stock, expand distribution, reduce waste.

### **3. Align pricing with shelf-life behavior**  
Optimize Pricing-to-Shelf-Life Ratio to improve turnover and reduce spoilage.

---

## 📁 Repository Structure

