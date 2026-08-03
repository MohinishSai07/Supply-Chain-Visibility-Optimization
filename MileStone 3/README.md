# Supply Chain Visibility and Optimization - Milestone 3

## Objective

The objective of Milestone 3 is to develop Supplier Performance and Transportation Analytics dashboards using Power BI. The dashboards help evaluate supplier performance, monitor transportation efficiency, and support business decision-making through interactive visualizations and DAX measures.

## Supplier Scorecard Calculation Methodology

The Supplier Scorecard was developed using key supplier performance metrics, including:

- Total Suppliers
- Average Quality Score
- Average Reliability Percentage
- Average Lead Time (Days)
- Products Supplied
- Orders Fulfilled

## Supplier Ranking and Benchmarking Approach

Suppliers were ranked using the Supplier Composite Score calculated through DAX measures.

The suppliers were classified into the following performance tiers:

- High Reliability
- Medium Reliability
- Low Reliability

## Transportation Cost Analysis Methodology

Transportation performance was analyzed using the following Key Performance Indicators (KPIs):

- Average Profit Per Order
- Total Discount Given
- Average Discount Rate
- Same Day Share Percentage
- Late Rate by Shipping Mode

## Route and Carrier Performance Evaluation

Transportation performance was evaluated by analyzing:

- Shipping Mode Performance
- Order Region Performance
- Market-wise Transportation Analysis
- Delivery Performance
- Transportation Cost Distribution

## DAX Measures Used

### Supplier Performance

Total Suppliers =
DISTINCTCOUNT(Dim_supplier[supplier_name])

Avg Quality Score =
AVERAGE(Dim_supplier[quality_score])

Avg Reliability % =
AVERAGE(Dim_supplier[reliability_%])

Avg Lead Time (Days) =
AVERAGEX(
    VALUES(Dim_supplier[supplier_name]),
    CALCULATE(
        AVERAGE(Dim_supplier[lead_time_(days)])
    )
)

Products Supplied =
DISTINCTCOUNT(Dim_supplier[product_card_id])

Orders Fulfilled (Proxy) =
CALCULATE(
    DISTINCTCOUNT(Fact_table[order_id]),
    Fact_table[order_status] IN {"COMPLETE","CLOSED"}
)

Reliability Tier =
SWITCH(
    TRUE(),
    Dim_supplier[reliability_%] >= 80,"High",
    Dim_supplier[reliability_%] >= 50,"Medium",
    "Low"
)

Supplier Composite Score =
(Dim_supplier[quality_score] * 0.4)
+ (Dim_supplier[reliability_%] * 0.4)
+ (((30 - Dim_supplier[lead_time_(days)]) / 30) * 100 * 0.2)

Supplier Rank =
RANKX(
    ALL(Dim_supplier),
    Dim_supplier[Supplier Composite Score],
    ,
    DESC
)

### Transportation Analytics

Avg Profit Per Order =
AVERAGE(Fact_table[order_profit_per_order])

Total Discount Given =
SUM(Fact_table[order_item_discount])

Avg Discount Rate =
AVERAGE(Fact_table[order_item_discount_rate])

Same Day Share % =
DIVIDE(
    CALCULATE(
        DISTINCTCOUNT(Fact_table[order_id]),
        Fact_table[shipping_mode] = "Same Day"
    ),
    [Total Orders],
    0
)

Late Rate by Shipping Mode =
CALCULATE(
    [Late Delivery %],
    ALLEXCEPT(
        Fact_table,
        Fact_table[shipping_mode]
    )
)

## Key Insights

- Supplier performance varies based on quality, reliability, and lead time.
- Composite score and supplier ranking help identify the best-performing suppliers.
- Transportation performance differs across shipping modes.
- Discount strategies directly impact overall profitability.
- Monitoring late delivery rates helps improve logistics planning and customer satisfaction.

## Business Recommendations

- Strengthen partnerships with high-performing suppliers.
- Improve supplier quality and reliability through regular performance monitoring.
- Optimize transportation routes to reduce delivery delays.
- Review discount strategies to maximize profitability.
- Continuously monitor KPIs for better supply chain decision-making.

## Tools Used

- Power BI Desktop
- Power Query
- DAX (Data Analysis Expressions)
- Microsoft Excel
- GitHub
