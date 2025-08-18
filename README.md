# Instacart-Customer-Intelligence
End-to-end customer intelligence project using the Instacart dataset — combining reorder prediction, segmentation, market basket analysis, and recommendation systems.

Instacart Customer Intelligence & Reorder Prediction
Problem Statement
Instacart processes millions of grocery orders every week. To stay competitive and deliver a best-in-class shopping experience, Instacart must anticipate what customers will purchase next, understand shopper behavior, and recommend the right products at the right time.
Without effective intelligence, Instacart risks:
•	Customers spending more time searching and fewer items being added to baskets.
•	Marketing campaigns underperforming due to generic targeting.
•	High-value customers disengaging without timely reactivation.
•	Inventory inefficiencies, such as overstocking perishable items or understocking popular products.
Project Objectives & Business Goals
The goal of this project is to transform raw Instacart transaction data into actionable customer intelligence that drives personalization, growth, and efficiency.
1.	Close the Personalization Gap
By predicting likely reorders, Instacart can surface tailored, one-click reorder lists. This reduces search effort, increases basket size, and strengthens loyalty.
2.	Capture Cross-Sell & Upsell Opportunities
Using co-purchase patterns and product similarity, Instacart can recommend complementary or premium items (e.g., bananas → strawberries, regular milk → organic milk). This improves product discovery, raises average order value, and builds trust in Instacart’s recommendation system.
3.	Enable Precision Marketing
Customer segmentation allows marketing teams to design targeted campaigns:
o	Heavy loyal shoppers → rewarded with loyalty programs.
o	Steady regular users → nudged with cross-sell offers.
o	Low-engagement users → reactivated with discounts or bundles.
This approach improves ROI and reduces wasted marketing spend.
4.	Strengthen Customer Retention
By identifying at-risk users early, Instacart can launch personalized nudges and offers that prevent churn. This increases lifetime value and lowers acquisition costs.
5.	Improve Inventory Forecasting & Operations
Reorder predictions help forecast demand more accurately, reducing the chance of overstocking perishables or understocking high-demand products. This enhances supply chain efficiency and ensures product availability for customers.
 Dataset & Files
Dataset: Instacart Market Basket Analysis (2017, 3M+ orders, 30M+ rows).
Key Inputs:
•	orders.csv – order metadata (user, sequence, time).
•	order_products__prior.csv – historical product-level data.
•	order_products__train.csv – labels for supervised training (reordered or not).
•	products.csv, aisles.csv, departments.csv – product metadata.
Processed Files:
•	prior_data.pkl – merged dataset (~32M rows).
•	user_features.pkl – user-level metrics.
•	product_features.pkl – product, aisle, department stats.
•	up.pkl – user × product interaction features.
•	df.pkl – final modeling dataset (8.4M rows, 50+ features).
Project Notebooks:
1.	Part 1 – Exploratory Data Analysis & Data Preparation
2.	Part 2 – Feature Engineering & Training Base Construction
3.	Part 3 – Modeling & Evaluation (XGBoost, LightGBM, CatBoost)
4.	Part 4 – Clustering & Segmentation (KMeans, PCA, DBSCAN)
5.	Part 5 – Market Basket Analysis & Recommendations (Apriori, Word2Vec, KMeans)
Methodology & Business Relevance
Part 1 – Exploratory Data Analysis (EDA)
What we did:
•	Analyzed 32M+ orders: basket size distribution, reorder ratios, time-of-day/week patterns, top products & departments.
•	Found ~59% of items are reorders, peak shopping happens on Sundays/Mondays, baskets are typically <15 items.
Business Value:
•	Informs promotion timing and app design (highlight reorders during peak windows).
•	Identifies high-value categories (produce, dairy, beverages) that drive repeat purchases.
Part 2 – Feature Engineering & Training Base
What we did:
•	Created user features (frequency, basket size, timing, reorder ratios).
•	Built product features (popularity, reorder rates, aisle/department rollups).
•	Constructed user × product features (frequency, recency, reorder streaks).
•	Produced df.pkl with 8.4M labeled pairs for modeling.
Business Value:
•	Provides a 360° view of customer behavior.
•	Distinguishes habitual purchases vs. one-off items, enabling more relevant targeting.
Part 3 – Reorder Prediction Modeling
What we did:
•	Tested XGBoost, LightGBM, CatBoost.
•	Best: LightGBM (threshold = 0.23) with F1 ≈ 0.45, ROC-AUC ≈ 0.84.
•	SHAP analysis confirmed key drivers: user reorder ratio, product reorder rate, days since prior order.
Business Value:
•	Powers a personalized reorder carousel → bigger baskets, higher satisfaction.
•	Improves demand forecasting by predicting which products will be reordered.
Part 4 – Customer Segmentation (Clustering)
What we did:
•	Used KMeans and PCA to cluster users into 3 groups:
1.	Heavy loyal shoppers (large baskets, frequent orders).
2.	Core steady users (medium baskets, consistent cadence).
3.	Low-engagement users (small baskets, long gaps).
Business Value:
•	Enables targeted marketing campaigns by segment.
•	Guides loyalty rewards, cross-sell offers, and reactivation strategies.
Part 5 – Market Basket Analysis & Recommendations
What we did:
•	Apriori algorithm revealed frequent itemsets (bananas, strawberries, avocados dominate).
•	Association rules showed strong product affinities (e.g., raspberries ↔ strawberries, bananas ↔ Fuji apples).
•	Trained Word2Vec embeddings → product similarity captured in vector space.
•	PCA visualized product clusters; KMeans grouped products into interpretable segments (produce, dairy, packaged).
•	Built recommendation prototypes: product-to-product, basket-based, and user-personalized.
Business Value:
•	Supports cross-sell & upsell by suggesting complementary or premium items.
•	Improves product discovery and app experience with smarter recommendations.
•	Informs digital shelf design & merchandising through product clustering.
Results at a Glance
•	Prediction Model: LightGBM, F1 ≈ 0.45, ROC-AUC ≈ 0.84.
•	Segmentation: 3 clear customer groups for marketing strategy.
•	Market Basket: High-lift associations validate bundling opportunities.
•	Embeddings: Captured semantic similarity; prototype recommenders worked at product, basket, and user levels.
Business Impact
•	Personalization: Reorder predictions reduce friction, grow basket size, and improve satisfaction.
•	Revenue Growth: Cross-sell and upsell opportunities increase average order value.
•	Smarter Marketing: Segmentation enables precision targeting and higher ROI on campaigns.
•	Retention: Early detection of at-risk users supports proactive re-engagement.
•	Operational Efficiency: Forecasting reorders improves inventory and reduces waste.
 Future Work
•	Scale recommendations across all users in real time.
•	Extend to churn prediction and upsell modeling.
•	Deploy as a Streamlit/Flask app with dashboards for marketers.
•	Experiment with hybrid recommenders (embeddings + collaborative filtering).
•	Automate segmentation and affinity reporting for business teams.
<img width="468" height="650" alt="image" src="https://github.com/user-attachments/assets/235fbcc3-a31c-4122-b55d-d6b7961fad39" />
