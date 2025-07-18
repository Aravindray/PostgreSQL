[<< SQL Intro](./SQL-Intro.md)

## Table of Content
- [Clauses](#clauses)
- [OPERATORS](#operators)
  - [Arithmetic Operators](#arithmetic-operators)
  - [Bitwise Operators](#bitwise-operators)
  - [Comparison Operators](#comparison-operators)
  - [Compound Operators](#compound-operators)
  - [Logical Operators](#logical-operators)
  - [Special Operators](#special-operators)
  - [JSONB Operators](#jsonb-operators)
- [CRUD Operations - Create | Read | Update | Delete](#crud-operations---create--read--update--delete)
  - [Create](#create)
    - [CREATE: How to create a database?](#create-how-to-create-a-database)
    - [CREATE: How to create a table?](#create-how-to-create-a-table)
    - [CREATE: How to create a table with unique name and ignore if name exists?](#create-how-to-create-a-table-with-unique-name-and-ignore-if-name-exists)
    - [INSERT: TABLE ... VALUES - How to add a new item in a table?](#insert-table--values---how-to-add-a-new-item-in-a-table)
    - [INSERT: TABLE ... VALUES - How to insert multiple items in a table?](#insert-table--values---how-to-insert-multiple-items-in-a-table)
    - [INSERT: INTO ... SELECT ... - How to select results from one table and create it in another table?](#insert-into--select----how-to-select-results-from-one-table-and-create-it-in-another-table)
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
    - [DELETE: FROM - How to delete all records?](#delete-from---how-to-delete-all-records)
    - [DELETE: FROM ... WHERE ... - How to delete particular record(s)?](#delete-from--where----how-to-delete-particular-records)
    - [DELETE: FROM ... WHERE ... - How to delete a single record?](#delete-from--where----how-to-delete-a-single-record)
    - [DELETE: How to delete a table?](#delete-how-to-delete-a-table)
    - [DELETE: How to delete a table if you are unsure about whether if it exists or not?](#delete-how-to-delete-a-table-if-you-are-unsure-about-whether-if-it-exists-or-not)
    - [DELETE: How to delete a database?](#delete-how-to-delete-a-database)
- [Relation Operations](#relation-operations)
  - [One-to-One Relationship](#one-to-one-relationship)
  - [One-to-Many Relationship](#one-to-many-relationship)
  - [Many-to-Many Relationship](#many-to-many-relationship)
- [JOIN Operations](#join-operations)
  - [INNER JOIN / JOIN ... ON ... - With One-to-Many Relationship](#inner-join--join--on----with-one-to-many-relationship)
  - [JOIN...ON... - With Many-to-Many Relationship](#joinon---with-many-to-many-relationship)
  - [CROSS JOIN (Rarely used)](#cross-join-rarely-used)
  - [LEFT JOIN...ON...](#left-joinon)
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
  - [INDEX](#index)
    - [INDEX - How to make an index for a table?](#index---how-to-make-an-index-for-a-table)
    - [INDEX - How to make an unique index?](#index---how-to-make-an-unique-index)
    - [INDEX - How to make a GIN index?](#index---how-to-make-a-gin-index)
    - [INDEX - How to make an Natural Language Inverted Index with Postgres?](#index---how-to-make-an-natural-language-inverted-index-with-postgres)
    - [INDEX - Index Maintenance!](#index---index-maintenance)
    - [INDEX - How to delete a index?](#index---how-to-delete-a-index)
- [How to Questions? - Beyond CRUD](#how-to-questions---beyond-crud)
  - [How to use GENERATED ALWAYS AS?](#how-to-use-generated-always-as)
  - [How to generate random data(s) in Database?](#how-to-generate-random-datas-in-database)
    - [How to generate random data(s) and insert into on table with if/else condition in Database?](#how-to-generate-random-datas-and-insert-into-on-table-with-ifelse-condition-in-database)
  - [How to check table size in database?](#how-to-check-table-size-in-database)
  - [How to optimize the SQL queries?](#how-to-optimize-the-sql-queries)
      - [How to optimize the B-tree index for better performance?](#how-to-optimize-the-b-tree-index-for-better-performance)
      - [How to optimize the Hash index for better performance?](#how-to-optimize-the-hash-index-for-better-performance)
  - [How to check postgres version?](#how-to-check-postgres-version)
  - [What is this?](#what-is-this)

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
| LEFT JOIN     | Join tables even if no matches  |
| USING         | Make condition in Index         |

**Notes:** SELECT() - [article](https://www.postgresql.org/docs/current/sql-select.html)

# OPERATORS

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

| Operator        | Meaning                                                          |
| --------------- | ---------------------------------------------------------------- |
| \|\|            | Concat strings                                                   |
| ::              | Casting                                                          |
| LIKE            | Pattern matching                                                 |
| ILIKE           | Ignore case                                                      |
| NOT LIKE        |                                                                  |
| NOT iLIKE       |                                                                  |
| IN (...)        | Match any values in list or subquery, =                          |
| BETWEEN A AND B | Match range                                                      |
| IS NULL         | Check for NULL value                                             |
| EXISTS          | Subquery return rows                                             |
| ALL             |                                                                  |
| ANY             | Compare a values to any element of array, =, <, >                |
| SOME            |                                                                  |
| UNIQUE          |                                                                  |
| SIMILAR TO      | Like Regular expression                                          |
| NOT SIMILAR TO  |                                                                  |
| <@              | Return Intersection between 2 arrays                             |
| @@              | Return t/f result of to_tsquery and to_tsvector                  |
| q & q           | to_tsquery special operators - combine operation (q means query) |
| q <-> q         | to_tsquery special operators - first_appear <-> second_appear    |
| ! q & q         | to_tsquery special operators - first_appear <-> second_appear    |

## JSONB Operators

| Operator | Meaning           |
| -------- | ----------------- |
| ->>      |                   |
| @>       | Contains Operator |

# CRUD Operations - Create | Read | Update | Delete

## Create

### CREATE: How to create a database?

Logged in with a <a title="How to login with SQL Server with PSQL?" href="https://github.com/Aravindray/PostgreSQL/blob/main/Basic/Intro.md#how-to-login-with-sql-server-as-a-admin-with-psql">superuser account</a> and <a title='How to create a user?' href="https://github.com/Aravindray/PostgreSQL/blob/main/Basic/Intro.md#how-to-create-a-user">create a new user</a> for the owner of this newly creating database and then execute the below cmd

```sql
admin_syntax=# CREATE DATABASE database_name WITH OWNER 'user_name' ENCODING 'UTF8';
```

```sql
admin_example=# CREATE DATABASE people WITH OWNER 'pg4e' ENCODING 'UTF8';
```

Replace the database_name with actual database and name the database with singular noun. And replace the 'user_name' with new user which you are created from superuser.

### CREATE: How to create a table?

```sql
syntax=> CREATE TABLE table_name(
    col_1_name datatype(condition),
    col_2_name datatype(condition),
    col_3_name datatype,
);
```

```sql
example=> CREATE TABLE user(
    name VARCHAR(128),
    email VARCHAR(128),
    about TEXT
);
```

### CREATE: How to create a table with unique name and ignore if name exists?

```sql
syntax=> CREATE TABLE IF NOT EXISTS table_name (
  ....
);
```

```sql
example=> CREATE TABLE IF NOT EXISTS jtrack (
  id SERIAL,
  body JSONB
);
```

### INSERT: TABLE ... VALUES - How to add a new item in a table?

```sql
syntax=> INSERT TABLE table_name (col_1, col_2) VALUES (col_1_value, col_2_value);
```

```sql
example=> INSERT TABLE user (name, email) VALUES ('Ray', 'ray@gmail.com');
```

### INSERT: TABLE ... VALUES - How to insert multiple items in a table?

```sql
syntax=> INSERT INTO table_name (col) VALUES (val1), (val2), (val);
```

```sql
example=> INSERT INTO user (name) VALUES ('Aravind'), ('Ray'), ('Raj');
```

### INSERT: INTO ... SELECT ... - How to select results from one table and create it in another table?

Consider these 2 tables xy_raw (x, y, y_id - all text field) and y (id - PK, y - text)

```sql
syntax=> INSERT INTO new_table(new_col) SELECT DISTINCT old_col FROM old_table;
```

```sql
example=> INSERT INTO y(y) SELECT DISTINCT y FROM xy_raw;
```

## Read

### Select: How to select and display all the results?

Retrieves a group of records.

```sql
syntax=> SELECT * FROM table_name;
```

```sql
example=> SELECT * FROM user;
```

### Select: WHERE - How to select and display particular result(s)?

You can either retrieve all the records or a subset of the record with the help of WHERE Clause.

```sql
syntax=> SELECT * FROM table_name WHERE condition;
syntax=> SELECT * FROM table_name WHERE condition_1 AND condition_2;
syntax=> SELECT * FROM table_name WHERE condition_1 OR condition_2;
```

From above AND, and OR operators is used to add multiple conditions. AND statement only execute if both the condition is True and OR statement execute if either one condition is True.

```sql
example=> SELECT * FROM user WHERE email='ray@gmail.com';
```

The above query return one or more results if one or more rows have the same email id.

### Select: WHERE ... LIKE ... - How to select and display particular result(s) with matching patterns (wildcard)?

With the combination of WHERE clause and LIKE operation we can search for results in particular patterns, this method also known as wildcard.

```sql
syntax=> SELECT * FROM table_name WHERE column_name LIKE '%a%';
```

Above method will take more time since this is linear process, so be careful while using this method.

```sql
example=> SELECT * FROM user WHERE name LIKE '%e%';
```

### Select: WHERE - How to select and display only one result?

For every table there will be a unique identifier (primary key) for each row (record) and it's field name is `id`, with **id** we can access only one single result.

```
syntax=> SELECT * FROM table_name WHERE id=1;
```

### Select: ORDER BY - How to select and display result in different orders (sorted)?

With the ORDER BY clause we can get the result sorted in ascending or descending order.

```sql
syntax=> SELECT * FROM table_name ORDER BY column_name; --default order is ascending
syntax=> SELECT * FROM table_name ORDER BY col_1, col_2;
syntax=> SELECT * FROM table_name ORDER BY column_name DESC;
```

```sql
example=> SELECT * FROM user ORDER BY email;
example=> SELECT * FROM user ORDER BY email DESC;
```

### Select: LIMIT/OFFSET - How to limit the results?

- We can request to server to return first 'n' rows, or the first 'n' rows after skipping some rows
- The WHERE and ORDER BY clause happen 'before' the LIMIT / OFFSET are applied
- OFFSET starts from 0 (zero), like Python list index

```sql
syntax=> SELECT * FROM table_name ORDER BY column_name DESC LIMIT 2;
syntax=> SELECT * FROM table_name ORDER BY column_name OFFSET 1 LIMIT 2;
```

```sql
example=> SELECT * FROM user ORDER BY email DESC LIMIT 2;
example=> SELECT * FROM user ORDER BY email OFFSET 1 LIMIT 2;
```

### Select: COUNT - How to display the results count?

```sql
syntax=> SELECT COUNT(*) FROM table_name;
syntax=> SELECT COUNT(*) FROM table_name WHERE condition;
```

Above statement return the count of the query

```sql
example=> SELECT COUNT(*) FROM user;
example=> SELECT COUNT(*) FROM user WHERE email='ray@gmail.com';
```

## Update

### Update: SET ... WHERE ... - How to update / modify the existing data?

```sql
syntax=> UPDATE table_name SET col_1='new_value', col_2='new_value' WHERE condition;
syntax=> UPDATE table_name SET col_1='new_value', col_2='new_value' WHERE condition_1 AND condition_2;
```

Above statement will update one or more records if multiple rows met the same conditions, so be careful while updating.

```sql
example=> UPDATE user SET name='Aravind' WHERE email='ray@gmail.com';
```

### ALTER TABLE - How to update the table column field(s)?

- Sometime you make a mistake or your application evolve
- If we made any error we change the value or data type of a table column with ALTER TABLE statement
- We can also alter indexes, uniqueness constraints, foreign keys
- Best thing is that it work / run on live database

```sql
-- to remove a column from a table
syntax=> ALTER TABLE table_name DROP COLUMN column_name;

-- to alter the datatype of a column (I think there are many other methods and ways)
syntax=> ALTER TABLE table_name ALTER COLUMN column_name TYPE new_datatype;

-- to add a new column in a table (can I able to add constrains?)
syntax=> ALTER TABLE table_name ADD COLUMN column_name DATATYPE;
```

```sql
example=> ALTER TABLE fav DROP COLUMN oops;
example=> ALTER TABLE post ALTER COLUMN content TYPE TEXT;
example=> ALTER TABLE fav ADD COLUMN howmuch INTEGER;
```

## Delete

### DELETE: FROM - How to delete all records?

```sql
syntax=> DELETE FROM table_name;
```

Be careful while deleting or updating record, this process can not be undone.

```sql
example=> DELETE FROM user;
```

### DELETE: FROM ... WHERE ... - How to delete particular record(s)?

With the help of WHERE clause we can check the conditions and delete the records.

```sql
syntax=> DELETE FROM table_name WHERE condition;
syntax=> DELETE FROM table_name WHERE condition AND condition;
```

Be careful while deleting if many records satisfy the conditions all of them will be deleted.

```sql
example=> DELETE FROM user WHERE email='ray@gmail.com';
```

### DELETE: FROM ... WHERE ... - How to delete a single record?

To delete a single retrieve the particular row with primary key and delete the record.

```sql
syntax=> DELETE FROM table_name WHERE id=1;
```

Be careful while deleting or updating record, this process can not be undone.

```sql
example=> DELETE FROM user WHERE id=1;
```

### DELETE: How to delete a table?

```sql
query=> DROP TABLE table_name;
```

### DELETE: How to delete a table if you are unsure about whether if it exists or not?

```sql
query=> DROP TABLE IF EXISTS table_name;
```

### DELETE: How to delete a database?

```sql
query=> DROP DATABASE database_name;
```

# Relation Operations

- For best check out this [article](../Relational-Database-Design/Design-Intro.md), for my remembrance I will repeat it once.

## One-to-One Relationship

## One-to-Many Relationship

- Simple example of One-to-Many is album and songs relationship, because an album my have may songs.
Let's see how to create an song table and make relation with album table.

```sql
-- create album table
query=> CREATE TABLE album (
  id SERIAL,
  name VARCHAR(128) UNIQUE,
  -- since this is simple example I add the artist directly in album but this is not how it's work, we make artist table separately
  artist VARCHAR(128)
  PRIMARY KEY(id)
);

-- create song table
query=> CREATE TABLE song (
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

```sql
-- create a book table
query=> CREATE TABLE book (
  id SERIAL,
  title VARCHAR(128) UNIQUE,
  PRIMARY KEY(id)
);

query=> CREATE TABLE author (
  id SERIAL,
  name VARCHAR(128) UNIQUE,
  PRIMARY KEY(id)
);

query=> CREATE TABLE book_author (
  book_id INTEGER REFERENCES book(id) ON DELETE CASCADE,
  author_id INTEGER REFERENCES book(id) ON DELETE CASCADE,
)
```
Above tables are now considered as many-to-many relationships

# JOIN Operations

## INNER JOIN / JOIN ... ON ... - With One-to-Many Relationship

This example is based on these table from this [article](../Relational-Database-Design/Design-Intro.md#sql-query-to-build-one-to-many-relationship)

**How to query all the album which published by artist**

```sql
syntax=> SELECT tab_1.col_nam, tab_2.col_nam FROM tab_1 JOIN tab_2 ON tab_1.foreign_key_filed = tab_2.primary_key;
```

```sql
query=> SELECT artist.name, album.title
FROM artist
JOIN album ON album.artist_id = artist.id;

-- below give same result as above
query=> SELECT artist.name, album.title
FROM artist
INNER JOIN album ON album.artist_id = artist.id;
```

## JOIN...ON... - With Many-to-Many Relationship

This example is based on these table from this [article](../Relational-Database-Design/Design-Intro.md#sql-query-to-build-many-to-many-relationship)

**How to display all the books written by particular author**

```sql
syntax=> SELECT pk_table_1.field_name, pk_table_2.field_name
FROM pk_table_1
JOIN intermediate_table ON intermediate_table.pk_table_1_id = pk_table_1.id
JOIN pk_table_2 ON intermediate_table.pk_table_2_id = pk_table_2.id
WHERE pk_table_2.filter_field = 'author_name';
```

```sql
query=> SELECT book.title, author.name
FROM book
JOIN author_book ON author_book.book_id = book.id
JOIN author ON author_book.author_id = author.id
WHERE author.name = 'Aravind';
```

**How to find this book(s) written by which author**

```sql
-- Similar as above query instead of filtering by author, use book
query=> SELECT book.title, author.name
FROM book
JOIN author_book ON author_book.book_id = book.id
JOIN author ON author_book.author_id = author.id
WHERE book.title = 'How to do it?';
```

**Map every book buy it author(s)**

```sql
-- Same as above, without filter
query=> SELECT book.title, author.name
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

## LEFT JOIN...ON...

**How to join words with their stem words** - example form Chapter 5. Natural Language

```sql
query=> SELECT id, keyword, stem FROM (
  SELECT DISTINCT d.id, s.keyword from docs as d, unnest(string_to_array(lower(d.doc) ' ')) s(keyword) WHERE s.keyword NOT IN (SELECT word FROM stop_words)
) as k
LEFT JOIN docs_stem AS s ON k.keyword = s.word;
```

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

```sql
query=> SELECT NOW()::DATE, CAST(NOW() AS DATE), CAST(NOW() AS TIME);
```

#### Intervals

- We can do date interval arithmetic with INTERVAL keyword

```sql
query=> SELECT NOW(), NOW() - INTERVAL '2 days', (NOW() - INTERVAL '2 days')::DATE;
```

#### DATE_TRUNC()

- Sometime we want to discard some of the accuracy that is in a timestamp

Example generated by AI
```sql
-- Truncate to the beginning of the day
query=> SELECT date_trunc('day', '2025-05-05 15:30:00'::timestamp); -- Output: 2025-05-05 00:00:00

-- Truncate to the beginning of the day
query=> SELECT date_trunc('month', '2025-05-05 15:30:00'::timestamp); -- Output: 2025-05-01 00:00:00

-- Truncate to the beginning of the year
query=> SELECT date_trunc('year', '2025-05-05 15:30:00'::timestamp); -- Output: 2025-01-01 00:00:00

-- Truncate to the beginning of the year
query=> SELECT date_trunc('hour', '2025-05-05 15:30:00'::timestamp); -- Output: 2025-05-05 15:00:00
```

#### Performance

- Not all equivalent queries have the same performance
- Full table scan is bad performance

**This is a fast query and better performance**

```sql
query=> SELECT id, content, created_at
FROM comment
WHERE crated_at >= DATE_TRUNC('day', NOW())
AND created_at < DATE_TRUNC('day', NOW() + INTERVAL '1 day');
```

**Equivalent query but slow performance**

```sql
query=> SELECT id, content, created_at
FROM comment
WHERE created_at::DATE = NOW()::DATE;
```

## DISTINCT

- DISTINCT only return unique rows in a result set and row will only appear once.
- **DISTINCT ON (rarely used)** limits duplicate removal to a set of columns

```sql
syntax=> SELECT DISTINCT col_name FROM table_name;
```

## GROUP BY

- GROUP BY is combined with aggregate functions like COUNT(), MAX(), SUM(), AVG()

```sql
example=> SELECT COUNT(abbrev), abbrev FROM pg_timezone_names GROUP BY abbrev;
```

### HAVING

- WHERE clause reduce the result set before the GROUP BY
- HAVING is like WHERE clause which filter after the group data

```sql
query=> SELECT COUNT(abbrev) AS ct, abbrev
FROM pg_timezone_names
WHERE is_dst = 't' -- dst means daylight saving time
GROUP BY abbrev
HAVING COUNT(abbrev) > 10;
```

## Regular Expression

- A text based programming language
- Clever wild-card strings for matching and parsing text
- Widely available
- Unix commands like "grep"
- Virtually every programming language
- Subtle differences across implementations
- PostgreSQL uses the POSIX variant

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
| ~        | Matches                                             |
| ~*       | Matches case insensitive                            |
| !~       | Does not match                                      |
| !~*      | Does not match case insensitive                     |

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

```sql
query=> SELECT * FROM account WHERE email='ray@gmail.com';
query=> SELECT content FROM comment WHERE account_id = 7;

-- example of sub-query
example=> SELECT content FROM comment
WHERE account_id = (SELECT id FROM account WHERE email='ray@gmail.com');
```

## Concurrency

- Database are designed to accept SQL commands from a variety of source simultaneously and make them atomically

**Atomicity**
- To implement atomicity, PostgreSQL 'locks' areas before it start on SQL command that might change an area of the database
- All other access to that area must wait until the area is unlocked

```sql
example=> UPDATE track SET count=count+1 WHERE id=42;

-- behind the process
flow=> LOCK ROW 42 OF track
READ count FROM track ROW 42
count = count + 1
WRITE count TO track ROW 42
UNLOCK ROW 42 OF track
```

- Single SQL Statements are Atomic
  - Not just update statement, insert statement also atomic
- All the inserts will work and get a unique primary key
- From below, which account gets which key is not predictable

```sql
example=> INSERT INTO account(email) VALUES ('ed@umich.edu');
example=> INSERT INTO account(email) VALUES ('sue@umich.edu');
example=> INSERT INTO account(email) VALUES ('shally@umich.edu');
```

**Compound Statements**
- There are statements which do more than one things in one statement for efficiency and concurrency.

```sql
-- need more explanation
example=> INSERT INTO fav (post_id, account_id, howmuch)
VALUES (1,1,1)
RETURNING *;

example=> UPDATE fav SET howmuch=howmuch+1
WHERE post_id = 1 AND account_id = 1
RETURNING *;
```

We use RETURNING feature a lot

### ON CONFLICT - Like Try and Expect

- Sometimes you "bump into" a constrain on purpose
- This is same like try and except statement in python

```sql
-- fail statement
example=> INSERT INTO fav (post_id, account_id, howmuch)
VALUES (1,1,1)
RETURNING *;

-- success statement
example=> INSERT INTO fav (post_id, account_id, howmuch)
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

```sql
-- Syntax
-- create a transaction and save successfully
BEGIN
UPDATE
COMMIT

-- create a transaction and revert back
BEGIN
UPDATE
ROLLBACK
```

```sql
-- revert scenario
example=> BEGIN;
SELECT howmuch FROM fav WHERE account_id=1 AND post_id=1 FOR UPDATE OF fav;
-- Time passes ...
UPDATE fav SET howmuch=999 WHERE account_id=1 AND post_id=1;
ROLLBACK;
SELECT howmuch FROM fav WHERE account_id=1 AND post_id=1;

-- commit scenario
example=> BEGIN;
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

```sql
-- consider the table name fav in it we have updated_at field which will update automatically whenever the user modify the data

-- old query before stored procedure
query=> UPDATE fav SET howmuch = howmuch + 1, updated_at = NOW()
WHERE post_id = 1 and account_id = 1;

-- using functions and trigger for automate updated_at
query=> CREATE OR REPLACE FUNCTION trigger_set_timestamp()
RETURNS TRIGGER AS $$
BEGIN
  NEW.updated_at = NOW();
  RETURN NEW;
END;
$$ LANGUAGE plpgsql;

query=> CREATE TRIGGER set_timestamp
BEFORE UPDATE ON fav
FOR EACH ROW
EXECUTE PROCEDURE trigger_set_timestamp();

-- new query after stored procedure
query=> UPDATE fav SET howmuch=howmuch+1
WHERE post_id = 1 and account_id = 1;
```

## If/Else in Postgres - CASE THEN ELSE END

```sql
syntax=> SELECT (CASE WHEN (condition)
THEN ...
ELSE ...
END
)
```

```sql
example=> SELECT (CASE WHEN (random() < 0.5)
  THEN 'https://www.pg4e.com/neon/'
  ELSE 'http://www.pg4e.com/LEMONS/'
  END
) || generate_series(100000, 200000)
```

## INDEX

- Index are used for reduce the query time with the help of algorithms like B-Tree, Hash, GIN and so on
- For Natural Language we need efficient index method with stemming, casing, eliminating stop-words, weighting and ranking

### INDEX - How to make an index for a table?

- First create a table and then create a index and link the table with index
- This will create B-Tree index but it **allows duplicate**

```sql
-- Consider we have a table with text field
query=> CREATE TABLE textfun (
  content TEXT
);

-- To create index
query=> CREATE INDEX textfun_b ON textfun (content);
```

### INDEX - How to make an unique index?

- First create a table and then create a index and link the table with index
- This will create B-Tree index but it **does not allows duplicate**

```sql
syntax=> CREATE UNIQUE INDEX index_name ON table(field);
```

```sql
example=> CREATE UNIQUE INDEX cr2_md5 ON cr2(md5(url));
```

### INDEX - How to make a GIN index?

- The index expression must be exact match with where clause.

```sql
-- use lecture 5 docs table
query=> CREATE INDEX gin1 ON docs USING gin(string_to_array(doc, ' ') _text_ops); -- for postgres 9
query=> CREATE INDEX gin1 ON docs USING gin(string_to_array(doc, ' ') array_ops); -- for postgres >= 11
-- to use with WHERE clause
query=> SELECT id, doc FROM docs WHERE {learn} <@ string_to_array(doc, ' ');
-- run explain analyze to check the performance
```

**Notes:**

- The query expression must be same as index expression like string_to_array('string', 'DELIMITER')
- Use **<@** operator
- GiST and GIN index are same, explore the google while making GiST index

### INDEX - How to make an Natural Language Inverted Index with Postgres?

- With the help of to_tsvector() and to_tsquery() functions and @@ operator

```sql
query=> CREATE INDEX gin ON docs USING gin(to_tsvector('english', doc));
-- to query
query=> SELECT id, doc FROM docs WHERE to_tsquery('english', 'teaching') @@ to_tsvector('english', doc);
-- run explain analyze
```

### INDEX - Index Maintenance!

- Check out this official doc of [Index Maintenance](https://wiki.postgresql.org/wiki/Index_Maintenance)

**Sample query to pull the number of rows, indexes, and some info about those indexes for each table**

```sql
query=> SELECT
    pg_class.relname,
    pg_size_pretty(pg_class.reltuples::bigint)            AS rows_in_bytes,
    pg_class.reltuples                                    AS num_rows,
    COUNT(*)                                              AS total_indexes,
    COUNT(*) FILTER ( WHERE indisunique)                  AS unique_indexes,
    COUNT(*) FILTER ( WHERE indnatts = 1 )                AS single_column_indexes,
    COUNT(*) FILTER ( WHERE indnatts IS DISTINCT FROM 1 ) AS multi_column_indexes
FROM
    pg_namespace
    LEFT JOIN pg_class ON pg_namespace.oid = pg_class.relnamespace
    LEFT JOIN pg_index ON pg_class.oid = pg_index.indrelid
WHERE
    pg_namespace.nspname = 'public' AND
    pg_class.relkind = 'r'
GROUP BY pg_class.relname, pg_class.reltuples
ORDER BY pg_class.reltuples DESC;
```

### INDEX - How to delete a index?

Just like to drop a table - `DROP INDEX index_name;`

# How to Questions? - Beyond CRUD

## How to use GENERATED ALWAYS AS?

While developing saving table, I have 3 columns income, expense and balance. What I want to do is to auto store balance column based on income - expense formula


```sql
-- Generated by AI
CREATE TABLE saving (
  id SERIAL PRIMARY KEY,
  date DATE NOT NULL UNIQUE,
  income NUMERIC NOT NULL,
  expense NUMERIC NOT NULL,
  balance NUMERIC GENERATED ALWAYS AS (income - expense) STORED
);
```

## How to generate random data(s) in Database?

```sql
query=> SELECT 'https://pg4e.com/neon/' || TRUNC(RANDOM() * 1000000) || REPEAT('LEMON', 5) || GENERATE_SERIES(1, 5);
-- https://pg4e.com/neon/706794LEMONLEMONLEMONLEMONLEMON1
-- https://pg4e.com/neon/937655LEMONLEMONLEMONLEMONLEMON2
-- https://pg4e.com/neon/977594LEMONLEMONLEMONLEMONLEMON3
-- https://pg4e.com/neon/721555LEMONLEMONLEMONLEMONLEMON4
-- https://pg4e.com/neon/16917LEMONLEMONLEMONLEMONLEMON5
```

### How to generate random data(s) and insert into on table with if/else condition in Database?

```sql
syntax=> INSERT INTO table_name(col_name)
SELECT (CASE WHEN (condition)
        THEN 'text_1'
        ELSE 'text_2'
        END
) || GENERATE_SERIES(start, end);
```

```sql
example=> INSERT INTO textfun(content)
SELECT (CASE WHEN (random() < 0.5)
        THEN 'https://www.pg4e.com/neon'
        ELSE 'https://www.pg4e.com/lemon'
        END
) || GENERATE_SERIES(100000, 200000);
```

## How to check table size in database?

- Enter the table name in string

```sql
syntax=> SELECT pg_relation_size('table_name'), pg_indexes_size('table_name');
```

```sql
example=> SELECT pg_relation_size('textfun'), pg_indexes_size('textfun'), pg_size_pretty(pg_relation_size('textfun'));
```

## How to optimize the SQL queries?

- For **B-Tree** we can commend the sequence search to **stop**, after it read the one and only data in a table with **LIMIT** clause

```sql
-- Worst performance (If we know there are seq records from 1 to 200, below query will execute after it find value (in 150 row) since it don't know)
example=> explain analyze select content from textfun where content like '%150%';

-- Best performance (If we know there are seq records from 1 to 200, below query will stop after it find value (in 150 row) since it we know)
example=> explain analyze select content from textfun where content like '%150%' LIMIT 1;
```

- Don't use sub-queries and sub-select

**Notes:** Check out _6. Index Choices and Index Techniques_ from Postgres for Everybody course

#### How to optimize the B-tree index for better performance?

- Create a index for the table with md5 hash fields
- Then query the result with md5 hash function in WHERE clause

```sql
example=> CREATE UNIQUE INDEX crl_md5 ON CRL(MD5(url));
-- now check the size of table and index (which is much more smaller)

-- bad performance - Check with Explain
example=> SELECT * FROM crl WHERE url='lemons'; -- take full table scan

-- good performance - Check with Explain
example=> SELECT * FROM crl WHERE MD5(url)=MD5('lemons'); -- takes index scan and much faster
```

#### How to optimize the Hash index for better performance?

- hash index cannot be unique
- only good for exact match

```sql
example=> CRATE TABLE crl_4 (
  id SERIAL
  url TEXT
  content TEXT
);

example=> CREATE INDEX crl_4_hash ON crl_4 USING hash (url);

-- check the table and index size
-- check the explain analyze
```

## How to check postgres version?

```sql
query=> SELECT version();
```

## How to delete a trigger?

```sql
example=> DROP TRIGGER trigger_name ON table_name;
```

## What is this?

```sql
what=> SELECT char_length('学习管理'), octet_length('学习管理'), bit_length('学习管理'), ascii('学');

what=> SHOW SERVER_ENCODING;
```
