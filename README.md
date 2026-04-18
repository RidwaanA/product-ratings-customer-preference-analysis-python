# 🛋️ Product Ratings & Customer Preference Analysis

## Project Overview
This project analyzes order and customer satisfaction data for Neat Furniture Store, an online furniture retailer operating across 12 brands, 6 product categories, and 31 subcategories.

Using Python (Pandas, Seaborn, Matplotlib), the analysis explores purchasing behavior, delivery performance, pricing patterns, and the impact of assembly services on customer ratings — providing actionable insights to help the business enhance customer experience and sharpen its product strategy.

## Business Problem
**Neat Furniture Store** aims to strengthen its competitive position in the e-commerce furniture market by better understanding what drives customer satisfaction and purchasing decisions.

The challenge:
➡️ Identify which product categories, brands, delivery conditions, and service attributes most influence customer ratings and order value.

## Dataset
- ~1,938 customer orders
- 14 features including: `product_category`, `product_subcategory`, `brand`, `customer_rating`, `customer_id`, `total_amount`, `delivery_status`, `payment_method`
- Covers 12 brands, 6 product categories, and 31 product subcategories
- Mix of free and paid assembly orders with 4 columns requiring missing value treatment

## Tools & Technologies
- **Python** (Pandas, NumPy, Seaborn, Matplotlib)
- **Jupyter Notebook**
- **Tableau**

## Data Processing / Methodology
- Converted `order_id` and `customer_id` from integer to object dtype for appropriate handling
- Investigated and flagged duplicate order IDs assigned to multiple customers as a data quality issue
- Imputed missing values in `brand` using mode; `shipping_cost` and `customer_rating` using group-wise mean imputation (grouped by category, subcategory, and brand); `assembly_cost` using group-wise median imputation (due to outliers)
- Verified post-imputation distributions against originals to confirm data integrity
- Performed univariate, bivariate, and multivariate analysis across numerical and categorical features
- Conducted correlation analysis across all numerical variables

## Key Code Highlights
```python
// Group-wise mean imputation for missing shipping costs
df['shipping_cost'] = df['shipping_cost'].fillna(
    df.groupby(['product_category', 'product_subcategory', 'brand'])['shipping_cost'].transform('mean')
)
```
```python
// Group-wise median imputation for assembly cost (outliers present)
df['assembly_cost'] = df['assembly_cost'].fillna(
    df.groupby(['product_category', 'product_subcategory', 'brand'])['assembly_cost'].transform('median')
)
```
```python
// Assembly service impact on ratings
df.groupby('assembly_service_requested')['customer_rating'].mean()
```
```python
// Average customer rating by product category
sns.lineplot(data=df, x='product_category', y='customer_rating', ci=None)
plt.xticks(rotation=90)
plt.show()
```

## Visualization / Dashboard
- Distribution plots and boxplots for all numerical features (product price, shipping cost, assembly cost, total amount, delivery window days, customer rating)
- Count plots for all categorical features (product category, subcategory, brand, delivery status, payment method, assembly service)
- Line and box plots for total amount, delivery window days, and customer rating across categories, subcategories, and brands
- Correlation heatmap and pairplot across numerical variables
- Post-imputation distribution comparisons to validate data integrity

🔗 **[View Interactive Tableau Dashboard](https://public.tableau.com/your-dashboard-link-here)** *(replace with your actual link)*

## Key Insights
- **Most popular categories:** → Outdoor (338 orders) and Living Room (333 orders); Dining Room ordered the least at 303
- **Top subcategories:** → Bar Cart, Pantry Cabinet, Garden Chair, Kitchen Cabinet, and Office Chair led in demand
- **Highest-rated categories:** → Outdoor, Kitchen, and Dining Room; Office and Living Room rated the lowest
- **Brand performance:** → Target and Ashley Furniture led in customer ratings; IKEA and World Market ranked lowest
- **Delivery impact:** → Cancelled and Delivered orders received the highest ratings; In Transit and Failed Delivery the lowest
- **Assembly services:** → Orders that included assembly requests were rated marginally higher on average
- **Payment method:** → Bank Transfer-linked orders had the highest ratings; Google Pay the lowest
- **Pricing:** → Bedroom, Kitchen, and Living Room products generated the highest total order values; Office products were the least costly 

## Recommendations
- Prioritize inventory and marketing for high-demand categories (Outdoor, Living Room) while reassessing strategies for lower-demand ones like Dining Room
- Invest in top subcategories (Bar Cart, Garden Chair, Kitchen Cabinet) and consider repositioning or phasing out consistently low performers (Bar Stool, Wardrobe, Armchair)
- Strengthen partnerships with highly patronised brands; review pricing, quality, or branding for underperforming brands to improve uptake
- Investigate the high rate of failed, cancelled, and rescheduled orders — improve logistics, order fulfilment, and customer communication processes
- Reduce delivery window days for slow categories (Living Room, Bedroom, Dining Room), benchmarking against faster categories like Outdoor
- Focus quality improvement efforts on Office and Living Room products, which received the lowest ratings despite reasonable demand
- Promote higher-rated payment methods and optimise the checkout experience for lower-rated options like Google Pay

## Outcome / Impact
This analysis enables:
- ✅ Data-driven product assortment and inventory decisions
- ✅ Targeted brand partnership and pricing strategies
- ✅ Improved delivery and fulfilment operations
- ✅ Enhanced customer experience through service and payment optimisation

## Next Steps
- Build a predictive model to forecast customer ratings based on product and order attributes
- Integrate time-series analysis to track seasonal demand and rating trends
- Develop an interactive Tableau dashboard for real-time monitoring of product and delivery performance
