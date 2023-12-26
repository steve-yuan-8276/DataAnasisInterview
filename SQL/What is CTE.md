# Common Table Expression (CTE)

A Common Table Expression (CTE) is a temporary result set defined within the execution scope of a SELECT, INSERT, UPDATE, or DELETE statement in SQL. CTEs are similar to derived tables or subqueries but are defined using the WITH clause at the beginning of a query. They provide a concise and readable way to break down complex queries into more manageable and modular components.

**How to Use CTE:**
To use a CTE, you typically follow these steps:

1. **Define the CTE using the WITH clause:**
   ```sql
   WITH CTE_name (column1, column2, ...) AS (
       -- Your CTE query goes here
   )
   ```

2. **Write the main query, referencing the CTE as if it were a table:**
   ```sql
   SELECT * FROM CTE_name;
   ```

**Example:**
```sql
-- Defining a CTE to get high-value customers
WITH HighValueCustomers AS (
    SELECT 
        CustomerID,
        FirstName,
        LastName,
        TotalPurchases
    FROM Customers
    WHERE TotalPurchases > 1000
)

-- Using the CTE in the main query
SELECT * FROM HighValueCustomers;
```

In this example:
- `HighValueCustomers` is the name of the CTE.
- The CTE is defined to select specific columns from the `Customers` table where `TotalPurchases` exceed 1000.
- The main query then selects all columns from the CTE.

CTEs are particularly useful when a query involves multiple steps or when the same subquery needs to be referenced multiple times within a larger query. They enhance the readability and maintainability of SQL code by breaking it into logical sections.

It's important to note that the CTE is only valid for the duration of the query in which it is defined. Once the query execution is complete, the CTE is discarded, making it suitable for temporary and modular data manipulations within a query.
