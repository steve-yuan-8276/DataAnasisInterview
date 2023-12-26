# What is Subquery

A subquery, also known as a nested query or inner query, is a query nested within another query. It's enclosed within parentheses and is used to retrieve data that will be used by the main query. A subquery can be employed in various parts of a SQL statement, such as the SELECT clause, FROM clause, WHERE clause, or HAVING clause. The result of the subquery is then used as input for the main query.

**Example of a Subquery:**
```sql
SELECT FirstName, LastName
FROM Customers
WHERE CustomerID IN (SELECT CustomerID FROM Orders WHERE TotalAmount > 1000);
```

In this example, the subquery `(SELECT CustomerID FROM Orders WHERE TotalAmount > 1000)` retrieves a list of customer IDs meeting a certain condition, and the main query then selects the corresponding customer names from the `Customers` table.

**Difference Between Subquery and CTE:**
- **Temporary Nature:**
  - Subquery: Part of the main query, providing a one-time result set for that specific execution.
  - CTE: Defined using the WITH clause, offering a named, temporary result set for the duration of the entire query.

- **Reference in Main Query:**
  - Subquery: Embedded within the WHERE clause or other parts of the main query.
  - CTE: Referenced in the main query as if it were a table or view.

- **Readability and Modularity:**
  - Subquery: Can make the main query less readable and harder to maintain, especially if used in multiple places.
  - CTE: Enhances readability by breaking down complex queries into modular sections, promoting a more structured and manageable code.

**Example of CTE vs. Subquery:**
```sql
-- CTE Example
WITH HighValueCustomers AS (
    SELECT CustomerID
    FROM Orders
    WHERE TotalAmount > 1000
)

SELECT FirstName, LastName
FROM Customers
WHERE CustomerID IN (SELECT CustomerID FROM HighValueCustomers);
```

In this CTE example, the temporary result set is named `HighValueCustomers` and then referenced in the main query.

In summary, while both subqueries and CTEs serve the purpose of providing intermediate result sets within a SQL query, CTEs offer a more modular and readable approach, especially in scenarios involving complex queries or multiple references to the same data.
