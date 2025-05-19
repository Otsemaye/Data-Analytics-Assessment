# Data-Analytics-Assessment

This project includes SQL solutions to four real-world data analysis tasks designed to uncover customer behavior patterns and financial insights for a savings and investment platform. Each task explores different business questions using SQL techniques such as joins, aggregations, date functions, and CTEs.

Question 1: 
Approach:
Use subqueries to separately count savings and investment plans.
Join with the users table to extract customer details.
Aggregate total deposits and sort the results.

Challenges:
Ensuring that only users with **both types of plans** were selected required multiple conditional joins.
Used `IFNULL` to handle missing deposit values and prevent nulls from distorting the total.

Question 2:
Approach:

Use a CTE to count confirmed monthly transactions per user.
Calculate the average transaction frequency.
Use a `CASE` expression to assign frequency categories.
Aggregate users by category.

Challenges:
Required careful handling of time-based grouping to ensure accuracy.
Used `FIELD()` in `ORDER BY` to ensure consistent display of categories.

Question 3: 
Approach:

Create a CTE for active plans (not deleted, approved status).
Use a `LEFT JOIN` to include accounts with no transactions.
Calculate inactivity using `DATEDIFF` from the last transaction date.
Assign default values to handle nulls.

Challenges:
Avoided excluding truly inactive accounts by using a `LEFT JOIN` and default values like `'1900-01-01'` for missing dates.
Ensured robust grouping and accurate inactivity computation, even when no transactions existed.

Question 4:
Approach:

Calculate account tenure in months from the signup date.
Count total transactions and compute average profit.
Apply a simplified CLV formula:
  `(Total Transactions / Tenure) × 12 × Avg. Profit per Transaction`
Use rounding and NULL safety measures.

Challenges:

Used `NULLIF` to errors for new users with 0-month tenure.
Balanced simplicity and realism in the CLV formula, acknowledging assumptions.
Ensured inactive or low-activity users were still represented via `LEFT JOIN`.
