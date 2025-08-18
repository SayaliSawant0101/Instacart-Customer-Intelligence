# Instacart-Customer-Intelligence
End-to-end customer intelligence project using the Instacart dataset — combining reorder prediction, segmentation, market basket analysis, and recommendation systems.

# 🛒 Instacart Customer Intelligence & Reorder Prediction  

## 📌 Problem Statement  
Instacart processes millions of grocery orders every week. To stay competitive and deliver a best-in-class shopping experience, Instacart must anticipate what customers will purchase next, understand shopper behavior, and recommend the right products at the right time.  

Without effective intelligence, Instacart risks:  
- ⏳ Customers spending more time searching and fewer items being added to baskets.  
- 🎯 Marketing campaigns underperforming due to generic targeting.  
- 💔 High-value customers disengaging without timely reactivation.  
- 📦 Inventory inefficiencies, such as overstocking perishable items or understocking popular products.  

---

## 🎯 Project Objectives & Business Goals  
The goal of this project is to transform raw Instacart transaction data into **actionable customer intelligence** that drives personalization, growth, and efficiency.  

1. **Close the Personalization Gap**  
   Predict likely reorders → surface one-click reorder lists. Reduces search effort, increases basket size, and strengthens loyalty.  

2. **Capture Cross-Sell & Upsell Opportunities**  
   Recommend complementary or premium items (e.g., bananas → strawberries, regular milk → organic milk). Improves product discovery, raises order value, builds trust.  

3. **Enable Precision Marketing**  
   Segment customers into targeted campaigns:  
   - Heavy loyal shoppers → loyalty rewards  
   - Steady regular users → cross-sell nudges  
   - Low-engagement users → reactivation bundles  

   Improves ROI and reduces wasted spend.  

4. **Strengthen Customer Retention**  
   Identify at-risk users early → personalized nudges to prevent churn. Increases LTV, lowers acquisition costs.  

5. **Improve Inventory Forecasting & Operations**  
   Predict reorders at scale → reduce overstocking/understocking, improve supply chain efficiency.  

---

## 📂 Dataset & Files  

**Dataset:** Instacart Market Basket Analysis (2017, 3M+ orders, 30M+ rows).  

**Key Inputs:**  
- `orders.csv` – order metadata (user, sequence, time)  
- `order_products__prior.csv` – historical product-level data  
- `order_products__train.csv` – labels for supervised training (reordered or not)  
- `products.csv`, `aisles.csv`, `departments.csv` – product metadata  

**Processed Files:**  
- `prior_data.pkl` – merged dataset (~32M rows)  
- `user_features.pkl` – user-level metrics  
- `product_features.pkl` – product, aisle, department stats  
- `up.pkl` – user × product interaction features  
- `df.pkl` – final modeling dataset (8.4M rows, 50+ features)  

**Project Notebooks:**  
1. Part 1 – Exploratory Data Analysis & Data Preparation  
2. Part 2 – Feature Engineering & Training Base Construction  
3. Part 3 – Modeling & Evaluation (XGBoost, LightGBM, CatBoost)  
4. Part 4 – Clustering & Segmentation (KMeans, PCA, DBSCAN)  
5. Part 5 – Market Basket Analysis & Recommendations (Apriori, Word2Vec, KMeans)  

---

## 🛠 Methodology & Business Relevance  

### Part 1 – Exploratory Data Analysis (EDA)  
**What we did:**  
- Analyzed 32M+ orders (basket size, reorder ratios, timing, top products/categories).  
- Found ~59% of items are reorders; peak shopping on Sundays/Mondays; baskets <15 items.  

**Business Value:**  
- Optimize promotion timing & app design.  
- Identify high-value repeat categories (produce, dairy, beverages).  

---

### Part 2 – Feature Engineering & Training Base  
**What we did:**  
- Built user, product, and user×product features.  
- Produced `df.pkl` with 8.4M labeled pairs for modeling.  

**Business Value:**  
- Creates a **360° view** of customer behavior.  
- Differentiates habitual vs. one-off purchases → more relevant targeting.  

---

### Part 3 – Reorder Prediction Modeling  
**What we did:**  
- Tested XGBoost, LightGBM, CatBoost.  
- Best: LightGBM (threshold = 0.23), F1 ≈ 0.45, ROC-AUC ≈ 0.84.  
- SHAP: key drivers were reorder ratio, reorder rate, recency.  

**Business Value:**  
- Powers personalized reorder carousel → bigger baskets, higher satisfaction.  
- Improves demand forecasting accuracy.  

---

### Part 4 – Customer Segmentation (Clustering)  
**What we did:**  
- KMeans + PCA → 3 customer groups:  
  1. Heavy loyal shoppers  
  2. Core steady users  
  3. Low-engagement users  

**Business Value:**  
- Enables targeted campaigns → loyalty rewards, cross-sell nudges, reactivation.  

---

### Part 5 – Market Basket Analysis & Recommendations  
**What we did:**  
- Apriori → frequent bundles (bananas, strawberries, avocados).  
- Association rules → strong affinities (e.g., raspberries ↔ strawberries).  
- Word2Vec embeddings → product similarity.  
- PCA + KMeans → grouped products into clusters.  
- Built product, basket, and user-level recommenders.  

**Business Value:**  
- Supports cross-sell & upsell.  
- Improves discovery & app experience.  
- Informs digital shelf design & merchandising.  

---

## 📊 Results at a Glance  
- **Prediction Model:** LightGBM → F1 ≈ 0.45, ROC-AUC ≈ 0.84  
- **Segmentation:** 3 actionable customer groups  
- **Market Basket:** High-lift product associations validated bundles  
- **Embeddings:** Captured semantic similarity for recommendations  

---

## 💼 Business Impact  
- ✅ Personalization → bigger baskets, higher satisfaction  
- ✅ Revenue Growth → cross-sell & upsell boost AOV  
- ✅ Smarter Marketing → segmentation improves ROI  
- ✅ Retention → early detection prevents churn  
- ✅ Operational Efficiency → reorder forecasts improve inventory  

---

## 🚀 Future Work  
- Scale recommendations for all users in real time  
- Extend to churn prediction & upsell modeling  
- Deploy Streamlit/Flask app + dashboards  
- Explore hybrid recommenders (embeddings + collaborative filtering)  
- Automate segmentation & affinity reporting  
