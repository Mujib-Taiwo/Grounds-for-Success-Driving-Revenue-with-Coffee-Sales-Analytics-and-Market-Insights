# Grounds-for-Success-Driving-Revenue-with-Coffee-Sales-Analytics-and-Market-Insights
1. INTRODUCTION

Coffee is one of the most consumed beverages worldwide, with demand patterns influenced by various factors such as seasonality, consumer preferences, and pricing. Understanding sales trends can provide valuable insights for business decisions, such as inventory management, pricing strategies, and marketing efforts. This analysis focuses on coffee sales data obtained from kaggle, spanning from March 2024 to February 2025. The dataset provides valuable insights into sales trends, payment methods, and popular coffee choices over the given period. The data is structured across two CSV files, each representing a distinct year, and consists of 3,373 rows with the following key columns: date , datetime, cash_type, card, money and coffee_name. Through Exploratory Data Analysis (EDA), we aim to uncover key trends such as peak sales periods, preferred coffee types, and customer payment behaviors. The insights gained will help in understanding market demand, optimizing pricing strategies, and making data-driven business decisions.

2. DATA COLLECTION AND CLEANING
   
Data Collection

The dataset used in this analysis was sourced from Kaggle, a well-known platform for open-source datasets and machine learning projects. It consists of two CSV files, each containing transaction data for different years, covering the period from March 2024 to February 2025. The dataset captures a wide range of transactional details, making it a valuable resource for understanding coffee sales trends, customer preferences, and purchasing behaviors.

Dataset Overview

The dataset contains 3,373 rows and includes six key columns:
•	date – The date of the transaction.
•	datetime – The exact timestamp when the purchase was made.
•	cash_type – The payment method used (either cash or card).
•	card – An anonymized card identifier for card transactions.
•	money – The transaction amount in monetary value.
•	coffee_name – The specific type of coffee purchased.
While the dataset provides useful information, it requires preprocessing to ensure accuracy and consistency before analysis.
 
Data Cleaning Process

Cleaning the dataset was a crucial step to ensure that the analysis is based on high-quality, error-free data. The following data cleaning procedures were applied:
a. Handling Missing and Incomplete Data
•	Some rows contained missing values, particularly in the cash_type and money columns. These were either imputed using logical assumptions (e.g., transactions with blank card numbers were classified as cash payments) or removed if they lacked critical details.
b. Correcting Date and Time Anomalies
•	The datetime column exhibited inconsistencies, with some timestamps showing incorrect formats (e.g., "46:33.0"), which is not a valid time format. These were either corrected or removed to prevent errors in time-based analysis.
•	The date column was reformatted into a DD-MM-YYYY format to maintain uniformity.
c. Standardizing Categorical Data
•	The coffee_name column contained variations in naming conventions, such as "Americano with Milk" vs. "Americano w/ Milk." These inconsistencies were resolved by grouping similar entries under a standardized naming scheme.
d. Removing Duplicate Transactions
•	Duplicate rows, which could result from data entry errors or system glitches, were identified and removed to prevent misleading analysis results.
e. Converting Data Types
•	The date and datetime columns were properly formatted as datetime objects for time-series analysis.
f. Feature Engineering – Creating New Columns
To enhance the dataset and allow for more in-depth analysis, several new columns were derived from the original data:
•	coffee_group – Categorizing coffee types into broader groups (e.g., "Americano with Milk" grouped under "Americano").
•	Day Name – Extracting the day of the week from the date (e.g., Monday to Sunday).
•	Milk Preference – Identifying whether the coffee was ordered with or without milk.
•	End of Month – A feature indicating the last day of the month for financial and sales trend analysis.
•	Season – Categorizing transactions based on seasonal periods (e.g., Spring, fall, summer and winter).
•	Time Period – Classifying transactions into different parts of the day, such as Morning, Afternoon, or Evening, based on the transaction time.
These newly created columns allowed for more granular insights into customer preferences, peak sales periods, and seasonal trends.
Processed Data
Following the data cleaning and transformation phase, two structured datasets were created to enhance data granularity and provide deeper insights into transactional patterns. These processed datasets serve different analytical purposes. These queries updates when additional data are added.
a. fDatasets (Enhanced Transactional dataset)
The first processed dataset, fDatasets, is an enriched version of the original dataset. It retains the core transaction details while integrating additional derived columns to enhance its analytical depth. These additional columns, as explained in the data cleaning section, include: Day Name, Milk Preference, End of Month,Season,Time Period.
By incorporating these new fields, fDatasets enables more detailed trend exploration, such as analyzing peak transaction times, seasonal variations in coffee preferences, and consumer habits based on milk preference or payment method.
b. TransactionMonthOfEachYear (Aggregated Monthly Data)
While fDatasets focuses on individual transactions, the second processed dataset, TransactionMonthOfEachYear, provides a summarized view of monthly trends. This dataset aggregates transactional data to offer insights into overall revenue and transaction volume over time. It includes the following metrics:
•	End of Month: The final date of each recorded month.
•	Revenue: Total revenue generated in that month.
•	Average Daily Revenue: Computed by dividing total revenue by the number of days in the month.
•	Number of Transactions per Day: The average daily transaction count, offering insights into business activity levels.
This high-level aggregation enables efficient monitoring of revenue growth, identification of seasonal fluctuations, and assessment of monthly sales performance trends.

3. EXPLORATORY DATA ANALYSIS (EDA)
   
Summary Analysis

The summary statistics derived from the dataset offer a clear and concise snapshot of the coffee sales performance over the analyzed period. In total, the business generated $106,656.10 in revenue from 3,373 transactions. This figure is further divided between two years, with 2024 accounting for $85,830.80 and 2025 contributing $20,825.30. Such a breakdown not only highlights the overall revenue generation but also sets the stage for understanding year-on-year performance and growth trends. A deeper dive into the payment methods reveals that card transactions overwhelmingly dominate form of payment. Of the 3,373 total transactions, 3,246 were completed by card, resulting in $102,528.10 in revenue at an average of $31.59 per transaction. In contrast, the 127 cash transactions generated $4,128.00 in revenue with an average of $32.50 per transaction. This insight is critical for tailoring payment infrastructure and marketing strategies to the predominant mode of transaction.
Further granularity is evident when examining the sales by coffee type. For instance, the Latte, with 725 transactions, generated $25,797.62 in revenue, positioning it as one of the leading contributors to sales. Similarly, Americano with Milk recorded 782 transactions and contributed $23,867.52 to the overall revenue. These metrics help identify consumer preferences and allow for strategic focus on the most popular and profitable products.Temporal analysis adds another layer of understanding to the sales dynamics. Hourly sales data indicates varying transaction volumes throughout the day, with peak activity generally observed during mid-morning to early afternoon. For example, transaction counts increase from as low as 2 at 06:00 to a peak of over 300 during the mid-day hours. Moreover, when evaluating sales on a daily basis, weekdays such as Tuesday and Monday report higher revenue and transaction volumes compared to other days. Monthly aggregations also highlight fluctuations in revenue, with October 2024 reaching the highest monthly sales of $13,891.16, while other months reflect a more modest performance.
Additional insights are gleaned from specific customer preferences and revenue metrics. The dataset shows that a significant majority of 2,609 customers opted for coffee without milk, while 764 preferred it with milk. Moreover, metrics such as Average Daily Revenue, ranging from $227.43 in March to $448.10 in October 2024, offer a nuanced view of daily performance, and the Year-over-Year (YOY) revenue change indicates a dramatic decline from 2024 to 2025, with a reduction of 75.74% in revenue for the latter period.

Data Visualisation

Data visualization is a crucial step in exploratory data analysis (EDA) as it helps uncover patterns, trends, and outliers that may not be evident in raw data. For this coffee shop sales analysis, I designed interactive dashboards to visually represent key business metrics, transaction patterns, revenue trends, and customer behaviors. By comparing data across different periods and dimensions, we can extract valuable insights into sales performance and customer preferences. The dashboard is divided into two main sections, built using Microsoft Excel for easy data visualization and analysis.

•	Summary Metrics Section

o	Displays key performance indicators (KPIs) such as total revenue, number of transactions, and average sales per transaction.
o	Helps in quickly assessing business performance over different periods.

•	Visual Analytics Section

o	Hourly Sales Chart – Highlights transaction patterns throughout the day.
o	Weekday Sales Chart – Compares sales performance across different days of the week.
o	Monthly Revenue Trend – Shows fluctuations in total sales by month.
o	Seasonal Performance Chart – Illustrates revenue distribution across Fall, Winter, Spring, and Summer.
o	Product Performance Breakdown – Highlights best-selling items per season, helping to identify customer preferences.
The dashboard provides a clear and interactive view of business trends, enabling data-driven decisions for pricing, marketing, and staffing optimization.

5. KEY FINDINGS AND TRENDS

i. Sales Performance
The dashboard provides a high-level summary of total transactions, revenue, and key sales metrics. In 2024, the coffee shop recorded 3,373 total transactions, generating $106,656.10 in total revenue. This translates to an average daily revenue of $304.26, with approximately 9.63 transactions per day. When comparing this to 2025 (so far), we see that the number of transactions in the early months is 680, contributing to $20,825.30 in revenue. Although this is a small sample size, it indicates a 25% growth compared to the same period last year. This suggests an increase in customer engagement or possible seasonal influences that need further exploration.
ii. Product performance and Revenue Contribution
One of the most insightful visualizations in the dashboard is the "Top Products Transactions" and "Revenue by Products" charts, which show the contribution of different coffee types to total sales.

•	Top Products by Transactions:

o	Americano leads with 1,248 transactions, making it the most frequently purchased item.
o	Latte follows with 725 transactions, showing strong customer preference.
o	Cappuccino ranks third with 460 transactions, while Hot Chocolate and Cortado also show significant sales.
o	Espresso, Cocoa, and other specialty drinks have comparatively lower transactions.

•	Revenue Contribution by Product:

o	Americano contributes the highest revenue at $36,016, aligning with its high transaction volume.
o	Latte follows with $25,798, indicating strong revenue per sale.
o	Cappuccino ($16,522), Hot Chocolate ($9,243), and Cortado ($7,457) are other key revenue contributors.
o	Lower revenue drinks such as Espresso ($2,906) and Irish Whiskey Coffee ($353) suggest they are niche preferences rather than high-volume items.
A comparison to the past year shows a consistent demand for Americano and Latte, reaffirming them as staple products. However, the revenue distribution suggests exploring promotional strategies for lower-performing items.
iii. Sales Pattrns Across Time
Understanding when customers purchase coffee helps optimize business operations. Various visualizations in the dashboard highlight hourly, daily, weekly, and seasonal sales patterns.

•	Hourly Transactions:

o	Sales peak in the afternoon (12 PM - 5 PM), making it the busiest period of the day. This suggests that many customers prefer coffee later in the day, possibly for a post-lunch energy boost or afternoon meetings.
o	The morning rush (6 AM - 11 AM) sees strong sales but remains lower than the afternoon peak. While morning coffee is traditionally popular, the data suggests that afternoon demand is even higher. This could indicate an opportunity to introduce promotional morning deals to attract more customers earlier in the day.
o	Evening sales (6 PM - closing) drop significantly, reflecting a reduced demand for coffee at night. This insight can help the business decide whether to adjust operating hours, reduce staff during late hours, or introduce special promotions to attract evening customers.

•	Weekday Transactions:

o	The highest sales occur on Tuesday (547 transactions), followed by Monday (524 transactions). This suggests that coffee demand remains strong at the start of the week, possibly due to work routines and a need for an energy boost.
o	Wednesday (440 transactions) and Thursday (472 transactions) experience a slight dip, indicating midweek slowdowns. To counter this, targeted promotions such as “Midweek Discounts” or “Buy One, Get One Free” deals could help increase sales on these days.
o	Friday Saturday and Sunday transactions are relatively stable, showing that coffee demand is not significantly affected by the shift from workdays to weekends.

•	 Monthly Revenue Trends: 

o	Revenue fluctuates across the year, peaking in October and November, possibly due to seasonal demand.
o	Comparing revenue from March 2024 to February 2025, sales in the latter months show an upward trend.

•	Seasonal Revenue Trends:

Fall (1,029 Transactions, $32,470.34 Revenue – Highest Sales Season)
o	Americano (339) and Latte (282) dominate sales, contributing significantly to Fall’s revenue peak.
o	Hot Chocolate (106) and Cappuccino (111) also perform well, aligning with seasonal preferences for warm beverages.
o	The high number of transactions and premium-priced drinks (like Americano, Latte, and Hot Chocolate) justify Fall’s revenue leadership.
Winter (939 Transactions, $29,063.04 Revenue – Strong Coffee Season)
o	Americano (363) remains the top seller, followed by Latte (142).
o	Diverse product selection, including Irish Whiskey (13), Mochaccino (3), and Super Chocolate (1), suggests holiday-inspired drinks boost sales.
o	Despite fewer transactions than Fall, Winter still maintains high revenue, indicating premium-priced drinks contribute significantly.
Spring (669 Transactions, $22,834.18 Revenue – Moderate Sales Decline)
o	Americano (253) and Latte (137) remain strong, but sales volume drops compared to Fall and Winter.
o	Cappuccino (118) holds steady, but Hot Chocolate (49) and Cocoa (21) see a noticeable decline, likely due to warmer weather.
o	Lower demand for warm drinks correlates with the seasonal revenue dip.
Summer (736 Transactions, $22,288.54 Revenue – Highest Transactions, Lowest Revenue)
o	Despite the higher number of transactions compared to Spring, Summer generates the lowest revenue.
o	Americano (293) and Latte (164) lead sales, but Cocoa (25), Hot Chocolate (31), and Espresso (38) have minimal demand, reinforcing a shift toward colder, lower-priced beverages.
o	Lower revenue per transaction suggests customers opt for iced coffee or cold drinks, which may be priced lower than warm beverages.
iv. Customer Behaviour and Preferences
The dashboard also provides key insights into customer preferences and spending behavior, which can inform marketing and loyalty strategies.

•	Milk Preference:

o	23% of transactions involve milk-based coffee, while 77% of sales are black coffee or other non-milk beverages.
o	Understanding this ratio can help with inventory management and menu optimization.
•	Mode of Payment:
o	96% of transactions are done via card, while only 4% are cash payments.
o	This aligns with modern consumer trends favoring digital payments, reinforcing the need for seamless card-based transactions.
•	Top Customers Contribution:
o	The dashboard highlights the top 10 highest-paying customers, with Customer ID 0012 contributing $3,785.92, followed by ID 0141 at $2,749.78.
o	The average revenue per top customer is around $1,900, suggesting a strong base of repeat buyers.
o	Focusing on customer retention and personalized offers for these high-value customers could boost revenue further.
7. Yearly Comparison and Growth Trends
The comparison of revenue and transaction growth over time provides a snapshot of business performance.

•	Transactions Growth:

o	In 2024, there were 2,693 transactions, while early 2025 has recorded 680 transactions so far.
o	The 25% growth rate compared to the previous year indicates an upward trajectory.
•	Revenue Growth:
o	Revenue from 2024 stood at approximately $106,656.10, while 2025’s early months have already generated $20,825.30.
o	A 24% increase in revenue year-over-year suggests rising demand or improved pricing strategies.
These figures suggest a positive trajectory for the coffee shop, with increasing transactions and revenue.

5. ACTIONABLE BUSINESS STRATEGIES

Based on the analyzed data and visualized trends, the following actionable strategies can be implemented to optimize sales, improve customer retention, and increase revenue for the coffee shop.

a. Optimize Pricing & Promotions

•	Midweek Discounts: Sales drop on certain weekdays (e.g., Wednesday). Offering "Midweek Specials" or "Buy One, Get One Free" (BOGO) deals can help boost transactions.
•	Monday and Tuesday Rewards: With Monday and Tuesday being the busiest weekdays, introducing a "Monday and Tuesday Rewards" program—where repeat customers get a discount for visiting again later in the week—can encourage more frequent visits.
•	Seasonal Promotions: Fall and Winter generate the highest revenue. Capitalizing on these high-demand seasons with premium product offerings and exclusive deals (e.g., limited-edition flavors, bundled discounts) can further drive sales.
•	Boosting Sales in Low-Revenue Months: Since revenue dips in Spring and Summer, strategic promotions such as happy hours, iced coffee discounts, or limited-time cold brew specials can help maintain steady transactions.
•	Loyalty Rewards: The top 10 customers significantly contribute to total revenue. Implementing a tiered rewards program to encourage repeat visits can strengthen customer loyalty.

b. Improve Staffing Efficiency

•	Peak Hour Scheduling: Transactions peak in the afternoon (12 PM - 5 PM), followed by morning (6 AM - 11 AM). Ensuring more staff availability during these hours will improve service speed and customer satisfaction.
•	Weekend & Monday Preparedness: High sales on Tuesdays and Mondays suggest a strong demand at the start of the week. Adequate stock and staffing should be ensured to accommodate the rush.

c. Product and Menu Optimization

•	Expand Best-Selling Products: Americano and Latte consistently drive the highest revenue across seasons. More variations (e.g., flavored lattes, specialty Americanos) could attract more customers.
•	Upselling Strategies: Since high-revenue items include Americano, Latte, and Cappuccino, bundling them with complementary items (e.g., pastries) can increase the average transaction value.
•	Introduce Seasonal Beverages: Fall and Winter generate the highest revenue. Limited-time seasonal drinks (e.g., pumpkin spice in Fall, peppermint mocha in Winter) could further drive sales.
•	Enhancing Summer Offerings: Since Summer has more transactions but lower revenue, introducing higher-priced iced coffee varieties and premium cold drinks could improve overall profitability.

d. Enhance Payment Options for Higher Sales

•	Mobile Payment Integration: Implementing mobile payment options like Apple Pay, Google Pay, or a dedicated coffee shop app could streamline transactions and enhance customer experience.
e. Customer Engagement & Retention Strategies
•	Targeted Marketing for Top Customers: Since a small group of loyal customers generates a significant portion of revenue, personalized offers (e.g., birthday discounts, exclusive deals) could boost retention.
•	Subscription-Based Coffee Plans: Since many people grab coffee on their way to work, offering subscription-based morning coffee plans or partnering with nearby offices could provide a steady stream of sales and build long-term customer loyalty.
•	Workplace Partnerships: Collaborating with corporate offices for bulk coffee orders or morning delivery services can increase daily transactions.
By implementing these data-driven strategies, the coffee shop can maximize sales, optimize costs, and improve customer satisfaction, leading to sustainable business growth.

7. CONCLUSION AND FUTHER RESEARCH

The data analysis highlights key trends in customer behavior, seasonal revenue fluctuations, and product performance, providing actionable insights for optimizing sales and operational efficiency. Peak sales periods, such as Fall and Winter, present opportunities for premium offerings, while lower-revenue seasons like Spring and Summer require strategic promotions to maintain stability. Additionally, high weekday transactions on Monday and Tuesday suggest a strong start to the week, which can be leveraged through targeted rewards programs.
To further refine business strategies, additional research could be conducted in the following areas:
•	Customer Preferences & Satisfaction: Gathering direct customer feedback through surveys or loyalty program interactions can help tailor promotions and menu offerings.
•	Competitor Benchmarking: Analyzing pricing, promotions, and product trends of competitors could provide insights into potential gaps and opportunities.
•	Impact of External Factors: Investigating how weather, holidays, or local events affect sales could help in planning better inventory and promotional strategies.
•	Optimizing Product Pricing: Evaluating whether pricing adjustments—especially for popular beverages like Americanos and Lattes—could enhance profitability without affecting demand.
•	Advanced Sales Forecasting: Implementing predictive analytics models can improve decision-making regarding inventory management and staffing.
By continuously analyzing data and adapting business strategies accordingly, the coffee shop can enhance revenue, improve customer retention, and maintain a competitive edge in the market.


