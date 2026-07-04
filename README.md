# Grocery Mart Customer Segmentation Project

## Project Background
Grocery Mart is a grocery retailer running marketing campaigns across its customer base without a clear view of who its customers actually are. Campaigns are currently sent broadly, which risks wasting spend on customers unlikely to respond while under-serving high-value segments with generic messaging.

This project uses unsupervised machine learning to segment Grocery Mart's customers into distinct groups based on their demographics and purchasing behavior. The goal is to move from a one-size-fits-all marketing approach to targeted strategies tailored to each segment's income level, family structure, and campaign responsiveness, improving campaign efficiency and reducing wasted marketing spend on unresponsive customers.

## Dataset Structure
The dataset used for this project consists of a single source:

- **Grocery Mart Data**: customer demographic and purchase history records, comprising 2,240 rows across 29 raw columns, grouped into four categories (_Demographics_, _Customer Tenure_, _Spending by Category_, _Purchase Channels & Purchase History_).
  
_Note: After removing rows with missing income values and capping age/income outliers, the working dataset used for clustering has 2,212 customers._

## Executive Summary
Four distinct customer segments emerged from clustering Grocery Mart's customer base on PCA-reduced demographic and behavioral features (K-Means: k=4):

- **Established Family Providers**: mid-to-high income parents with teenagers, moderate-to-high spend
- **Budget-Conscious Young Parents**: youngest, lowest-income segment; high app engagement but low conversion
- **Affluent DINKs (Dual Income, No Kids)**: highest income and spend, most campaign-responsive segment
- **Value-Driven Large Families**: largest households, oldest on average, lowest campaign response rate

Spend varies by as much as 13.5x between the highest and lowest-spending segments, and campaign response rates vary by 4.3x, revealing that a single, undifferentiated marketing strategy leaves significant value on the table. Segment-specific strategies (premium upsell, value bundles, cart-conversion offers, and loyalty re-engagement) are recommended to close this gap.

## Codes
The **Python Pipeline** used for data cleaning, EDA, feature engineering, dimensionality reduction with PCA, optimal cluster selection via the Elbow Method and K-Means clustering can be found [here](customer_segmentation.ipynb).

## Insights & Recommendations
Detailed segment profiles and targeted marketing strategy recommendations for each of the four clusters can be found [here](Insights%20&%20Recommendations.pdf). 

## Assumptions and Caveats

#### Assumptions:
* Missing `Income` values were dropped rather than imputed. Extreme age/income outliers were capped, under the assumption these do not represent the target customer base.
* Categorical variables (`Education`, `Living_With`) were label-encoded; this introduces an implicit ordering that is not meaningful in terms of distance-based clustering here, but should be reconsidered if the segmentation approach changes.

#### Caveats:
* This is an unsupervised analysis and there are no target variable, thus segment quality is validated by the Elbow Method instead of classification accuracy.
* Cluster assignments are based on a one-time snapshot of historical purchasing behavior, and may drift with changes to customer behavior over time, it is recommended to re-cluster periodically rather than consider segments as permanent.

