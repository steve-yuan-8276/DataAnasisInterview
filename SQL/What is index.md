# What is Index?

In databases, an index (Index) is a data structure used to improve the efficiency of searching database tables. An index is similar to a book's table of contents and can speed up the finding of data in a table, especially on large data sets. Indexes contain key values and corresponding row pointers that can be used to quickly locate rows of data based on the key values.

Indexes can be created in SQL queries using the `CREATE INDEX` statement. Indexes can be based on a single column or multiple columns and can be unique or non-unique.

The following is a basic syntax for creating an index:

```sql
-- Create a single-column index
CREATE INDEX index_name ON table_name (column_name).

-- Create a multicolumn index
CREATE INDEX index_name ON table_name (column1, column2, ...) ;
```

where:
- `index_name` is the name of the index to be referenced in the query.
- `table_name` is the name of the table for which the index is to be created.
- `column_name`, `column1, column2, ... ` are the names of the columns to be included in the index.
Using an index in a query can be accomplished with the `INDEX` or `FORCE INDEX` hints. The database system automatically chooses whether or not to use an index based on the complexity of the query and statistical information, but sometimes manual intervention may be more effective.

Example:
```sql
-- Use the index prompt
SELECT * FROM table_name INDEX (index_name) WHERE condition;

-- Force the index to be used
SELECT * FROM table_name FORCE INDEX (index_name) WHERE condition;
```

**Notes:**
1. index creation increases the cost of write operations because indexes need to be updated during inserts, updates, and deletes.
2. Not all queries are suitable for using indexes, depending on the query conditions, table size, and data distribution.
3. Too many indexes can lead to performance degradation because it increases the overhead of storage and maintenance.
When choosing to create an index, it needs to be evaluated and tested based on real-world scenarios to ensure that it has a positive effect on query performance improvement.
