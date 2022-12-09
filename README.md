# learnPostgreSQL

Learning more about how to work with database, here I will cover some concepts based on PostgreSQL. 

# Getting Started
```shell
# Still in progress ...
```
# Whats a database? 
Database is a organized collection of data stored. There so many context about it, but you can image a database like a folder and inside of that there so many tables listed. Here in this project, template0 and template1 are our folders.

# Version
I'm using postgreSQL 14, I really recommend you to use the same version, because I don't know what kind of features change between the other version.
### Docker image
[complete-intro-to-SQL](https://sql.holt.courses/lessons/welcome/docker)
[postgres](https://hub.docker.com/_/postgres/)
### Useful commands
```shell
# After get the docker images, run the command to see if its working
$ docker run -e POSTGRES_PASSWORD=lol --name=pg --rm -d -p 5432:5432 postgres:14

# To execute the postgres inside the container, it should return the postgres cli
docker exec -u postgres -it pg psql
```
### PSQL commands
```shell
# List all databases
$ \l

# Run some bash commands, maybe you want to use a cat to see files or pwd to find the current directory
$ \! pwd 

# Show all the tables and sequences and relations
$ \d

# Connect to a database
\c recipeguru #\c + database name
```
# SQL code block
DO NOT USE "DOUBLE QUOTES" IF YOU WILL INSERT VALUES ONLY 'SINGLE QUOTES'
### CREATE DATABASE

```SQL
-- Create a database
CREATE DATABASE dbName;
```

### INSERT INTO
```SQL
-- Insert data inside a table
INSERT INTO table_name (column1, column2, ...);
```
### DROP TABLE
```SQL
-- Drop table
DROP TABLE table_name;

-- Drop Database
DROP DATABASE dbName;
```
### ALTER TABLE
```SQL
-- Used to add, delete or modify columns, is also used to add and drop constraints on an existing table
ALTER TABLE table_name ADD column_name datatype;
ALTER TABLE table_name DROP COLUMN column_name;
ALTER TABLE table_name ALTER COLUMN column_name datatype;
```

### ON CONFLICT
```SQL
-- If a row already exists just do nothing about it
ON CONFLICT DO NOTHING
-- Insert if does not exists and update if does not.
ON CONFLICT (column_name) DO UPDATE SET column_name = 'something';
```
### UPDATE 
```SQL
-- Updating directly, use WHERE clause to filter what you want to update
UPDATE table_name SET column_name = 'something' WHERE title = 'something';
-- You can add RETURNING clause to specify which columns do you want to see after run the query
UPDATE ingredients SET image = 'watermelon.jpg' WHERE title = 'watermelon' RETURNING id, title, image;
-- RETURNING * -> it will return all the columns
```

### DELETE 
```SQL
-- It will delete every image with the different.jpg attribute
DELETE FROM ingredients
WHERE image='different.jpg'
RETURNING *;
```

### SELECT
```SQL
-- Select will basic search in your dabatase
SELECT * FROM ingredients;  -- it will return all the data

-- You can specify the limit that you want to request
SELECT * FROM ingredients LIMIT 10; 
```
### LIMIT and OFFSET
```SQL
-- With limit we can return only five records
SELECT id, title, image
FROM ingredients
LIMIT 5;

-- But let's imagine that you need to get the next five records, in this case, we can use OFFSET to skip that many rows before beginning return  rows
SELECT id, title, image
FROM ingredients
LIMIT 5
OFFSET 5;

-- It will return 5 ingredients but starting from 6 because we are skipping the number 5 with offset clause
```
### ORDER BY
```SQL
-- We can use order by to order the data
SELECT * FROM ingredients ORDER BY title;

-- We can order by DESC, it will return by descending and ascending too.
SELECT * FROM ingredients ORDER BY id DESC;
```

### LIKE, ILIKE & SQL FUNCTIONS
```SQL
-- It used in "WHERE" clause to search for a specified pattern in a column
SELECT * FROM ingredients WHERE title LIKE 'b%';

-- Function LOWER() and UPPER() will return transform the data on that function
SELECT * FROM ingredients WHERE LOWER(title) LIKE '%BANANA%'; -- return: banana

```

```SQL
-- ILIKE is used when you have upper strings inside the input, but whatever the way that want search, it always convert to lower.
SELECT * FROM ingredients WHERE title ILIKE '%bAnAnA%'; -- return: banana

-- If you add bAnAnA with "LIKE" clause it will not find, because there are uppercase strings.
-- By default postgres is sensitive case, which means that the data should be exactly equals the result.
-- Based on that, they created "ILIKE" where is used in insensitive cases, you can put uppercase strings but it always read as lower.

```

```SQL 
-- CONCAT FUNCTION
SELECT CONCAT('OI', 'CARAI');

return:
 concat
---------
 OICARAI
```

#### Rules
| LIKE OPERATOR                  | DESCRIPTION                                                                  |
|--------------------------------|------------------------------------------------------------------------------|
| WHERE CustomerName LIKE 'a%'   | Finds any values that start with "a"                                         |
| WHERE CustomerName LIKE '%a'   | Finds any values that end with "a"                                           |
| WHERE CustomerName LIKE '%or%' | Finds any values that have "or" in any position                              |
| WHERE CustomerName LIKE '_r%'  | Finds any values that have "r" in the second position                        |
| WHERE CustomerName LIKE 'a_%'  | Finds any values that start with "a" and are at least 2 characters in length |
| WHERE CustomerName LIKE 'a__%' | Finds any values that start with "a" and are at least 3 characters in length |
| WHERE ContactName LIKE 'a%o'   | Finds any values that start with "a" and ends with "o"                       |


# Reference
[doc](https://gist.github.com/coproduto/5e8cec614a86f1d5668e5322a8b2e67c)
