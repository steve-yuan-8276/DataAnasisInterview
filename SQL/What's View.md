# What is View?

In SQL, a view is a virtual table that is based on the result of a SELECT query. Unlike a physical table, a view doesn't store data itself but rather provides a way to represent the result of a query as if it were a table. Views can be used to simplify complex queries, encapsulate business logic, and restrict access to specific columns or rows.

**Creating a View in SQL:**
To create a view in SQL, you can use the CREATE VIEW statement followed by a SELECT query that defines the structure and data to be included in the view.

**Example:**
```sql
-- Creating a view to display information about high-value customers
CREATE VIEW HighValueCustomers AS
SELECT 
    CustomerID,
    FirstName,
    LastName,
    TotalPurchases
FROM Customers
WHERE TotalPurchases > 1000;
```

In this example:
- `HighValueCustomers` is the name of the view.
- The SELECT statement defines the structure of the view and the criteria for selecting data.
- The view includes only the specified columns (CustomerID, FirstName, LastName, TotalPurchases) and rows where TotalPurchases exceed 1000.

Once a view is created, it can be queried like a regular table:

```sql
-- Querying the view
SELECT * FROM HighValueCustomers;
```

Views provide a layer of abstraction, allowing users to interact with the data in a more structured and controlled manner without directly accessing the underlying tables. They are particularly useful for simplifying complex queries, enforcing security, and promoting a modular approach to database design.


Example：

Assuming there are two tables, one of which is the "customer" table with a primary key of "customer_id", including the following content:

- address_id (MUL, smallint)
- create_date (datetime)
- customer_id (PRI, smallint)
- email (varchar, nullable)
- first_name (varchar)
- last_name (MUL, varchar)
- last_update (timestamp, CURRE
- store_id (MUL, tinyint)

The second table is "rental", with the primary key being "rental_id". It includes the following content:

customer_id (MUL, smallint)
inventory_id (MUL, mediumint)
last_update (timestamp, CURREl rental_date (MUL, datetime)
rental_id (PRI, int)
return_date (datetime, nullable)
staff_id (MUL, tinyint)

The final query should include all customer information and a column showing the average difference in days between return_date and rental_date, grouped by customer. Segment customers into three groups based on their return times: "GOOD" for those who return (on average) within a week after rental, "FAIR" for those who return within 30 days, and "BAD" for those who take more than 30 days. For the rentals, please only use data from 2005 onwards.

```sql
# Create a view to return the difference between return date and rental date for each movie rental

CREATE VIEW rental_return_times AS
SELECT
 rental_id,
 customer_id,
 rental_date,
 DATEDIFF(IF(ISNULL(return_date), CURRENT_DATE, return_date), rental_date) AS rental_days
FROM rental;

# Create a view to obtain the average movie return time of each customer

CREATE VIEW customer_avg_return_times AS
SELECT
 customer_id,
 AVG(rental_days) AS avg_rental_days
 FROM rental_return_times
WHERE
 YEAR(rental_date) >= 2005
GROUP BY customer_id;

# Create a view from the query that feeds the customer dashboard

Create view customer_dashborad as
SELECT
 c.*,
 CASE
  WHEN ca.avg_rental_days <= 7 THEN 'GOOD'
  WHEN ca.avg_rental_days > 7 AND ca.avg_rental_days <= 30 THEN 'FAIR'
  ELSE 'BAD'
  END AS customer_category
FROM
 customer c INNER JOIN customer_avg_return_times ca
 ON ca.customer_id = c.customer_id;
 ```
