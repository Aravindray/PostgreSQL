## Table of Content
- [What is SQL?](#what-is-sql)
  - [Components of SQL System](#components-of-sql-system)
  - [Category of SQL Commands](#category-of-sql-commands)
    - [DDL - Data Definition Language](#ddl---data-definition-language)
    - [DQL - Data Query Language](#dql---data-query-language)
    - [DML - Data Manipulation Language](#dml---data-manipulation-language)
    - [DCL - Data Control Language](#dcl---data-control-language)
    - [TCL - Transaction Control Language](#tcl---transaction-control-language)
  - [Data Types in SQL](#data-types-in-sql)

<br>

# What is SQL?

SQL stands for Structured Query Language. SQL let you efficiently access and manipulate the relational database, it perform the operations like querying, creating and manipulating, and managing access permission.

- Don't forget to add the **;** (semi-colon) at the end of the each statement.
- Use single quotes for string literals - `SELECT * FROM user WHERE email='ray@gmail.com';`

## Components of SQL System

|                                                     |                            |                                                          |
| --------------------------------------------------- | -------------------------- | -------------------------------------------------------- |
| <li>Database</li>                                   | <li>Table</li>             | <li><a href="../Learn-SQL/SQL-Queries.md">Query</a></li> |
| <li>Security</li>                                   | <li>Permissions</li>       | <li>Joins</li>                                           |
| <li>Constraints</li>                                | <li>Stored</li> Procedures | <li>Transactions</li>                                    |
| <li><a href="#data-types-in-sql">Data Type</a></li> | <li>Indexes</li>           | <li>Views</li>                                           |

## Category of SQL Commands

### DDL - Data Definition Language
### DQL - Data Query Language
### DML - Data Manipulation Language
### DCL - Data Control Language
### TCL - Transaction Control Language

## Data Types in SQL

- CHAR(n)
  - If CHAR(64) - it allocate entire 64 bit space (which means 64 character), we need to store entire 64 bit space
  - Best for storing GUID (Global Unique Identifier - format is numbers and letter (A-Z))
- VARCHAR(n)
  - If VARCHAR(128) - depend on the data length it will store the from 1 character to 128 character
- TEXT
  - Get as much space as you need to store paragraph or HTML page
  - Not used for Index and Sorting (which means no ORDER BY and WHERE clause used with this data type)
- BINARY (rarely used)
  - Not used for Index and Sorting
  - Store small size image
- SMALLINT
  - This type store -32766 to +32766
- INTEGER
  - This type stores up to 2 Billion numbers
- BIGINT
  - This stores 10^18 length of data
- REAL
  - 32-bit [10^38]
- DOUBLE PRECISION
  - 64-bit [10^308]
- NUMERIC
  - This holds accuracy values
  - Used for to store money
- TIMESTAMP
  - Format is 'YYYY-MM-DD HH:MM:SS'
- DATE
  - Format is 'YYYY-MM-DD'
- TIME
  - Format is 'HH:MM:SS'

Notes: For DateTime type postgres also support NOW() function <br>
Articles: [Data Types in PostgreSQL](https://www.postgresql.org/docs/current/datatype.html)

[Learn SQL Queries >>](./SQL-Queries.md)