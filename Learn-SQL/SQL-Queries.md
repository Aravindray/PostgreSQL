[<< SQL Intro](./SQL-Intro.md)

## Table of Content
- [Clauses](#clauses)
- [OPERATOR](#operator)
  - [Arithmetic Operators](#arithmetic-operators)
  - [Bitwise Operators](#bitwise-operators)
  - [Comparison Operators](#comparison-operators)
  - [Compound Operators](#compound-operators)
  - [Logical Operators](#logical-operators)
  - [Special Operators](#special-operators)
- [CRUD Operations - Create | Read | Update | Delete](#crud-operations---create--read--update--delete)
  - [Create](#create)
    - [Create: How to create a database?](#create-how-to-create-a-database)
    - [Create: How to create a table?](#create-how-to-create-a-table)
    - [Insert: TABLE ... VALUES - How to add a new item in a table?](#insert-table--values---how-to-add-a-new-item-in-a-table)
    - [INSERT INTO ... SELECT ... - How to select results from one table and create it in another table?](#insert-into--select----how-to-select-results-from-one-table-and-create-it-in-another-table)
  - [Read](#read)
    - [Select: How to select and display all the results?](#select-how-to-select-and-display-all-the-results)
    - [Select: WHERE - How to select and display particular result(s)?](#select-where---how-to-select-and-display-particular-results)
    - [Select: WHERE ... LIKE ... - How to select and display particular result(s) with matching patterns (wildcard)?](#select-where--like----how-to-select-and-display-particular-results-with-matching-patterns-wildcard)
    - [Select: WHERE - How to select and display only one result?](#select-where---how-to-select-and-display-only-one-result)
    - [Select: ORDER BY - How to select and display result in different orders (sorted)?](#select-order-by---how-to-select-and-display-result-in-different-orders-sorted)
    - [Select: LIMIT/OFFSET - How to limit the results?](#select-limitoffset---how-to-limit-the-results)
    - [Select: COUNT - How to display the results count?](#select-count---how-to-display-the-results-count)
  - [Update](#update)
    - [Update: SET ... WHERE ... - How to update / modify the existing data?](#update-set--where----how-to-update--modify-the-existing-data)
    - [ALTER TABLE - How to update the table column field(s)?](#alter-table---how-to-update-the-table-column-fields)
  - [Delete](#delete)
    - [Delete: FROM - How to delete all records?](#delete-from---how-to-delete-all-records)
    - [Delete: FROM ... WHERE ... - How to delete particular record(s)?](#delete-from--where----how-to-delete-particular-records)
    - [Delete: FROM ... WHERE ... - How to delete a single record?](#delete-from--where----how-to-delete-a-single-record)
- [Relation Operations](#relation-operations)
  - [One-to-One Relationship](#one-to-one-relationship)
  - [One-to-Many Relationship](#one-to-many-relationship)
  - [Many-to-Many Relationship](#many-to-many-relationship)
- [JOIN Operations](#join-operations)
  - [JOIN with One-to-Many relationship - INNER JOIN / JOIN ... ON ...](#join-with-one-to-many-relationship---inner-join--join--on-)
  - [JOIN with Many-to-Many relationship](#join-with-many-to-many-relationship)
  - [CROSS JOIN (Rarely used)](#cross-join-rarely-used)
- [Vital](#vital)
  - [DATES](#dates)
      - [TIMESTAMPTZ - Best practice](#timestamptz---best-practice)
      - [CASTING](#casting)
      - [Intervals](#intervals)
      - [DATE\_TRUNC()](#date_trunc)
      - [Performance](#performance)
  - [DISTINCT](#distinct)
  - [GROUP BY](#group-by)
    - [HAVING](#having)
  - [Regular Expression](#regular-expression)
  - [Wildcard](#wildcard)
  - [Sub-Queries](#sub-queries)
  - [Concurrency](#concurrency)
    - [ON CONFLICT - Like Try and Expect](#on-conflict---like-try-and-expect)
  - [Transactions](#transactions)
  - [Stored Procedures](#stored-procedures)
  - [If/Else in Postgres - CASE THEN ELSE END](#ifelse-in-postgres---case-then-else-end)

<br>

# Clauses

| Clause        | Description                     |
| ------------- | ------------------------------- |
| SELECT        | Retrieve data                   |
| FROM          | Choose the table                |
| WHERE         | Filter rows                     |
| GROUP BY      | Group rows                      |
| HAVING        | Filter groups                   |
| ORDER BY      | Sort results                    |
| LIMIT         | Limit result rows               |
| OFFSET        | Skip rows                       |
| JOIN          | Combine tables                  |
| ON            | Condition for JOIN              |
| AS            | Rename column/table             |
| INSERT INTO   | Add new rows                    |
| VALUES        | Provide values for insert       |
| UPDATE        | Modify data                     |
| SET           | Set new values in update        |
| DELETE        | Delete rows                     |
| CREATE TABLE  | Define new table                |
| DROP TABLE    | Remove table                    |
| DROP DATABASE | Remove database                 |
| ALTER TABLE   | Modify table structure          |
| SERIAL        | Used to mark auto increment key |
| REFERENCES    | Used to connect tables          |
| IN            | Used to check element in array  |

**Notes:** SELECT() - [article](https://www.postgresql.org/docs/current/sql-select.html)

# OPERATOR

## Arithmetic Operators

| Operator | Meaning  |
| -------- | -------- |
| +        | Add      |
| -        | Subtract |
| *        | Multiply |
| /        | Divide   |
| %        | Modulo   |

## Bitwise Operators

| Operator | Meaning              |
| -------- | -------------------- |
| &        | Bitwise AND          |
|          | Bitwise OR           |
| ^        | Bitwise exclusive OR |

## Comparison Operators

| Operator   | Meaning          |
| ---------- | ---------------- |
| =          | Equal to         |
| != (or) <> | Not equal to     |
| >          | Greater than     |
| <          | Less than        |
| >=         | Greater or equal |
| <=         | Less or equal    |

## Compound Operators

| Operator | Meaning                  |
| -------- | ------------------------ |
| +=       | Add equals               |
| -=       | Subtract equals          |
| *=       | Multiply equals          |
| /=       | Divide equals            |
| %=       | Modulo equals            |
| &=       | Bitwise AND equals       |
| ^-=      | Bitwise exclusive equals |
| !*=      | Bitwise OR equals        |

## Logical Operators

| Operator | Meaning              |
| -------- | -------------------- |
| AND      | Both conditions true |
| OR       | At least one true    |
| NOT      | Negate condition     |

## Special Operators

| Operator        | Meaning              |
| --------------- | -------------------- |
| \|\|            | Concat strings       |
| LIKE            | Pattern matching     |
| IN (...)        | Match any in list    |
| BETWEEN A AND B | Match range          |
| IS NULL         | Check for NULL value |
| EXISTS          | Subquery return rows |
| ALL             |                      |
| ANY             |                      |
| SOME            |                      |
| UNIQUE          |                      |

# CRUD Operations - Create | Read | Update | Delete

## Create

### Create: How to create a database?

Logged in with a <a title="How to login with SQL Server with PSQL?" href="../Basic/Intro.md#how-to-login-with-sql-server-with-psql">superuser account</a> and <a title='How to create a user?' href="../Basic/pg-specific-cmds.md#how-to-create-a-user">create a new user</a> for the owner of this newly creating database and then execute the below cmd

Syntax
```
=# CREATE DATABASE database_name WITH OWNER 'user_name' ENCODING 'UTF8';
```

Example
```
=# CREATE DATABASE people WITH OWNER 'pg4e' ENCODING 'UTF8';
```

Replace the database_name with actual database and name the database with singular noun. And replace the 'user_name' with new user which you are created from superuser.

### Create: How to create a table?

Syntax
```
=> CREATE TABLE table_name(
    col_1_name datatype(condition),
    col_2_name datatype(condition),
);
```

Example
```
=> CREATE TABLE user(
    name VARCHAR(128),
    email VARCHAR(128),
);
```

### Insert: TABLE ... VALUES - How to add a new item in a table?

Syntax
```
=> INSERT TABLE table_name (col_1, col_2) VALUES (col_1_value, col_2_value);
```

Example
```
=> INSERT TABLE user (name, email) VALUES ('Ray', 'ray@gmail.com');
```

### INSERT INTO ... SELECT ... - How to select results from one table and create it in another table?

Consider these 2 tables xy_raw (x, y, y_id - all text field) and y (id - PK, y - text)

Syntax
```
=> INSERT INTO new_table(new_col) SELECT DISTINCT old_col FROM old_table;
```

Example
```
=> INSERT INTO y(y) SELECT DISTINCT y FROM xy_raw;
```

## Read

### Select: How to select and display all the results?

Retrieves a group of records.

Syntax
```
=> SELECT * FROM table_name;
```

Example
```
=> SELECT * FROM user;
```

### Select: WHERE - How to select and display particular result(s)?

You can either retrieve all the records or a subset of the record with the help of WHERE Clause.

Syntax
```
=> SELECT * FROM table_name WHERE condition;
=> SELECT * FROM table_name WHERE condition_1 AND condition_2;
=> SELECT * FROM table_name WHERE condition_1 OR condition_2;
```
From above AND, and OR operators is used to add multiple conditions. AND statement only execute if both the condition is True and OR statement execute if either one condition is True.

Example
```
=> SELECT * FROM user WHERE email='ray@gmail.com';
```

The above query return one or more results if one or more rows have the same email id.

### Select: WHERE ... LIKE ... - How to select and display particular result(s) with matching patterns (wildcard)?

With the combination of WHERE clause and LIKE operation we can search for results in particular patterns, this method also known as wildcard.

Syntax
```
=> SELECT * FROM table_name WHERE column_name LIKE '%a%';
```
Above method will take more time since this is linear process, so be careful while using this method.

Example
```
=> SELECT * FROM user WHERE name LIKE '%e%';
```

### Select: WHERE - How to select and display only one result?

For every table there will be a unique identifier (primary key) for each row (record) and it's field name is `id`, with **id** we can access only one single result.

```
=> SELECT * FROM table_name WHERE id=1;
```

### Select: ORDER BY - How to select and display result in different orders (sorted)?

With the ORDER BY clause we can get the result sorted in ascending or descending order.

Syntax
```
=> SELECT * FROM table_name ORDER BY column_name; --default order is ascending
=> SELECT * FROM table_name ORDER BY col_1, col_2;
=> SELECT * FROM table_name ORDER BY column_name DESC;
```

Example
```
=> SELECT * FROM user ORDER BY email;
=> SELECT * FROM user ORDER BY email DESC;
```

### Select: LIMIT/OFFSET - How to limit the results?

- We can request to server to return first 'n' rows, or the first 'n' rows after skipping some rows
- The WHERE and ORDER BY clause happen 'before' the LIMIT / OFFSET are applied
- OFFSET starts from 0 (zero), like Python list index

Syntax
```
=> SELECT * FROM table_name ORDER BY column_name DESC LIMIT 2;
=> SELECT * FROM table_name ORDER BY column_name OFFSET 1 LIMIT 2;
```

Example
```
=> SELECT * FROM user ORDER BY email DESC LIMIT 2;
=> SELECT * FROM user ORDER BY email OFFSET 1 LIMIT 2;
```

### Select: COUNT - How to display the results count?

Syntax
```
=> SELECT COUNT(*) FROM table_name;
=> SELECT COUNT(*) FROM table_name WHERE condition;
```

Above statement return the count of the query

Syntax
```
=> SELECT COUNT(*) FROM user;
=> SELECT COUNT(*) FROM user WHERE email='ray@gmail.com';
```

## Update

### Update: SET ... WHERE ... - How to update / modify the existing data?

Syntax
```
=> UPDATE table_name SET col_1='new_value', col_2='new_value' WHERE condition;
=> UPDATE table_name SET col_1='new_value', col_2='new_value' WHERE condition_1 AND condition_2;
```

Above statement will update one or more records if multiple rows met the same conditions, so be careful while updating.


Example
```
=> UPDATE user SET name='Aravind' WHERE email='ray@gmail.com';
```

### ALTER TABLE - How to update the table column field(s)?

- Sometime you make a mistake or your application evolve
- If we made any error we change the value or data type of a table column with ALTER TABLE statement
- We can also alter indexes, uniqueness constraints, foreign keys
- Best thing is that it work / run on live database

Syntax
```
-- to remove a column from a table
ALTER TABLE table_name DROP COLUMN column_name;

-- to alter the datatype of a column (I think there are many other methods and ways)
ALTER TABLE table_name ALTER COLUMN column_name TYPE new_datatype;

-- to add a new column in a table (can I able to add constrains?)
ALTER TABLE table_name ADD COLUMN column_name DATATYPE;
```

Example
```
ALTER TABLE fav DROP COLUMN oops;
ALTER TABLE post ALTER COLUMN content TYPE TEXT;
ALTER TABLE fav ADD COLUMN howmuch INTEGER;
```

## Delete

### Delete: FROM - How to delete all records?

Syntax
```
=> DELETE FROM table_name;
```

Be careful while deleting or updating record, this process can not be undone.

Example
```
=> DELETE FROM user;
```

### Delete: FROM ... WHERE ... - How to delete particular record(s)?

With the help of WHERE clause we can check the conditions and delete the records.

Syntax
```
=> DELETE FROM table_name WHERE condition;
=> DELETE FROM table_name WHERE condition AND condition;
```

Be careful while deleting if many records satisfy the conditions all of them will be deleted.

Example
```
=> DELETE FROM user WHERE email='ray@gmail.com';
```

### Delete: FROM ... WHERE ... - How to delete a single record?

To delete a single retrieve the particular row with primary key and delete the record.

Syntax
```
=> DELETE FROM table_name WHERE id=1;
```

Be careful while deleting or updating record, this process can not be undone.

Example
```
=> DELETE FROM user WHERE id=1;
```

# Relation Operations

- For best check out this [article](../Relational-Database-Design/Design-Intro.md), for my remembrance I will repeat it once.

## One-to-One Relationship

## One-to-Many Relationship

- Simple example of One-to-Many is album and songs relationship, because an album my have may songs.

Let's see how to create an song table and make relation with album table.

Query
```
-- create album table
CREATE TABLE album (
  id SERIAL,
  name VARCHAR(128) UNIQUE,
  -- since this is simple example I add the artist directly in album but this is not how it's work, we make artist table separately
  artist VARCHAR(128)
  PRIMARY KEY(id)
);

-- create song table
CREATE TABLE song (
  id SERIAL,
  title VARCHAR(128) UNIQUE,
  album_id INTEGER REFERENCES album(id) ON DELETE CASCADE,
  PRIMARY KEY(id)
);
```

**REFERENCES** keyword plays a major role between relations.

## Many-to-Many Relationship

- Some of the example to user Many-to-Many relationships are _course - student_, (a student can enroll into multiple student and a course can have n no of student), similarly _book - author_.
- Technically there is no direct many-to-many relationship we create a intermediate (through, join, junction) table and link both tale primary key into this one.

Query
```
-- create a book table
CREATE TABLE book (
  id SERIAL,
  title VARCHAR(128) UNIQUE,
  PRIMARY KEY(id)
);

CREATE TABLE author (
  id SERIAL,
  name VARCHAR(128) UNIQUE,
  PRIMARY KEY(id)
);

CREATE TABLE book_author (
  book_id INTEGER REFERENCES book(id) ON DELETE CASCADE,
  author_id INTEGER REFERENCES book(id) ON DELETE CASCADE,
)
```
Above tables are now considered as many-to-many relationships

# JOIN Operations

## JOIN with One-to-Many relationship - INNER JOIN / JOIN ... ON ...

This example is based on these table from this [article](../Relational-Database-Design/Design-Intro.md#sql-query-to-build-one-to-many-relationship)

**How to query all the album which published by artist**

Syntax
```
=> SELECT tab_1.col_nam, tab_2.col_nam FROM tab_1 JOIN tab_2 ON tab_1.foreign_key_filed = tab_2.primary_key;
```

Actual Query
```
=> SELECT artist.name, album.title
FROM artist
JOIN album ON album.artist_id = artist.id;

-- below give same result as above

=> SELECT artist.name, album.title
FROM artist
INNER JOIN album ON album.artist_id = artist.id;
```

## JOIN with Many-to-Many relationship

This example is based on these table from this [article](../Relational-Database-Design/Design-Intro.md#sql-query-to-build-many-to-many-relationship)

**How to display all the books written by particular author**

Syntax
```
=> SELECT pk_table_1.field_name, pk_table_2.field_name
FROM pk_table_1
JOIN intermediate_table ON intermediate_table.pk_table_1_id = pk_table_1.id
JOIN pk_table_2 ON intermediate_table.pk_table_2_id = pk_table_2.id
WHERE pk_table_2.filter_field = 'author_name';
```

Query
```
=> SELECT book.title, author.name
FROM book
JOIN author_book ON author_book.book_id = book.id
JOIN author ON author_book.author_id = author.id
WHERE author.name = 'Aravind';
```

**How to find this book(s) written by which author**

Query - Similar as above query instead of filtering by author, use book
```
SELECT book.title, author.name
FROM book
JOIN author_book ON author_book.book_id = book.id
JOIN author ON author_book.author_id = author.id
WHERE book.title = 'How to do it?';
```

**Map every book buy it author(s)**

Query - Same as above, without filter
```
SELECT book.title, author.name
FROM book
JOIN author_book ON author_book.book_id = book.id
JOIN author ON author_book.author_id = author.id;
```


## CROSS JOIN (Rarely used)
- It joins everything in a table

**Difference between**
| CROSS JOIN                                  | INNER JOIN                                       |
| ------------------------------------------- | ------------------------------------------------ |
| Cross join means take everything that match | Inner join means take the things that only match |
| It also does **not need ON clause**         |                                                  |

# Vital

## DATES

**DataTypes**
- DATE - 'YYYY-MM-DD'
- TIME - 'HH:MM:SS'
- TIMESTAMP - 'YYYY-MM-DD HH:MM:SS' - Use 8 bytes for storing data
- TIMESTAMPTZ - 'YYYY-MM-DD HH:MM:SS+00' - Use 8 bytes for storing data

Data type also have NOW() function

**Basic Notes**
- we can save some code by auto populating data field when a row is inserted

#### TIMESTAMPTZ - Best practice
- Store date and time with timezone
- Prefer UTC for store time stamps
- Convert to local time zone when retrieving

#### CASTING
- Convert data type from one type to another (postgres has several form of casting)
- We use CAST() function

Query
```
=> SELECT NOW()::DATE, CAST(NOW() AS DATE), CAST(NOW() AS TIME);
```

#### Intervals
- We can do date interval arithmetic with INTERVAL keyword

```
=> SELECT NOW(), NOW() - INTERVAL '2 days', (NOW() - INTERVAL '2 days')::DATE;
```

#### DATE_TRUNC()
- Sometime we want to discard some of the accuracy that is in a timestamp

Examples generated by AI
```
-- Truncate to the beginning of the day

=> SELECT date_trunc('day', '2025-05-05 15:30:00'::timestamp); -- Output: 2025-05-05 00:00:00

-- Truncate to the beginning of the day

=> SELECT date_trunc('month', '2025-05-05 15:30:00'::timestamp); -- Output: 2025-05-01 00:00:00

-- Truncate to the beginning of the year

=> SELECT date_trunc('year', '2025-05-05 15:30:00'::timestamp); -- Output: 2025-01-01 00:00:00

-- Truncate to the beginning of the year

=> SELECT date_trunc('hour', '2025-05-05 15:30:00'::timestamp); -- Output: 2025-05-05 15:00:00
```

#### Performance
- Not all equivalent queries have the same performance
- Full table scan is bad performance

**This is a fast query and better performance**
```
=> SELECT id, content, created_at
FROM comment
WHERE crated_at >= DATE_TRUNC('day', NOW())
AND created_at < DATE_TRUNC('day', NOW() + INTERVAL '1 day');
```

**Equivalent query but slow performance**
```
=> SELECT id, content, created_at
FROM comment
WHERE created_at::DATE = NOW()::DATE;
```

## DISTINCT

- DISTINCT only return unique rows in a result set and row will only appear once.
- **DISTINCT ON (rarely used)** limits duplicate removal to a set of columns

Syntax
```
=> SELECT DISTINCT col_name FROM table_name;
```

## GROUP BY

- GROUP BY is combined with aggregate functions like COUNT(), MAX(), SUM(), AVG()

Example
```
=> SELECT COUNT(abbrev), abbrev FROM pg_timezone_names GROUP BY abbrev;
```

### HAVING
- WHERE clause reduce the result set before the GROUP BY
- HAVING is like WHERE clause which filter after the group data

Query
```
=> SELECT COUNT(abbrev) AS ct, abbrev
FROM pg_timezone_names
WHERE is_dst = 't' -- dst means daylight saving time
GROUP BY abbrev
HAVING COUNT(abbrev) > 10;
```

## Regular Expression

**Regular Expression Quick Guide**

| Symbol   | Description                                         |
| -------- | --------------------------------------------------- |
| ^        | Matches the beginning of a line                     |
| $        | Matches the end of the line                         |
| .        | Matches any character                               |
| \s       | Matches whitespace                                  |
| \S       | Matches any non-whitespace character                |
| *        | Repeats a character zero or more times              |
| *?       | Repeats a character zero or more times (non-greedy) |
| +        | Repeats a character one or more times               |
| +?       | Repeats a character one or more times (non-greedy)  |
| [aeiou]  | Matches a single character in the listed set        |
| [^XYZ]   | Matches a single character not in the listed set    |
| [a-z0-9] | The set of characters can include a range           |
| (        | Indicates where string extraction is to start       |
| )        | Indicates where string extraction is to end         |

## Wildcard

**Wildcard Characters**

| Symbol | Description                       |
| ------ | --------------------------------- |
| %      | Represent zero or more characters |
| _      | Represent a single character      |

| Pattern  | Meaning                                            |
| -------- | -------------------------------------------------- |
| '%es'    | ends with                                          |
| '%me%'   | contains                                           |
| 'ar%'    | starts with                                        |
| '_ondon' | starts with                                        |
| 'L___on' | starts with 'L' and ends with 'on'                 |
| 'a__%'   | starts with 'a' and at least 3 character in length |
| '_r%'    | return all have 'r' in second position             |

## Sub-Queries
- A Query with in a query
- Due to performance issue, we use sub-queries rarely
- It use a value or set of values in a query that are completed by another query
- It makes performance slow, It work like creating a temp table for inner query and filter the result and display it

```
-- basic queries
=> SELECT * FROM account WHERE email='ray@gmail.com';
=> SELECT content FROM comment WHERE account_id = 7;

-- example of sub-query
=> SELECT content FROM comment
WHERE account_id = (SELECT id FROM account WHERE email='ray@gmail.com');
```

## Concurrency
- Database are designed to accept SQL commands from a variety of source simultaneously and make them atomically

**Atomicity**
- To implement atomicity, PostgreSQL 'locks' areas before it start on SQL command that might change an area of the database
- All other access to that area must wait until the area is unlocked

Example
```
=> UPDATE track SET count=count+1 WHERE id=42;

-- behind the process
=> LOCK ROW 42 OF track
READ count FROM track ROW 42
count = count + 1
WRITE count TO track ROW 42
UNLOCK ROW 42 OF track
```

- Single SQL Statements are Atomic
  - Not just update statement, insert statement also atomic
- All the inserts will work and get a unique primary key
- From below, which account gets which key is not predictable

```
INSERT INTO account(email) VALUES ('ed@umich.edu');
INSERT INTO account(email) VALUES ('sue@umich.edu');
INSERT INTO account(email) VALUES ('shally@umich.edu');
```

**Compound Statements**
- There are statements which do more than one things in one statement for efficiency and concurrency.

Example (need more explanation)
```
INSERT INTO fav (post_id, account_id, howmuch)
VALUES (1,1,1)
RETURNING *;

UPDATE fav SET howmuch=howmuch+1
WHERE post_id = 1 AND account_id = 1
RETURNING *;
```
We use RETURNING feature a lot

### ON CONFLICT - Like Try and Expect
- Sometimes you "bump into" a constrain on purpose
- This is same like try and except statement in python

Example
```
-- fail statement
INSERT INTO fav (post_id, account_id, howmuch)
VALUES (1,1,1)
RETURNING *;

-- success statement
INSERT INTO fav (post_id, account_id, howmuch)
VALUES (1,1,1)
ON CONFLICT (post_id, account_id)
DO UPDATE SET howmuch = fav.howmuch + 1
RETURNING *;
```

## Transactions

- The implementation of Transaction makes a big difference in database performance
  - Lock
  - Lock Implementation
- Lock strength UPDATE, NO KEY UPDATE (explore more - he didn't cover)
- What to do when encountering a lock (WAIT), NOWAIT, SKIP LOCKED (explore more - he didn't cover)

Syntax
```
-- create a transaction and save successfully
BEGIN
UPDATE
COMMIT

-- create a transaction and revert back
BEGIN
UPDATE
ROLLBACK
```

Example
```
-- revert scenario
=> BEGIN;
SELECT howmuch FROM fav WHERE account_id=1 AND post_id=1 FOR UPDATE OF fav;
-- Time passes ...
UPDATE fav SET howmuch=999 WHERE account_id=1 AND post_id=1;
ROLLBACK;
SELECT howmuch FROM fav WHERE account_id=1 AND post_id=1;

-- commit scenario
=> BEGIN;
SELECT howmuch FROM fav WHERE account_id=1 AND post_id=1 FOR UPDATE OF fav;
-- Time passes ...
UPDATE fav SET howmuch=999 WHERE account_id=1 AND post_id=1;
COMMIT;
SELECT howmuch FROM fav WHERE account_id=1 AND post_id=1;
```

## Stored Procedures
- A stored procedure is a bit of reusable code that runs inside the database server
- There are multiple language but choose - **plpgsql**
- Generally quite not-portable to other databases
- Usually the goal is to have fewer SQL statements

**You should have strong reason to use a stored procedure**
- Major performance problem
- Harder to test/modify
- No database portability
- Some rules that 'must' be enforced

Actual Query - auto update field (updated_at field)
```
-- consider the table name fav in it we have updated_at field which will update automatically whenever the user modify the data

-- old query before stored procedure
UPDATE fav SET howmuch = howmuch + 1, updated_at = NOW()
WHERE post_id = 1 and account_id = 1;

-- using functions and trigger for automate updated_at
CREATE OR REPLACE FUNCTION trigger_set_timestamp()
RETURN TRIGGER AS $$
BEGIN
  NEW.updated_at = NOW();
  RETURN NEW;
END;
$ $ LANGUAGE plpgsql;

CREATE TRIGGER set_timestamp
BEFORE UPDATE ON fav
FOR EACH ROW
EXECUTE PROCEDURE trigger_set_timestamp();

-- new query after stored procedure
UPDATE fav SET howmuch=howmuch+1
WHERE post_id = 1 and account_id = 1;
```

## If/Else in Postgres - CASE THEN ELSE END

Syntax
```
=> SELECT (CASE WHEN (condition)
THEN ...
ELSE ...
END
)
```

Example
```
=> SELECT (CASE WHEN (random() < 0.5)
  THEN 'https://www.pg4e.com/neon/'
  ELSE 'http://www.pg4e.com/LEMONS/'
  END
) || generate_series(100000, 200000)
```