# What is window function?

A window function is a type of SQL function that performs a calculation across a specified range of rows related to the current row within a result set, known as a "window." Unlike aggregate functions that operate on an entire result set, window functions focus on a subset of rows defined by an OVER clause.

**Common Applications of Window Functions:**

1. **Ranking Functions:**
   - **ROW_NUMBER():** Assigns a unique rank to each row within a partition of the result set.
   - **RANK():** Provides a rank with possible ties, leaving gaps for equivalent values.
   - **DENSE_RANK():** Similar to RANK(), but without gaps for ties.

   ```sql
   SELECT
       EmployeeID,
       Salary,
       ROW_NUMBER() OVER (ORDER BY Salary DESC) AS RowNum
   FROM Employees;
   ```

2. **Aggregation over Windows:**
   - Performs aggregate calculations over a specified window.
   - Common window functions include SUM(), AVG(), MIN(), and MAX().

   ```sql
   SELECT
       Department,
       Salary,
       AVG(Salary) OVER (PARTITION BY Department) AS AvgSalary
   FROM Employees;
   ```

3. **Window Frame Specification:**
   - Specifies the range of rows within a window.
   - Common options include ROWS UNBOUNDED PRECEDING, CURRENT ROW, and ROWS BETWEEN x PRECEDING AND y FOLLOWING.

   ```sql
   SELECT
       Date,
       Revenue,
       SUM(Revenue) OVER (ORDER BY Date ROWS BETWEEN 1 PRECEDING AND 1 FOLLOWING) AS AvgRevenue
   FROM SalesData;
   ```

4. **Running Total and Running Aggregates:**
   - Calculates a running total or other aggregates over a specified window.

   ```sql
   SELECT
       OrderDate,
       OrderAmount,
       SUM(OrderAmount) OVER (ORDER BY OrderDate) AS RunningTotal
   FROM Orders;
   ```

5. **Percentiles and Cumulative Distribution:**
   - Utilizes PERCENTILE_CONT() and PERCENTILE_DISC() functions for calculating percentiles within a window.

   ```sql
   SELECT
       Product,
       Sales,
       PERCENTILE_CONT(0.5) WITHIN GROUP (ORDER BY Sales) OVER (PARTITION BY Product) AS MedianSales
   FROM ProductSales;
   ```

Window functions offer powerful analytical capabilities, enabling more sophisticated analysis and reporting by considering the context of each row within the result set.
