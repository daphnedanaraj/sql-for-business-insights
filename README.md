# Sales Commission Analysis using SQL

## Overview

This project demonstrates SQL skills by analyzing a sales commission dataset. The dataset is generated using Python in a Jupyter notebook and uploaded to Google BigQuery for analysis. In this project, I focus on querying data related to sales performance and commission distribution across different salespeople. The key insights drawn from the analysis help in evaluating the performance of salespeople and making business recommendations.

## Project Structure

- **`mock_data.ipynb`**: Jupyter notebook that generates the mock sales data using Python and saves it as CSV files for uploading to BigQuery.
- **`images/q1.png`**: Screenshot of the SQL query output displaying the total commission earned by each salesperson.
- **`README.md`**: Documentation of the project, including SQL queries, insights, and recommendations.

## SQL Query: Total Commission Earned by Each Salesperson

This query calculates the total commission earned by each salesperson:

```sql
SELECT 
    sp.salesperson_id,
    sp.first_name,
    sp.last_name,
    SUM(co.commission_amount) AS total_commission
FROM `regal-bonito-467416-p3.edtech.commissions` co
JOIN `regal-bonito-467416-p3.edtech.salespersons` sp ON co.salesperson_id = sp.salesperson_id
GROUP BY sp.salesperson_id, sp.first_name, sp.last_name
ORDER BY total_commission DESC;

## Query Output

Below is a screenshot showing the query output with the total commission earned by each salesperson:

![Total Commission Output](./images/q1.png)

## Insights

### Top Performers:
- **Mindy Sutton** earned the highest commission ($70,070), followed by **Steven Price** ($68,168) and **Jessica Stewart** ($66,468).
- The **lowest performer** in this query is **Colleen Bailey** with $61,731 in commissions.

### Commission Distribution:
- The total commissions for the top 5 salespeople have a relatively small range between them, suggesting a balanced performance across the team.

### Business Recommendations:
1. **Recognize Top Performers**: Reward Mindy Sutton and Steven Price for their exceptional performance.
2. **Support for Lower Performers**: Colleen Bailey could benefit from additional training or mentorship to help improve sales and commission.
3. **Incentive Programs**: Consider implementing an incentive program to encourage consistent performance across the team.
