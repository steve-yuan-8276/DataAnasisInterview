# Join, Blend and Relationship

In Tableau, joins, blends, and relationships are all techniques used to combine data from multiple tables or data sources.

A **join** is a method of combining fields from two or more tables based on related columns between them. In Tableau Desktop, join is implemented at the physical layer and supports inner join, left join, right join, and full outer join. Currently, Tableau supports up to 32 tables joined together. With Tableau prep, you can also support rightonly join, leftonly join and notinner join.

**Data blending** is a technique used to combine data from different data sources in a single view. Unlike the join, data blending is referred to two tables, primary and secondary data sources. A join combines the data and then aggregates, while a blend aggregates and then combines the data. Blending is useful when you have data from different sources that can't be easily joined or want to keep the data separate but display them together in a single visualization.

**Relationships** are used to define how fields in different tables are related to each other without actually combining the data. There are two things: first, Relationships are more flexible in their usage, and you don't need to specify join type; second, Relationships are implemented at the logical level. Relationships are helpful when working with multiple tables where you want to create a logical connection between them, but you don't need to combine the data at the row level.
