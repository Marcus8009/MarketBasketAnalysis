# Market Basket Analysis with PySpark on Instacart Dataset

This notebook performs a market basket analysis using PySpark on a dataset from Instacart that consists of 32M rows. 

The data is sourced from : https://www.kaggle.com/competitions/instacart-market-basket-analysis


The key steps and findings are summarized below:

## Steps:

1. **Environment Setup**:
   - Install and import necessary libraries (`pandas`, `pyspark`).
   - Initialize Spark session with optimized settings.

2. **Data Loading**:
   - Define schemas for CSV files.
   - Load datasets (`order_products_prior.csv` and `products.csv`) into Spark DataFrames.
   - Convert CSV files to Parquet format for faster loading in future runs.

3. **Data Preparation**:
   - Merge DataFrames using broadcast join.
   - Repartition data for balanced distribution.
   - Create a product-level dataset and transaction data.

4. **Model Training**:
   - Apply the FPGrowth algorithm to find frequent itemsets and association rules.
   - Convert array columns to strings for easier visualization.

5. **Results Saving**:
   - Save frequent itemsets and association rules to CSV files.
   - Read and sort frequent itemsets and association rules for debugging.

6. **Results Visualization**:
   - Show the top frequent itemsets and association rules.

7. **Performance Measurement**:
   - Measure and print the execution time.

## Analysis

### High Confidence and Lift Values

- **Lemon Sparkling Water → Grapefruit Sparkling Water**: High confidence (0.35) and extremely high lift (79.28) suggest a strong association. Customers who buy Lemon Sparkling Water are very likely to buy Grapefruit Sparkling Water.
- **Non Fat Raspberry Yogurt → Icelandic Style Skyr Blueberry Non-fat Yogurt**: High confidence (0.45) and lift (75.44) indicate a strong relationship. Promoting these together could be effective.

### Yogurt Products

Multiple yogurt products show strong associations, such as Non Fat Raspberry Yogurt with Nonfat Icelandic Style Strawberry Yogurt and Vanilla Skyr Nonfat Yogurt. This suggests a pattern where customers buying one type of yogurt are likely to buy another.

### Sparkling Water

Several sparkling water combinations, like Sparkling Lemon Water with Lime Sparkling Water and Sparkling Water Grapefruit, show high confidence and lift values. This indicates a strong preference for variety among sparkling water buyers.

### Greek Yogurt

Products like Total 2% Lowfat Greek Strained Yogurt with different flavors (Blueberry, Strawberry, Peach) have strong associations. Customers buying one flavor are likely to buy others.

## Marketing Promotions

Based on these insights, here are some suitable marketing promotions:

### Bundle Offers

- **Sparkling Water Variety Packs**: Create bundles that include Lemon, Grapefruit, and Lime Sparkling Water. Offer a discount on the bundle to encourage customers to try multiple flavors.
- **Yogurt Packs**: Offer mixed packs of Non Fat Raspberry Yogurt, Icelandic Style Skyr Blueberry Non-fat Yogurt, and Nonfat Icelandic Style Strawberry Yogurt. This can attract customers who enjoy variety in their yogurt choices.

### Cross-Promotions

- **Yogurt and Sparkling Water**: Promote a discount when customers buy both yogurt and sparkling water. For example, "Buy any 3 yogurts and get a sparkling water for free."
- **Healthy Snack Combos**: Pair items like Clementines with Greek Yogurt or Sparkling Water to promote healthy snacking options.

### Loyalty Programs

- **Frequent Buyer Rewards**: Implement a loyalty program where customers earn points for purchasing specific combinations, such as different flavors of Greek yogurt or sparkling water. Points can be redeemed for discounts or free products.

### Seasonal Promotions

- **Summer Refreshment Packs**: During summer, promote sparkling water combinations as refreshing drinks. Offer limited-time discounts on variety packs.
- **Back-to-School Snacks**: Promote yogurt and fruit combinations as healthy snacks for students. Offer special deals for parents buying these items in bulk.
