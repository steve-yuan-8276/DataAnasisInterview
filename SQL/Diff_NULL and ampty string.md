# Diffrence between NULL and empty string

The difference between NULL and '' (an empty string) in the context of database systems, such as SQL, is as follows:

- NULL represents an unknown or undefined value. Even two NULL values are not considered equal. For example, the query SELECT NULL=NULL would return false. However, NULL values are treated as equal when involved in operations like DISTINCT, GROUP BY, or ORDER BY.
- '' has a length of 0 and doesn't occupy space in the same way a string would. NULL, on the other hand, represents the absence of any value and is considered to take up space, conceptually speaking, because it signifies an unknown value that needs to be handled differently.
- NULL values affect the outcome of aggregate functions. Functions such as SUM, AVG, MIN, and MAX ignore NULL values. The handling of NULL by the COUNT function depends on its usage. COUNT(*) will count all rows, including those with NULL values, whereas COUNT(column_name) will only count rows where the column has a non-NULL value.
- When querying for NULL values, you must use IS NULL or IS NOT NULL to check for the presence or absence of NULL. These special operators are required because standard comparison operators like =, !=, <, > do not work with NULL. In contrast, an empty string '' can be compared using standard comparison operators.

- NULL 代表一个不确定的值,就算是两个 NULL,它俩也不一定相等。例如，SELECT NULL=NULL的结果为 false，但是在我们使用DISTINCT,GROUP BY,ORDER BY时,NULL又被认为是相等的。
- ''的长度是 0，是不占用空间的，而NULL 是需要占用空间的。
- NULL 会影响聚合函数的结果。例如，SUM、AVG、MIN、MAX 等聚合函数会忽略 NULL 值。 COUNT 的处理方式取决于参数的类型。如果参数是 *(COUNT(*))，则会统计所有的记录数，包括 NULL 值；如果参数是某个字段名(COUNT(列名))，则会忽略 NULL 值，只统计非空值的个数。
- 查询 NULL 值时，必须使用 IS NULL 或 IS NOT NULLl 来判断，而不能使用 =、!=、 <、> 之类的比较运算符。而''是可以使用这些比较运算符的
