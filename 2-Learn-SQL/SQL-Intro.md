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
        - [UNIQUE](#unique)
        - [UNIQUE(field1, field2)](#uniquefield1-field2)
      - [AS](#as)
      - [ON DELETE](#on-delete)
        - [CASCADE](#cascade)
        - [RESTRICT](#restrict)
        - [SET NULL](#set-null)
      - [PRIMARY KEY / PRIMARY KEY()](#primary-key--primary-key)
      - [REFERENCES table\_name(primary\_key)](#references-table_nameprimary_key)
      - [JOIN](#join)
        - [INNER JOIN / JOIN](#inner-join--join)
        - [CROSS JOIN](#cross-join)
        - [LEFT JOIN](#left-join)
      - [Index Constrains](#index-constrains)
        - [\_text\_ops](#_text_ops)
        - [array\_ops](#array_ops)
        - [jsonb\_path\_ops](#jsonb_path_ops)
  - [Functions in PostgreSQL](#functions-in-postgresql)
      - [NOW()](#now)
      - [TRUNC()](#trunc)
      - [REPEAT()](#repeat)
      - [GENERATE\_SERIES()](#generate_series)
      - [RANDOM()](#random)
    - [Text Functions](#text-functions)
      - [UPPER()](#upper)
      - [LOWER()](#lower)
      - [RIGHT()](#right)
      - [LEFT()](#left)
      - [STRPOS() - Starting Position](#strpos---starting-position)
      - [SUBSTR() - Sub String](#substr---sub-string)
      - [SPLIT\_PART()](#split_part)
      - [TRANSLATE()](#translate)
      - [ASCII()](#ascii)
      - [CHR()](#chr)
      - [CHAR\_LENGTH()](#char_length)
      - [OCTET\_LENGTH()](#octet_length)
      - [BIT\_LENGTH()](#bit_length)
      - [SUBSTRING()](#substring)
      - [REGEXP\_MATCHES()](#regexp_matches)
      - [STRING\_TO\_ARRAY()](#string_to_array)
      - [UNNEST()](#unnest)
      - [to\_tsvector()](#to_tsvector)
      - [to\_tsquery()](#to_tsquery)
      - [ts\_rank()](#ts_rank)
      - [ts\_rank\_cd()](#ts_rank_cd)
      - [plainto\_tsquery()](#plainto_tsquery)
      - [phraseto\_tsquery()](#phraseto_tsquery)
      - [websearch\_to\_tsquery()](#websearch_to_tsquery)
    - [pg\_typeof()](#pg_typeof)
    - [COALESCE()](#coalesce)
    - [Hash Functions](#hash-functions)
      - [MD5()](#md5)
      - [SHA256()](#sha256)
    - [Vital](#vital)
      - [pg\_relation\_size()](#pg_relation_size)
      - [pg\_size\_pretty()](#pg_size_pretty)
      - [pg\_indexes\_size()](#pg_indexes_size)
    - [Extra](#extra)
      - [jsonb\_set()](#jsonb_set)
  - [Indexes](#indexes)
      - [B-Tree](#b-tree)
      - [Hashes](#hashes)
    - [Inverted Index](#inverted-index)
      - [GIN - Generalized Inverted Index](#gin---generalized-inverted-index)
      - [GiST](#gist)
  - [Text in Postgres](#text-in-postgres)
    - [Stop Words](#stop-words)
    - [Stemming](#stemming)
    - [Python and Unicode](#python-and-unicode)

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

##### UNIQUE

- It make sure that every record (row) value will be unique, and postgres automatically create index for this field.

##### UNIQUE(field1, field2)

- UNIQUE(title, album) - This make suer that the combination of field 1 (song name) and field 2 (album) must to be unique, for example if the song name 'Thank, Thank' have presented in 2 different albums like 'Vol 25', 'Vol 35'

#### AS

- Alias, It used as column, tables, views, functions, expression or sub-query aliasing to import readability

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
- Check out this example: [SQL Query to build the relationship](../Relational-Database-Design/Design-Intro.md#sql-query-to-build-the-relationship)

#### JOIN

##### INNER JOIN / JOIN

- The JOIN operation links across several tables as part of a SELECT operation.
- You must tell the JOIN how to use the keys that make the connection between the tables using an ON clause.

##### CROSS JOIN

- Rarely used

##### LEFT JOIN

- A LEFT JOIN is used to combine rows from two tables based on a related column, while ensuring that all rows from the left table are included in the result, even if there is no matching row in the right table. If no match is found in the right table, the result will contain NULL values for the columns from the right table. (Generated by AI)
- It allows us to do a conditional lookup without losing all the data

#### Index Constrains

##### _text_ops

- _text_pos means Text Operator
- Used as constrain while make GIN index if postgres version is less than 11

##### array_ops

- array_ops means Array Operator
- If postgres version >= 11 we use this constrain while making gin index

##### jsonb_path_ops

- Used as  constrain while making GIN index for jsonb column
- It uses @> operator

## Functions in PostgreSQL

#### NOW()

- DateTime field NOW() function is used to get to current date and time stamp with timezone

```sql
example=> SELECT NOW(); -- 2025-05-12 10:23:53.684396+05:30
```

#### TRUNC()

- This function will convert float number to integer

```sql
example=> SELECT TRUNC(RANDOM() * 100); -- 17
```

#### REPEAT()

- This function will take 2 argument string and no of times to repeat the string - ('text', 5)
- It will generate the result in one line (horizontally)

```sql
examplesql=> SELECT REPEAT('ABC', 3); -- ABCABCABC
example=> SELECT REPEAT('ABC ', 3); -- ABC ABC ABC
```

#### GENERATE_SERIES()

- This function will take 2 argument starting integer and ending integer - (1, 5)
- It will generate the results in rows (vertically)

```sql
example=> SELECT GENERATE_SERIES(1, 5);
-- 1
-- 2
-- 3
-- 4
-- 5
```

#### RANDOM()

- This function will generate random float number with 17 digit decimal place from 0 (inclusive) to 1 (exclusive)

```sql
example=> SELECT RANDOM(); -- 0.6359592059634787
```

### Text Functions

**Notes:**
- [Official Doc](https://www.postgresql.org/docs/current/functions-string.html)
- '8 bit of Memory' as a 'byte' of memory

#### UPPER()

- This function return the string in all upper case
- It will both be used in SELECT and WHERE clause as well

```sql
example=> SELECT UPPER('aravind'); -- ARAVIND
```

#### LOWER()

- This function return the string in all lower case
- It will both be used in SELECT and WHERE clause as well

```sql
example=> SELECT LOWER('ARAVIND'); -- aravind
```

#### RIGHT()

- This function will take string and no of character as argument and return the right side of the result - (str, no_of_char)
- It will both be used in SELECT and WHERE clause as well

```sql
example=> SELECT RIGHT('https://www.pg4e.com/LEMONS/150000', 4); -- 0000
```

#### LEFT()

- This function will take string and no of character as argument and return the left side of the result - (str, no_of_char)
- It will both be used in SELECT and WHERE clause as well

```sql
example=> SELECT LEFT('https://www.pg4e.com/LEMONS/150000', 4); -- http
```

#### STRPOS() - Starting Position

- This function will take the 2 arguments like (str, 'find_str') and return the position where the character start
- Index start with 1 (not zero (0) like python)

```sql
example=> SELECT STRPOS('https://www.pg4e.com/LEMONS/150000', 'ttps://'); -- 2
```

#### SUBSTR() - Sub String

- This function will take 3 arguments (str, start, end) where start and end characters include.

```sql
example=> SELECT SUBSTR('https://www.pg4e.com/LEMONS/150000', 2, 4); -- ttps
```

#### SPLIT_PART()

- This function will take 3 arguments - (str, delimiter, ele_pos_to_return)
- It is similar like python split

```sql
example=> SELECT SPLIT_PART('apple,banana,cherry', ',', 1); -- 'apple'
example=> SELECT SPLIT_PART('apple,,banana,cherry', ',', 2); -- ''
example=> SELECT SPLIT_PART('apple,banana,cherry', ',', 2); -- 'banana'
```

#### TRANSLATE()

- This function is similar like find and replace
- It will take 3 arguments ('str', find, replace)
- The find and replace part of argument must be similar no_of_character

```sql
example=> SELECT TRANSLATE('https://www.pg4e.com/LEMONS/150000', 'th.p/', 'TH!P_'); -- HTTPs:__www!Pg4e!com_LEMONS_150000
```

#### ASCII()

- This function tell us the numeric value of single ASCII character

```sql
example=> SELECT ASCII('H'), ASCII('E'), ASCII('L'), ASCII('h'), ASCII('e'), ASCII('l');
 ascii | ascii | ascii | ascii | ascii | ascii
-------+-------+-------+-------+-------+-------
    72 |    69 |    76 |   104 |   101 |   108
```

#### CHR()

- This function maps from Integer to ASCII character

```sql
example=> SELECT CHR(72), CHR(42), CHR(1), CHR(231), CHR(20013);
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

#### SUBSTRING()

- This function return the substring of the column
- It gets and return the first match in a text column

```sql
example=> SELECT DISTINCT SUBSTRING(email FROM '.+@(.*)$') FROM em; -- return all the characters after @ symbol
```

#### REGEXP_MATCHES()

- This function gets and return the array of matches
- It will take 3 arguments (col_name, 'expression', 'flag')

```sql
example=> SELECT REGEXP_MATCHES(tweet, '#([A-Za-z0-9_]+)', 'g') FROM tw; -- return all the character after # symbol
```

#### STRING_TO_ARRAY()

- Like python split function

```sql
example=> SELECT STRING_TO_ARRAY('Hello World', ' '); -- {Hello,World}
```

#### UNNEST()

- Similar to generate_series()
- It takes an array and expands it to rows
- Keyname: Horizontal to Vertical

```sql
example=> SELECT UNNEST(STRING_TO_ARRAY('Hello World', ' '));
-- Hello
-- World
```

#### to_tsvector()

- ts_vector means text string vector
- It take 2 arguments the Language and the string
- It process all the necessary steps like, stemming, removing stop-word and so on
- It also checks ordering of the function like sql followed by python

#### to_tsquery()

- ts_query also take 2 arguments same as above like language and string
- It used to query the index which created from ts_vector()
- It uses **@@** operator to check with to_tsvector()

```sql
query=> SELECT to_tsquery('english', 'teaching'); -- teach
query=> SELECT to_tsquery('english', 'teaches'); -- teach
query=> SELECT to_tsquery('english', 'and'); -- report error
query=> SELECT to_tsquery('english', 'SQL'); -- sql (return lower case sql since it is not a stop word, or no stem for it)
query=> SELECT to_tsquery('english', 'Teach | teaches | teaching | and | the | if');
         to_tsquery
-----------------------------
 'teach' | 'teach' | 'teach'
```

```sql
-- this function also take the special operators
query=> SELECT to_tsquery('english', 'learn & teach'); -- must both words in the sentences
query=> SELECT to_tsquery('english', 'pearson <-> learning'); -- person should comes first before learning (ordering)
query=> SELECT to_tsquery('english', '! learn & teach'); -- works as not operator, no learn but search teach only
query=> SELECT to_tsquery('english', '(learn & teach'); -- ( produce a syntax error - to overcome this we use plainto_query
```

#### ts_rank()

- Calculating a ranking is really cheap
- ts_rank is goes into SELECT clause not the WHERE clause
- It take 2 arguments which are to_tsvector and to_tsquery
- It check how close the vector and query they are
- ? Need more information

#### ts_rank_cd()

- It is same as above which use different calculation

**Note:** There are many ranking system, lookup on those in official postgres documentation

#### plainto_tsquery()

- It is similar to `to_tsquery('english', 'q & q')`, but this query will get input from user (while search), which they didn't know the fancy operators

```sql
-- It implies & between all of the query
query=> SELECT plainto_tsquery('english', 'SQL Python');
 plainto_tsquery
------------------
 'sql' & 'python'
```

#### phraseto_tsquery()

- ? Need more information
- If you want to see the character followed after another use it
- For example, if user (search) want to see 'python' followed by 'sql' use it

```sql
query=> SELECT phraseto_tsquery('english', 'SQL Python');
  phraseto_tsquery
--------------------
 'sql' <-> 'python'
-- above query is same as SELECT to_tsquery('english', 'pearson <-> learning');
```

#### websearch_to_tsquery()

- ? Need more information

```sql
query=> SELECT to_tsquery('english', '! learn & teach'); -- works as not operator, no learn but search teach only
query=> SELECT websearch_to_tsquery('english', '-learn teach') -- this web search query is exactly same as above, but use google syntax - (minus) operator instead of ! (exclamation) operator
```

**Notes:** Check out this official doc [12.3. Controlling Text Search](https://www.postgresql.org/docs/current/textsearch-controls.html)

### pg_typeof()

- This function takes the column as argument and return it's data type
- Similar to python type() function

```sql
syntax=> SELECT pg_typeof(expression);
syntax=> SELECT col_name, pg_typeof(col_name) FROM table_name;
```

### COALESCE()

- Null Coalescing - return the first non-null in a list

```sql
example=> SELECT COALESCE(NULL, NULL, 'umsi'); -- umsi
example=> SELECT COALESCE('SQL', NULL, 'umsi'); -- SQL
```

### Hash Functions

#### MD5()

- This function convert the given string into MD5 Hash

```sql
example=> SELECT MD5('hello'); -  5d41402abd4b2r76bs719d91101xxxxx
```

#### SHA256()

- This function convert the given string into SHA256 Hash

```sql
example=> SELECT SHA256('hello'); -  \x2cf24dba5fb0axx26exb2axxb9e29e1c161e5cxx425ed30r336d93xb98x4
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

### Extra

#### jsonb_set()

- At the time of lecture this function is bad and need convert the result to text and then jsonb
- don't like it, don't use it

## Indexes

Index is a technique used to quickly access the single data from million or billion of record with help of algorithms like Hash and B-Tree mechanism.

- Index automatically created for primary keys, logical keys (mostly have UNIQUE keyword).
- Index is fast for insert, delete, update and read the data from the table.
- Index is no good for TEXT field
- **The goal of the index is to ultimately reduce the Sequence scan** - Sequence scan means you are failed
- Heap scan, index scan, recheck - good things to see while running _explain analyze_

**Types of Indexes**
- B-Tree
  - default for many application
  - automatically balanced as it grows
- BRIN
  - Block Range INdex
  - Smaller / faster if data is mostly sorted
- Hash
  - Quick look up for long key strings
- GIN
  - Generalized Inverted Index
  - Multiple values in a column
- GiST
  - Generated Search Tree
- SP-GiST
  - Space Partitioned Generated Search Tree

#### B-Tree

- Binary Trees (B-Trees) works log amortized time, It optimized for system that read and write large block / amount of data.
- Tree index is good for exact match lookup, sorting, (compare) - <, >,  range lookups, prefix lookup (mostly for strings)
- It good for String, Number and Date Keys
- It great balance for cost of insert and update

**How to check the B-Tree Index performance**
Below query will return the execution time and some details about the performance, It is a psql specific command.
```sql
example=> explain analyze SELECT content FROM textfun WHERE content LIKE 'racing%';
```

#### Hashes

> A hash function is any algorithm or subroutine that maps large data sets to smaller data sets, called keys. For example, a single integer can serve as an index to an array (cf. associative array). The values returned by a hash function are called hash values, hash codes, hash sums, checksums, or simply hashes. Hash functions are mostly used to accelerate table lookup or data comparison tasks such as finding items in a database ... - 'Charles Severance'

- Hashes are so fast and only **good for exact match**, like Primary Keys, GUID
- Hashes is **not** good for prefix matching, sorting

A hash function is any function that can be used to map data of arbitrary size onto data of a fixed size.

> A hash function is a function that takes an input (or 'message') and returns a fixed-size string of bytes. The output, typically a number, is called the hash code or hash value. The main purpose of a hash function is to efficiently map data of arbitrary size to fixed-size values, which are often used as indexes in hash tables - 'MS Copilot'

**Uses of Hashes**
- Checksum
- Cryptography / Signature
- Fast lookup of data - Python Dictionaries and Database Tables, indexes

**Hash functions**
- Deterministic - There can be no randomness - must get the same output for the same input
- Uniform Distribution - Should have an equal chance of generating any value with the range of its outputs - values don't cluster or collide
- Sensitive - Any change in input should provide a change in output
- One-way - You should not be able to derive the input from the output (cannot reverse)

### Inverted Index

There are 2 types of Inverted Index
- GIN - Generalized Inverted Index
- GiST - Generalized Search Tree

**Basic**
- It uses "<@" operator
- It works with array

#### GIN - Generalized Inverted Index

- The preferred text search type index
- Very efficient for lookup and search for exact match
- It never look more rows than it needs to
- Can be costly when inserting or updating data

#### GiST

- It sort of reduced size (it uses hashing)
- Smaller and quicker for update
- If you query once a while, then GiST is better idea

**Downside** - It might read more block then necessary

## Text in Postgres

**Character Set** - we can't afford 32 bit characters
- UTF-8 is a compression scheme for Unicode
  - Represents 21 bits in 8-32 bits
  - 0-128 are ASCII
  - 128-255 are signals

### Stop Words

- Simply know as Ignore words (for my understanding)
- While query the database we tell postgres to ignore these words
- All language have repeated and simple words like - and, is, the

### Stemming

- The technical name for stemming is 'Conflation'
- The idea of stemming is remove the word from to it base form like musical to music, teaching to teach, teaches to teach.

### Python and Unicode

- Strings in memory are Unicode
- The "bytes" type is for 8-bit characters
- Strings "at rest" are generally stored UTF-8 for space and interoperability
  - Files - tell explicit when opening a file in encoding=None[UTF8] argument
  - Network resources - use decode() method
  - Database tables - psycopg2 automatically decode

```py
# Example

>>> x = b'abc'
>>> type (x) # <class 'bytes'>
>>> x = '이광춘'
>>> type (x) # <class 'str'>
>>> x = u'이광춘'
>>> type (x) # <class 'str'>
```

[Learn SQL Queries >>](./SQL-Queries.md)