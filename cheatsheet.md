[Data types](https://www.postgresql.org/docs/current/datatype.html)

## Schema
```sql
# create a schema
CREATE SCHEMA schema;

# drop a schema
DROP SCHEMA schema;
DROP SCHEMA schema CASCADE;
```
## Table
```sql
# create a table
CREATE TABLE my_table (
 col1 text,
 col2 integer
);

# drop a table
DROP TABLE my_table;
```

## Query
```sql
# a basic query
SELECT city FROM weather;

# with expression
SELECT city, (temp1 + tem2)/2 AS temp_avg FROM weather;

# where
SELECT city FROM weather
WHERE city = 'New York' AND temp > 20;

# order
ORDER BY city;

# distinct
SELECT DISTINCT city FROM weather;
```

## Transaction
```sql
BEGIN;
UPDATE accounts SET balance = balance -100
 WHERE name = 'Alice';
-- etc etc
COMMIT;



```
