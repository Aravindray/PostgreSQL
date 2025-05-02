## Table of Content
- [What is PostgreSQL?](#what-is-postgresql)
- [What is Relational Database and How it's working?](#what-is-relational-database-and-how-its-working)
  - [Types of Database](#types-of-database)
- [What is user and their role in a database?](#what-is-user-and-their-role-in-a-database)
- [How to Login?](#how-to-login)
  - [How to login with SQL Server as a admin with PSQL?](#how-to-login-with-sql-server-as-a-admin-with-psql)
  - [How to login with SQL Server as a user with PSQL?](#how-to-login-with-sql-server-as-a-user-with-psql)
- [How to create a user?](#how-to-create-a-user)

# What is PostgreSQL?

Postgres is both powerful and open source Relation Database Management System (RDBMS).

# What is Relational Database and How it's working?

A relational database is a collection of tables, and tables are linked with one other with relationship.

A table is the collection of <abbr title='A data is about a physical or abstract things, for example a person, or music track etc.,'>data</abbr> and arranged in the manner of <abbr title='a sets of attribute about a particular/single person'>rows</abbr> and <abbr title='Also know as field or attribute, which define the type of data and conditions'>columns</abbr>, like a excel spreadsheet.

Postgres work like a client-server relationship like a web browser and server computer connect with internet (through request-response cycle). Postgres server is like where our data stored in physical driver and Postgres client will connect with server with username and password (like login with gmail account) and user execute the SQL commends or statements to get the result from sever.

## Types of Database

There are many types of database: Document Database, NewSQL Database, Key-Value Database, Columnar Database, Graph Database, Time-series Database, Object-oriented Database, Hierarchical Databases, Network Databases, Cloud Database, Centralized Database, Operational Database, but these are the common one (source: AI Generated)


**Relational Databases** are the most widely used type of database. They store data in tables, which consist of rows and columns. Each table has a unique key that identifies its rows. SQL (Structured Query Language) is used to manage and query data in relational databases. Examples include MySQL, PostgreSQL, and Oracle.

**NoSQL Databases** are designed to handle unstructured or semi-structured data. They do not use tables like relational databases. Instead, they use various data models such as document, key-value, column-family, and graph. NoSQL databases are highly scalable and can handle large volumes of data. Examples include MongoDB, Cassandra, and Redis.

# What is user and their role in a database?

Like every app, Postgres have <abbr title='default is postgres'>superuser</abbr> (admin)  who have all the access, like manipulating both data and database and creating a new user with limited permissions and so on.

# How to Login?

**What is PSQL?** : PSQL is a command line tool where we execute SQL commands / statements.

## How to login with SQL Server as a admin with PSQL?

Okay, how to login with gmail account what are the things you need?, like you need URL, username and password.

Similarly to login with Postgres client we need Host, Port, Database, User and Password

`$> psql -U postgres` <br>
`-U` stand for user.

from the above command login with default superuser, enter the password now, then the prompt will change from `$>` to `postgres=#` where **#** indicate that you are logged in as superuser.

## How to login with SQL Server as a user with PSQL?

`$> psql database_name user_name` <br>
or `$> psql -U user_name` <br>
from the above command replace the database_name and  user_name with actual one and then enter the password to login.

# How to create a user?

To create a new user, we must need to log in with superuser account, once logged in execute this command in the terminal

Syntax: `=> CREATE USER user_name WITH PASSWORD 'password';`

replace user_name and actual_password with real username and password.

<a href='./psql-specific-cmds.md'>Learn Postgres specific commands >></a>