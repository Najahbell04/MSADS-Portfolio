IST 718: Big Data Analytics

**Project:** Predictive Insights for Apple Sales Data
**Presented by:** Najah Bell & Anthony Klein
**Tools:** Python · pandas · scikit-learn · matplotlib · seaborn



Project Overview

This project analyzed LLM-generated Apple historical sales data spanning January 2020 through November 2024 to generate predictive insights for business decision-making. Three core business questions were investigated:

1. Are there specific months in which product launches historically perform better in terms of sales?
2. Which store locations demonstrate the strongest sales performance, and which consistently underperform?
3. Can future sales and profit be forecasted at the store or country level?



Key Findings

**Seasonality:** January, March, and July/August/October were the highest-performing sales months. Counterintuitively, November and December ranked lowest, due to the dataset's synthetic nature, which does not reflect real-world holiday shopping patterns.

**Store Performance:** Apple Central World consistently generated the highest revenue globally. Despite the US being the top-performing country overall, only 1 US store appeared in the top 10, while 4 of the 10 lowest-performing stores were US locations.

**Country Rankings:** United States led by a wide margin, followed by Australia and China.

**Product Seasonality:** Accessories, laptops, smartphones, and tablets peaked in March; smart speakers in April; desktops in May; subscription services in August; audio products and wearables in October; streaming devices in December.



Predictive Models

| Model | RMSE | Error Rate |
|-------|------|------------|
| Linear Regression | 717 units | 14.1% |
| Random Forest Regressor | 841 units | 16.5% |

**Features used:** Lagged sales values, cyclical month encoding
**Evaluation metric:** Root Mean Square Error (RMSE)

Linear Regression outperformed Random Forest — demonstrating that on smooth, synthetic datasets, simpler models can outperform ensemble methods that overfit to low-noise data.



Visualizations Produced

•	Total Sales by Month (bar plot, all years combined)
•	Total Monthly Revenue with Best Month for Promotions highlighted
•	Heatmap of Top 10 Performing Stores by Month
•	Heatmap of Worst 10 Performing Stores by Month
•	Heatmap of Top 10 Selling Countries by Month
•	Heatmap of Best-Selling US Stores by Month
•	Heatmap of Top 10 Products by Monthly Revenue
•	Actual vs. Predicted Monthly Sales (scatter plot)
•	Residuals vs. Predicted Sales (scatter plot)



Files in This Folder

| File | Description |
|------|-------------|
| `IST718_Presentation.pdf` | Final project presentation slides |
| `apple_sales_analysis.ipynb` | Python notebook — EDA and modeling (upload if available) |



Ethical Reflection

This project used LLM-generated synthetic data. The patterns observed — particularly the underperformance of November and December — do not reflect real-world Apple sales trends. Transparently disclosing this limitation is an ethical obligation: business decisions operationalized from synthetic data without this disclosure could cause real organizational harm.

