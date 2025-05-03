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
      - [REFERENCES table\_name(primary\_key)](#references-table_nameprimary_key)
  - [Constraints in PostgreSQL](#constraints-in-postgresql)
      - [UNIQUE / UNIQUE()](#unique--unique)
      - [ON DELETE CASCADE](#on-delete-cascade)
      - [PRIMARY KEY / PRIMARY KEY()](#primary-key--primary-key)
  - [Functions in PostgreSQL](#functions-in-postgresql)
      - [NOW()](#now)
  - [Indexes](#indexes)

<br>

# What is SQL?

SQL stands for Structured Query Language. SQL let you efficiently access and manipulate the relational database, it perform the operations like querying, creating and manipulating, and managing access permission.

- Don't forget to add the **;** (semi-colon) at the end of the each statement.
- Use single quotes for string literals - `SELECT * FROM user WHERE email='ray@gmail.com';`

> SQL allows us to describe the shape of data to be stored and give many hints to the database engine as to how we will be accessing or using the data. SQL is a language that provides us operations to Create, Read, Update, and Delete (CRUD) our data in a database. - 'Charles Severance'

## Components of SQL System

|                                                           |                            |                                                          |
| --------------------------------------------------------- | -------------------------- | -------------------------------------------------------- |
| <li>Database</li>                                         | <li>Table</li>             | <li><a href="../Learn-SQL/SQL-Queries.md">Query</a></li> |
| <li>Security</li>                                         | <li>Permissions</li>       | <li>Joins</li>                                           |
| <li><a href="#constraints-in-sql">Constraints</a></li>    | <li>Stored</li> Procedures | <li>Transactions</li>                                    |
| <li><a href="#data-types-in-sql">Data Type</a></li>       | <li>Indexes</li>           | <li>Views</li>                                           |
| <li><a href="#functions-in-postgresql">Functions</a></li> |                            |                                                          |

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
#### REFERENCES table_name(primary_key)
- References keyword makes the relationship between table.
- Check out this Example: [SQL Query to build the relationship](../Relational-Database-Design/Design-Intro.md#sql-query-to-build-the-relationship)

Notes: ... <br>
Articles: [Data Types in PostgreSQL](https://www.postgresql.org/docs/current/datatype.html)

## Constraints in PostgreSQL

#### UNIQUE / UNIQUE()
**UNIQUE**
- It make sure that every record (row) value will be unique, and postgres automatically create index for this field.

**UNIQUE(field1, field2)**
- UNIQUE(title, album) - This make suer that the combination of field 1 (song name) and field 2 (album) must to be unique, for example if the song name 'Thank, Thank' have presented in 2 different albums like 'Vol 25', 'Vol 35'

#### ON DELETE CASCADE
- Basically says if parent/reference entry is deleted, delete everything belong to that id from this table also.
#### PRIMARY KEY / PRIMARY KEY()
- Primary key says make this field as auto increment integer field and index it and reference it

## Functions in PostgreSQL

#### NOW()
- for DateTime field NOW() function is used to get to current time stamp

## Indexes

Index is a technique used to quickly access the single data from million or billion of record with help of Hash and Tree mechanism (or) algorithms.

- Index automatically created for primary keys, logical keys (mostly have UNIQUE keyword).

**Tree**
- Binary Trees (B-Trees) works log amortized time, It optimized for system that read and write large block / amount of data.
- Tree index is good for exact match lookup, sorting, range lookups, prefix lookup (mostly for strings)

**Hashes**

> A hash function is any algorithm or subroutine that maps large data sets to smaller data sets, called keys. For example, a single integer can serve as an index to an array (cf. associative array). The values returned by a hash function are called hash values, hash codes, hash sums, checksums, or simply hashes. Hash functions are mostly used to accelerate table lookup or data comparison tasks such as finding items in a database ... - 'Charles Severance'
- Hashes are so fast and only good for exact match, like Primary Keys, GUID
- Hashes is **not** good for prefix matching, sorting

[Learn SQL Queries >>](./SQL-Queries.md)