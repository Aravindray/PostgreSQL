## Table of Content
- [What is SQL?](#what-is-sql)
  - [Components of SQL System](#components-of-sql-system)
  - [Category of SQL Commands](#category-of-sql-commands)
      - [DDL - Data Definition Language](#ddl---data-definition-language)
      - [DQL - Data Query Language](#dql---data-query-language)
      - [DML - Data Manipulation Language](#dml---data-manipulation-language)
      - [DCL - Data Control Language](#dcl---data-control-language)
      - [TCL - Transaction Control Language](#tcl---transaction-control-language)
  - [Data Types in PostgreSQL](#data-types-in-postgresql)
      - [CHAR(n)](#charn)
      - [VARCHAR(n)](#varcharn)
      - [TEXT](#text)
      - [BINARY (rarely used)](#binary-rarely-used)
      - [SMALLINT](#smallint)
      - [INTEGER](#integer)
      - [BIGINT](#bigint)
      - [REAL](#real)
      - [DOUBLE PRECISION](#double-precision)
      - [NUMERIC](#numeric)
      - [TIMESTAMP](#timestamp)
      - [DATE](#date)
      - [TIME](#time)
      - [SERIAL](#serial)
  - [Constraints in PostgreSQL](#constraints-in-postgresql)
      - [UNIQUE / UNIQUE()](#unique--unique)
      - [ON DELETE](#on-delete)
        - [CASCADE](#cascade)
        - [RESTRICT](#restrict)
        - [SET NULL](#set-null)
      - [PRIMARY KEY / PRIMARY KEY()](#primary-key--primary-key)
      - [REFERENCES table\_name(primary\_key)](#references-table_nameprimary_key)
      - [JOIN](#join)
        - [INNER JOIN / JOIN](#inner-join--join)
        - [CROSS JOIN](#cross-join)
  - [Functions in PostgreSQL](#functions-in-postgresql)
      - [NOW()](#now)
      - [TRUNC()](#trunc)
      - [REPEAT()](#repeat)
      - [GENERATE\_SERIES()](#generate_series)
      - [RANDOM()](#random)
    - [Text Functions](#text-functions)
      - [UPPER](#upper)
      - [LOWER](#lower)
      - [RIGHT](#right)
      - [LEFT](#left)
      - [STRPOS (Starting Position)](#strpos-starting-position)
      - [SUBSTR (Sub String)](#substr-sub-string)
      - [SPLIT\_PART](#split_part)
      - [TRANSLATE()](#translate)
      - [ASCII()](#ascii)
      - [CHR()](#chr)
      - [CHAR\_LENGTH()](#char_length)
      - [OCTET\_LENGTH()](#octet_length)
      - [BIT\_LENGTH()](#bit_length)
    - [Hash Functions](#hash-functions)
      - [MD5](#md5)
      - [SHA256](#sha256)
    - [Vital](#vital)
      - [pg\_relation\_size()](#pg_relation_size)
      - [pg\_size\_pretty()](#pg_size_pretty)
      - [pg\_indexes\_size()](#pg_indexes_size)
  - [Indexes](#indexes)
    - [B-Tree](#b-tree)
    - [Hashes](#hashes)
  - [Text in Postgres](#text-in-postgres)

<br>

# What is SQL?

SQL stands for Structured Query Language. SQL let you efficiently access and manipulate the relational database, it perform the operations like querying, creating and manipulating, and managing access permission.

- Don't forget to add the **;** (semi-colon) at the end of the each statement.
- Use single quotes for string literals - `SELECT * FROM user WHERE email='ray@gmail.com';`

> SQL allows us to describe the shape of data to be stored and give many hints to the database engine as to how we will be accessing or using the data. SQL is a language that provides us operations to Create, Read, Update, and Delete (CRUD) our data in a database. - 'Charles Severance'

## Components of SQL System

|                                                               |                                                                         |                                                                   |
| ------------------------------------------------------------- | ----------------------------------------------------------------------- | ----------------------------------------------------------------- |
| <li>Database</li>                                             | <li>Table</li>                                                          | <li><a href="./SQL-Queries.md">Query</a></li>                     |
| <li>Security</li>                                             | <li>Permissions</li>                                                    | <li><a href="./SQL-Queries.md#join-operations">Joins</a></li>     |
| <li><a href="#constraints-in-postgresql">Constraints</a></li> | <li><a href="./SQL-Queries.md#stored-procedures">Stored Procedures</li> | <li><a href="./SQL-Queries.md#concurrency">Concurrency</a></li>   |
| <li><a href="#data-types-in-postgresql">Data Type</a></li>    | <li>Indexes</li>                                                        | <li>Views</li>                                                    |
| <li><a href="#functions-in-postgresql">Functions</a></li>     | <li><a href="./SQL-Queries.md#sub-queries">Sub-Queries</a></li>         | <li><a href="./SQL-Queries.md#transactions">Transactions</a></li> |

## Category of SQL Commands

#### DDL - Data Definition Language
#### DQL - Data Query Language
#### DML - Data Manipulation Language
#### DCL - Data Control Language
#### TCL - Transaction Control Language

## Data Types in PostgreSQL

#### CHAR(n)
- If CHAR(64) - it allocate entire 64 bit space (which means 64 character), we need to store entire 64 bit space
- Best for storing GUID (Global Unique Identifier - format is numbers and letter (A-Z))

#### VARCHAR(n)
- If VARCHAR(128) - depend on the data length it will store the from 1 character to 128 character

#### TEXT
- Get as much space as you need to store paragraph or HTML page
- Not used for Index and Sorting (which means no ORDER BY and WHERE clause used with this data type)

#### BINARY (rarely used)
- Not used for Index and Sorting
- Store small size image

#### SMALLINT
- This type store -32766 to +32766

#### INTEGER
- This type stores up to 2 Billion numbers

#### BIGINT
- This stores 10^18 length of data

#### REAL
- 32-bit [10^38]

#### DOUBLE PRECISION
- 64-bit [10^308]

#### NUMERIC
- This holds accuracy values
- Used for to store money

#### TIMESTAMP
- Format is 'YYYY-MM-DD HH:MM:SS'

#### DATE
- Format is 'YYYY-MM-DD'

#### TIME
- Format is 'HH:MM:SS'

#### SERIAL
- It creates an auto increment integer column
- It used as Primary Key which postgres automatically generate unique sequential value

Notes: ... <br>
Articles: [Data Types in PostgreSQL](https://www.postgresql.org/docs/current/datatype.html)

## Constraints in PostgreSQL

#### UNIQUE / UNIQUE()
**UNIQUE**
- It make sure that every record (row) value will be unique, and postgres automatically create index for this field.
**UNIQUE(field1, field2)**
- UNIQUE(title, album) - This make suer that the combination of field 1 (song name) and field 2 (album) must to be unique, for example if the song name 'Thank, Thank' have presented in 2 different albums like 'Vol 25', 'Vol 35'

#### ON DELETE

##### CASCADE
- Basically says if parent/reference entry is deleted, delete everything belong to that id from this table also.

##### RESTRICT
- This is the default operation
- Don't allow the change that break the constrain

##### SET NULL
- Set the foreign key column in the child rows to null.
- If you decide to set null in tell postgres that this column in integer or integer null.

#### PRIMARY KEY / PRIMARY KEY()
- Primary key says make this field as auto increment integer field and index it and reference it

#### REFERENCES table_name(primary_key)
- References keyword makes the relationship between table.
- Check out this Example: [SQL Query to build the relationship](../Relational-Database-Design/Design-Intro.md#sql-query-to-build-the-relationship)

#### JOIN

##### INNER JOIN / JOIN
- The JOIN operation links across several tables as part of a SELECT operation.
- You must tell the JOIN how to use the keys that make the connection between the tables using an ON clause.

##### CROSS JOIN
- Rarely used

## Functions in PostgreSQL

#### NOW()
- DateTime field NOW() function is used to get to current date and time stamp with timezone

Example
```
=> SELECT NOW(); -- 2025-05-12 10:23:53.684396+05:30
```

#### TRUNC()
- This function will convert float number to integer

Example
```
=> SELECT TRUNC(RANDOM() * 100); -- 17
```

#### REPEAT()
- This function will take 2 argument string and no of times to repeat the string - ('text', 5)
- It will generate the result in one line (horizontally)

Example
```
=> SELECT REPEAT('ABC', 3); -- ABCABCABC
=> SELECT REPEAT('ABC ', 3); -- ABC ABC ABC
```

#### GENERATE_SERIES()
- This function will take 2 argument starting integer and ending integer - (1, 5)
- It will generate the results in rows (vertically)

Example
```
=> SELECT GENERATE_SERIES(1, 5);
-- 1
-- 2
-- 3
-- 4
-- 5
```

#### RANDOM()
- This function will generate random float number with 17 digit decimal place from 0 (inclusive) to 1 (exclusive)

Example
```
=> SELECT RANDOM(); -- 0.6359592059634787
```

### Text Functions

**Notes:**
- [Official Doc](https://www.postgresql.org/docs/current/functions-string.html)
- '8 bit of Memory' as a 'byte' of memory

#### UPPER
- This function return the string in all upper case
- It will both be used in SELECT and WHERE clause as well

Example
```
=> SELECT UPPER('aravind'); -- ARAVIND
```

#### LOWER
- This function return the string in all lower case
- It will both be used in SELECT and WHERE clause as well

Example
```
=> SELECT LOWER('ARAVIND'); -- aravind
```

#### RIGHT
- This function will take string and no of character as argument and return the right side of the result - (str, no_of_char)
- It will both be used in SELECT and WHERE clause as well

Example
```
-- text:
=> SELECT RIGHT('https://www.pg4e.com/LEMONS/150000', 4); -- 0000
```

#### LEFT
- This function will take string and no of character as argument and return the left side of the result - (str, no_of_char)
- It will both be used in SELECT and WHERE clause as well

Example
```
=> SELECT LEFT('https://www.pg4e.com/LEMONS/150000', 4); -- http
```

#### STRPOS (Starting Position)
- This function will take the 2 arguments like (str, 'find_str') and return the position where the character start
- Index start with 1 (not zero (0) like python)

Example
```
=> SELECT STRPOS('https://www.pg4e.com/LEMONS/150000', 'ttps://'); -- 2
```

#### SUBSTR (Sub String)
- This function will take 3 arguments (str, start, end) where start and end characters include.

Example
```
=> SELECT SUBSTR('https://www.pg4e.com/LEMONS/150000', 2, 4); -- ttps
```

#### SPLIT_PART
- This function will take 3 arguments - (str, delimiter, ele_pos_to_return)
- It is similar like python split

Example
```
=> SELECT SPLIT_PART('apple,banana,cherry', ',', 1); -- 'apple'
=> SELECT SPLIT_PART('apple,,banana,cherry', ',', 2); -- ''
=> SELECT SPLIT_PART('apple,banana,cherry', ',', 2); -- 'banana'
```

#### TRANSLATE()
- This function is similar like find and replace
- It will take 3 arguments ('str', find, replace)
- The find and replace part of argument must be similar no_of_character

Example
```
=> SELECT TRANSLATE('https://www.pg4e.com/LEMONS/150000', 'th.p/', 'TH!P_'); -- HTTPs:__www!Pg4e!com_LEMONS_150000
```

#### ASCII()
- This function tell us the numeric value of single ASCII character

Example
```
=> SELECT ASCII('H'), ASCII('E'), ASCII('L'), ASCII('h'), ASCII('e'), ASCII('l');
 ascii | ascii | ascii | ascii | ascii | ascii
-------+-------+-------+-------+-------+-------
    72 |    69 |    76 |   104 |   101 |   108
```

#### CHR()
- This function maps from Integer to ASCII character

Example
```
=> SELECT CHR(72), CHR(42), CHR(1), CHR(231), CHR(20013);
 chr | chr | chr  | chr | chr
-----+-----+------+-----+----
 H   | *   | \x01 |  ç  | 中
```

#### CHAR_LENGTH()
- This function return the character length

#### OCTET_LENGTH()
- This function return the values in byte that actually stored in database

#### BIT_LENGTH()
- This function return result of OCTET_LENGTH() * 8 (times 8) (because 8 bit - 1 byte)

### Hash Functions

#### MD5
- This function convert the given string into MD5 Hash

Example
```
=> SELECT MD5('hello'); -  5d41402abd4b2r76bs719d91101xxxxx
```

#### SHA256
- This function convert the given string into SHA256 Hash

Example
```
=> SELECT SHA256('hello'); -  \x2cf24dba5fb0axx26exb2axxb9e29e1c161e5cxx425ed30r336d93xb98x4
```

### Vital

#### pg_relation_size()
- This will answer the question - How much data is in this currently in the relation / table taking?
- It will take the table_name as argument - pg_relation_size(table_name)
- It will return the size of the table in bytes (Note in postgres table is also know as relation)

#### pg_size_pretty()
- Converts the size from bytes to a more readable format (e.g., KB, MB, GB).
- for example `pg_size_pretty(pg_relation_size('table_name'));`

#### pg_indexes_size()
- This will answer the question - How much data is in this currently in the index taking?
- It will take the table_name as argument, which index is linked - pg_indexes_size(table_name)
- It will return the size of the indexes in bytes

## Indexes

Index is a technique used to quickly access the single data from million or billion of record with help of Hash and B-Tree mechanism (or) algorithms.

- Index automatically created for primary keys, logical keys (mostly have UNIQUE keyword).
- Index is fast for insert, delete, update and read the data from the table.
- Index is no good for TEXT field

### B-Tree
- Binary Trees (B-Trees) works log amortized time, It optimized for system that read and write large block / amount of data.
- Tree index is good for exact match lookup, sorting, (compare) - <, >,  range lookups, prefix lookup (mostly for strings)

**How to check the B-Tree Index performance**

Below query will return the execution time and some details about the performance, It is a psql specific command.
```
=> explain analyze SELECT content FROM textfun WHERE content LIKE 'racing%';
```

### Hashes

> A hash function is any algorithm or subroutine that maps large data sets to smaller data sets, called keys. For example, a single integer can serve as an index to an array (cf. associative array). The values returned by a hash function are called hash values, hash codes, hash sums, checksums, or simply hashes. Hash functions are mostly used to accelerate table lookup or data comparison tasks such as finding items in a database ... - 'Charles Severance'

- Hashes are so fast and only **good for exact match**, like Primary Keys, GUID
- Hashes is **not** good for prefix matching, sorting

A hash function is any function that can be used to map data of arbitrary size onto data of a fixed size.

> A hash function is a function that takes an input (or 'message') and returns a fixed-size string of bytes. The output, typically a number, is called the hash code or hash value. The main purpose of a hash function is to efficiently map data of arbitrary size to fixed-size values, which are often used as indexes in hash tables - 'MS Copilot'

**Uses of Hashes**
- Checksum
- Cryptography / Signature
- Fast lookup of data - Python Dictionaries and Database Tables

**Hash functions**
- Deterministic - There can be no randomness - must get the same output for the same input
- Uniform Distribution - Should have an equal chance of generating any value with the range of its outputs - values don't cluster or collide
- Sensitive - Any change in input should provide a change in output
- One-way - You should not be able to derive the input from the output (cannot reverse)

## Text in Postgres

**Character Set** - we can't afford 32 bit characters
- UTF-8 is a compression scheme for Unicode
  - Represents 21 bits in 8-32 bits
  - 0-128 are ASCII
  - 128-255 are signals

[Learn SQL Queries >>](./SQL-Queries.md)