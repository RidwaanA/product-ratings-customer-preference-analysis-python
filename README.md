# Product Ratings & Customer Preference Analysis

# Business Problem
Neat Furniture Store seeks to understand how product mix, pricing, delivery performance, and value-added services influence customer purchasing behavior and satisfaction in a competitive e-commerce environment.

# Objectives
- Analyze demand across product categories, subcategories, and brands
- Evaluate impact of pricing, shipping, and assembly services on order value
- Identify top- and underperforming products using ratings and sales patterns
- Assess delivery performance and payment methods as drivers of satisfaction

# Dataset
- 1938 orders
- 14 features including: product_category, brand, customer_rating, total_amount
- Mix of 6 furniture categories across 12 brands

# Tools & Technologies
- Python (Pandas, NumPy)
- Data Visualization (Seaborn, Matplotlib)
- Jupyter Notebook

# Data Processing / Methodology
- Data cleaning (type fixes, missing value imputation using grouped mean/median)
- Univariate analysis (distribution, skewness, outliers)
- Bivariate analysis (category, brand, pricing, delivery vs ratings)
- Post-imputation validation
- Insight generation

# Key Code Highlights
### Total amount by product subcategory
sns.lineplot(data=df, x='product_subcategory', y='total_amount', ci=None);
plt.xticks(rotation=90)
plt.show()

### Assembly service impact on ratings
df.groupby('assembly_service_requested')['customer_rating'].mean()

### Imputing missing values in assembly cost
df['assembly_cost'] = df['assembly_cost'].fillna(value = df.groupby(['product_category','product_subcategory','brand'])['assembly_cost'].transform('median'))

# Visualization / Dashboard

# Key Insights 

# Recommnedations



