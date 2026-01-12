# Adventure Works Retail Sales Analysis
## Transforming Global Sales Data into Strategic Business Intelligence
This repository contains the complete analysis for the Adventure Works project. Using a combination of PostgreSQL and Power BI, I transformed raw transactional data into actionable insights focused on customer segmentation, product performance, and operational efficiency.

## Key Insights
- Customer Spending: Identified high-value customers with total spend exceeding $10,000 for targeted retention.
- Returns Analysis: Isolated the Top 10 returned products to identify potential quality control issues and revenue loss.
- Regional Growth: Analyzed purchase activity across the US, Canada, and Australia to drive regional marketing strategy.
- Targeted Outreach: Extracted an email list of the Top 50 customers of 2022 based on total revenue.

## Tools Used
- Microsoft Excel: Initial data cleaning and preparation.
- PostgreSQL: Structured data querying and view creation.
- Power BI: Interactive data modeling and dashboard development.

## Analytical Highlight (SQL)
To support the marketing team’s goal of high-value retention, I developed the following query to identify top-tier customers:

```sql
-- Identifying Top 50 revenue-generating customers for 2022
CREATE VIEW top50_customers_2022 AS
SELECT
    c.emailaddress,
    SUM(p.productprice * ts.orderquantity) revenue
FROM customer c
JOIN totalsales ts ON c.customerkey = ts.customerkey
JOIN product p ON ts.productkey = p.productkey
WHERE ts.orderdate >= '2022/01/01'
GROUP BY c.emailaddress
ORDER BY revenue DESC
LIMIT 50;
```
## Repository Structure
- Project Management: Project Brief and problem statement.
- Scripts: SQL queries answering 15 business-driven questions.
- Analysis: Power BI dashboard file (.pbix) and exported visuals.
- Sent to Client: Final presentation slides summarizing findings and recommendations.
