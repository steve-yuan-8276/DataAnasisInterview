# What is Temp Table?

A temporary table, or temp table, is a table that exists temporarily on the database server. It is created to store intermediate results during a session and is automatically dropped when the session ends. Temp tables can be explicitly created and manipulated like regular tables, providing a way to store and process temporary data.

**Example of a Temp Table:**
```sql
CREATE TEMPORARY TABLE TempHighValueCustomers AS (
    SELECT CustomerID, FirstName, LastName
    FROM Customers
    WHERE TotalPurchases > 1000
);

SELECT * FROM TempHighValueCustomers;
```

In this example, a temporary table named `TempHighValueCustomers` is created to store the same set of high-value customers.

**Difference Between CTE and Temp Table:**

1. **Scope and Duration:**
   - CTE: Exists only for the duration of the query in which it is defined.
   - Temp Table: Persists for the duration of the session or until explicitly dropped.

2. **Usage in Subsequent Queries:**
   - CTE: Can be referenced within the query in which it is defined.
   - Temp Table: Can be referenced in subsequent queries within the same session.

3. **Definition Syntax:**
   - CTE: Defined using the WITH clause.
   - Temp Table: Created using the CREATE TABLE statement with the TEMPORARY keyword.

4. **Readability and Modularity:**
   - CTE: Enhances query readability by breaking it into modular components.
   - Temp Table: Provides a separate storage structure for data and can be useful for large datasets or complex processing.

**Choosing Between CTE and Temp Table:**
- Use a CTE when the temporary result set is needed for the duration of a single query.
- Use a temp table when the data needs to be stored and reused across multiple queries within the same session or when dealing with large datasets that benefit from indexing.

In summary, both CTEs and temp tables serve the purpose of handling temporary data, but the choice between them depends on the scope, duration, and reuse requirements of the temporary data.

