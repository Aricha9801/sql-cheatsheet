[Data types](https://www.postgresql.org/docs/current/datatype.html)

# Managing

## systemd
```shell
sudo systemctl start postgresql
sudo service postgresql start
```

## psql
[psql commands](https://www.postgresguide.com/utilities/psql/)
```shell
# open psql
sudo -u postgres psql
# list all databases
\l
# connect to a database
\c mydatabase
# describe a table
\d core.plot
# list all schemas
\dn
# list all functions
\df
# exit
\q


```

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
# commit a transaction
BEGIN;
UPDATE accounts SET balance = balance -100
 WHERE name = 'Alice';
COMMIT;

# discard a transaction
BEGIN;
UPDATE account SET balance = balance -100;
ROLLBACK;

# use savepoints
BEGIN;
UPDATE accounts SET balance = balance - 100 WHERE name = 'Alice';
SAVEPOINT my_savepoint;
UPDATE accounts SET balance = balance + 100 WHERE name = 'Bob';
ROLLBACK TO my_save_point;
UPDATE accounts SET balance = balance + 100 WHERE name = 'Wally';
COMMIT
```

## Contraints
```sql
# check
CREATE TABLE products (
id integer,
name text,
price numeric CHECK (price > 0)
);
CREATE TABLE products (
id integer,
name text,
price numeric,
discounted_price numeric,
CHECK (discounted_price > 0),
CHECK (price > discounted_price)
);

# not null
CREATE TABLE products (
id integer NOT NULL,
name text,
price numeric
);

# unique
CREATE TABLE products (
id integer UNIQUE,
name text,
price numeric
);

# primary keys
CREATE TABLE products (
id integer PRIMARY KET,
name text,
price numeric
);

# foreign keys
CREATE TABLE orders (
order_id integer PRIMARY KEY,
product_no integer REFERENCES products (id),
quantity integer
);

```
