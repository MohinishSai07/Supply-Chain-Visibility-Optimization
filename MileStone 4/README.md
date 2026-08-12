# Supply Chain Visibility and Optimization - Milestone 4

## Objective

Milestone 4 focuses on developing Warehouse Efficiency and Executive Dashboards using Power BI to analyze warehouse operations and provide an executive-level overview of supply chain performance.

## Warehouse Utilization Methodology

Warehouse efficiency was analyzed using total, average, maximum, and minimum warehouse utilization. Warehouse capacity, stock levels, units shipped, and order volumes were also compared to evaluate operational efficiency.

## Throughput and Productivity

Warehouse productivity was evaluated using:

* Order Count = DISTINCTCOUNT(Fact_table[order_id])
* Warehouse Units Shipped = SUM(Fact_table[order_item_quantity])
* Total Sales = SUM(Fact_table[sales])

These KPIs help compare warehouse throughput and identify high- and low-performing warehouses.

## Executive Dashboard Methodology

The Executive Dashboard consolidates important KPIs from previous milestones, including orders, fulfillment, warehouses, suppliers, dead stock, delivery performance, inventory turnover, reliability, and sales trends.

Interactive slicers and time-based visuals allow users to analyze performance across markets, categories, regions, and dates.

## Forecasting Approach

Monthly sales trends were analyzed using Power BI time-series visualizations to identify historical patterns and support future business planning.

## DAX Measures Used

Total Warehouses = DISTINCTCOUNT(Fact_table[warehouse_name])

Max Utilization % = MAXX(VALUES(Fact_table[warehouse_name]), CALCULATE(AVERAGE(Fact_table[utilization_%])))

Min Utilization % = MINX(VALUES(Fact_table[warehouse_name]), CALCULATE(AVERAGE(Fact_table[utilization_%])))

Avg Utilization % = AVERAGE(Fact_table[utilization_%])

Warehouse Units Shipped = SUM(Fact_table[order_item_quantity])

Units per Order (Warehouse) = DIVIDE([Warehouse Units Shipped],[Order Count],0)

## Dashboard Optimization

* Reusable DAX measures were used for KPI calculations.
* Interactive slicers were implemented.
* Appropriate aggregations were used for visuals.
* Dashboards were organized into KPI and analysis sections.
* Meaningful titles and labels were applied for better usability.

## Key Insights

* Warehouse utilization varies across locations.
* Warehouse throughput differs based on order and shipment volumes.
* Comparing capacity and stock helps identify storage efficiency issues.
* Executive KPIs provide a consolidated view of supply chain performance.
* Sales trends support better planning and decision-making.

## Business Recommendations

* Monitor highly utilized warehouses and optimize capacity.
* Improve utilization of underused warehouses.
* Optimize inventory allocation based on demand and capacity.
* Monitor warehouse productivity and throughput regularly.
* Use executive KPIs and sales trends for data-driven supply chain planning.

## Tools Used

* Power BI Desktop
* Power Query
* DAX
* Microsoft Excel
* GitHub
