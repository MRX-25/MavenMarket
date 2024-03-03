# MavenMarket
Maven Market Toys Data Analysis

### Problem Statements 

### Identifying Profitable Product Categories:

Determine which product categories are driving the most profits for Maven Toys.
Analyze the sales data to identify the top-performing product categories based on revenue generated.
Investigate whether the profitability of product categories varies across different store locations.
### Analyzing Seasonal Trends:

Explore the sales data to identify any seasonal trends or patterns.
Determine if there are specific months or seasons where sales tend to be higher or lower.
Visualize the seasonal trends using line charts or other appropriate visualizations to understand any recurring patterns.
### Addressing Out-of-Stock Issues:

Investigate whether sales are being lost due to out-of-stock products at certain store locations.
Identify which products frequently experience stockouts and assess the impact on sales.
Analyze the relationship between stock levels and sales performance to determine if there is a correlation.
### Inventory Management and Cash Flow:

Estimate the amount of money tied up in inventory at the toy stores.
Calculate the inventory turnover rate to assess how quickly inventory is moving.
Determine how long the current inventory levels will last based on sales trends and turnover rate.
Provide insights into optimizing inventory management to improve cash flow and minimize excess inventory.
### Dashboard Design and Interactivity:

Create an interactive dashboard in Power BI to visualize the key metrics and insights derived from the data analysis.
Design visually appealing and informative visualizations that effectively communicate the findings.
Ensure the dashboard is user-friendly and allows users to easily explore different aspects of the sales and inventory data.
Provide filters and slicers to enable users to drill down into specific product categories, store locations, or time periods for deeper analysis.



### Steps followed 


Step 1: Load the Maven Toys sales and inventory data into Power BI Desktop. The dataset is provided as a CSV file.

Step 2: Open the Power Query Editor and enable column distribution, column quality, and column profile options under the View tab in the Data preview section.

Step 3: Ensure that column profiling is based on the entire dataset to get a comprehensive overview of the data.

Step 4: Check for errors and empty values in the dataset. Identify any columns with significant issues, if any.

Step 5: Analyze the "Arrival Delay" column. Determine how to handle null values, considering that less than 1% of values are null. Decide whether to exclude null values when calculating average delay time.

Step 6: In the report view, select a suitable theme for the dashboard to ensure visual consistency.

Step 7: Add visualizations to represent various aspects of the Maven Toys sales and inventory data. For example, use bar charts, line charts, or scatter plots to visualize sales trends, inventory levels, or profit margins.

Step 8: Add visual filters (Slicers) for relevant fields such as product categories, store locations, or transaction dates to enable users to filter and analyze the data interactively.

Step 9: Include key metrics such as average departure delay and average arrival delay in minutes using card visuals. Utilize visual level filters to exclude null values from consideration in the average calculation.

Step 10: Create additional visuals to represent customer satisfaction levels, product ratings, or sales performance metrics. Use appropriate visualization types such as pie charts or stacked bar charts to effectively convey the information.

Step 11: for creating new column Cumulative Average following DAX expression was written

Cumulative Average = 
    AVERAGEX(
        FILTER(
            ALL(sales),
            sales[Date] <= MAX(sales[Date])
        ),
        sales[Unit Sold]
    )


Step 12: for creating new ProfitMargin column  following DAX expression was written

ProfitMargin = DIVIDE([TotalProfit], [Total_Revenue], 0) * 100

Step 13: for creating new QuantitySold column following DAX expression was written

QuantitySold = SUM('sales'[Units])

Step 14: for creating new Sell_price column following DAX expression was written

Sell_price = sales[Units] * RELATED(products[Product_Price])

Step 15: for creating new Total_Revenue column following DAX expression was written

Total_Revenue = SUMX('Sales', 'Sales'[Units] * RELATED('products'[Product_Price]))



Step 16: for creating new TotalProfit column following DAX expression was written

TotalProfit = SUMX('sales', 'sales'[Units] * ('sales'[Sell_price] - RELATED('products'[Product_Cost]))
)

Step 17: for creating new TotalSales column following DAX expression was written


TotalSales = [Total_Revenue]




Step 18: for creating new Unit Sold column following DAX expression was written

Unit Sold = SUM('sales'[Units])

Step 19: for creating new Product_Offer column following DAX expression was written

Product_Offer = COUNTROWS(VALUES('products'[Product_ID]))

Step 20: for creating new OutofStockQuantity column following DAX expression was written


OutofStockQuantity = 
CALCULATE(
    SUM('inventory'[Stock_On_Hand]),
    'inventory'[Stock_On_Hand] <= 0
)


Step 21: for creating new RemainingInventory column following DAX expression was written

RemainingInventory = 
SUM('inventory'[Stock_On_Hand]) - SUM('sales'[QuantitySold])




### Report 


### Introduction:
Maven Toys, a fictitious chain of toy stores in Mexico, collects sales and inventory data to analyze its business operations, identify opportunities for growth, and optimize inventory management. This report provides an overview of the sales and inventory data analysis conducted for Maven Toys.

### Data Overview:
The dataset includes information about products, stores, daily transactions, and current inventory levels at each location. It contains the following key fields:

### Product ID
### Product Name
### Category
### Store ID
### Store Location
### Transaction Date
### Transaction ID
### Sales Revenue
### Quantity Sold
### Inventory Level
### Arrival Delay
### Customer Satisfaction



### Analysis Summary:

Product Categories and Profitability:

The analysis revealed that certain product categories, such as Action Figures and Board Games, drive the highest profits for Maven Toys.
Profitability varies across store locations, with some stores performing better in specific product categories than others.
Seasonal Trends:

Seasonal trends were identified in the sales data, with higher sales volumes observed during holiday seasons and special events.
Maven Toys can capitalize on these seasonal trends by adjusting inventory levels and marketing strategies accordingly.
Out-of-Stock Products:

Analysis showed that out-of-stock products negatively impact sales, leading to potential revenue loss.
Maven Toys should focus on optimizing inventory management to minimize stockouts and improve customer satisfaction.
Inventory Management and Cash Flow:

The report estimated the amount of money tied up in inventory at Maven Toys stores and assessed inventory turnover rates.
Insights were provided on optimizing inventory levels to improve cash flow and minimize excess inventory.
Recommendations:
Based on the analysis, the following recommendations are suggested for Maven Toys:

Implement targeted marketing strategies to promote high-profit product categories.
Enhance inventory forecasting techniques to prevent stockouts and improve sales performance.
Optimize inventory levels based on seasonal demand patterns to maximize revenue opportunities.
Invest in customer satisfaction initiatives to mitigate the impact of out-of-stock products on sales.
Conclusion:
The analysis of Maven Toys sales and inventory data provides valuable insights into the company's performance and opportunities for improvement. By leveraging these insights, Maven Toys can make informed business decisions to drive growth, enhance customer satisfaction, and optimize operations.
