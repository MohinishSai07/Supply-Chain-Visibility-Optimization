# Supply Chain Visibility and Optimization - Milestone 2

## Objective

The objective of Milestone 2 is to develop interactive Inventory Analytics and Delivery Performance dashboards in Power BI to monitor inventory performance, analyze delivery efficiency, and support business decision-making using DAX measures and KPIs.

## Inventory Turnover Calculation Approach

The Inventory Turnover Ratio is used to measure how efficiently inventory is utilized. DAX measures were created to analyze inventory movement based on inventory quantity and sales data. This helps identify inventory utilization and stock movement trends.

## Slow-Moving and Fast-Moving Inventory Identification Logic

Inventory items were categorized based on stock movement and inventory status.

- Fast-moving products are identified by higher sales and inventory movement.
- Slow-moving products are identified by lower inventory movement.
- Dead stock products are identified separately using the stock status.

## Delivery Performance Analysis Methodology

The Delivery Performance dashboard evaluates shipment efficiency using key performance indicators such as:

- On-Time Delivery Percentage
- Late Delivery Percentage
- Advance Shipping Percentage
- Late Delivery Risk
- Delivery performance by region
- Delivery performance by shipping mode
- Delivery trends over time

## DAX Measures and KPIs

The following DAX measures and KPIs were created to support dashboard analysis:

- Total Sales = sum(Fact_table[sales])
- Order Count = DISTINCTCOUNT(Fact_table[order_id])
- Inventory Turnover Ratio = DIVIDE([Total Sales],[Avg Inventory Value],0)
- Slow Moving Quantity = CALCULATE(SUM(Fact_table[stock_qty]), Fact_table[Stock Status]="Slow-Moving")
- Dead Stock Quantity =  CALCULATE(SUM(Fact_table[stock_qty]), Fact_table[Stock Status]="Dead Stock")
- On-Time Delivery Percentage = DIVIDE( CALCULATE(DISTINCTCOUNT(Fact_table[order_id]), Fact_table[delivery_status]="Shipping on Time"), [Total Orders],0)
- Late Delivery Percentage = DIVIDE( CALCULATE(DISTINCTCOUNT(Fact_table[order_id]), Fact_table[delivery_status]="Late Delivery" ), [Total Orders],0)
- Advance Shipping Percentage = DIVIDE( CALCULATE(DISTINCTCOUNT(Fact_table[order_id]), Fact_table[delivery_status]="Advance Shipping" ), [Total Orders],0)
- Late Delivery Risk Percentage = DIVIDE([Total Risk Flagged Orders],[Total Orders],0)

## Dashboard Overview

### Inventory Analytics Dashboard

- Inventory performance by warehouse
- Inventory performance by product category
- Inventory trend analysis
- Stock quantity and reorder level analysis
- Slow-moving and dead stock analysis

### Delivery Performance Dashboard

- On-time vs Late delivery analysis
- Delivery performance by region
- Delivery performance by shipping mode
- Delivery trend analysis
- Late delivery risk monitoring

## Key Insights

- Inventory performance varies across warehouses and product categories.
- Slow-moving inventory can increase storage and operational costs.
- Inventory trend analysis helps improve stock planning.
- Delivery performance differs across regions and shipping methods.
- Monitoring delivery KPIs helps improve customer satisfaction.

## Business Recommendations

- Maintain optimal inventory levels using reorder planning.
- Reduce slow-moving and dead stock through better inventory management.
- Improve warehouse inventory distribution.
- Focus on regions with higher late delivery rates.
- Optimize shipping methods to improve on-time deliveries.
- Continuously monitor KPIs to support business decision-making.

## Tools Used

- Power BI Desktop
- Power Query
- DAX (Data Analysis Expressions)
- GitHub
