[<< SQL Intro](./SQL-Intro.md)

## Table of Content
- [CRUD Operations](#crud-operations)
  - [Create: How to create a database?](#create-how-to-create-a-database)
  - [Create: How to create a table?](#create-how-to-create-a-table)
  - [Insert: How to add a new item in a table?](#insert-how-to-add-a-new-item-in-a-table)

# CRUD Operations

## Create: How to create a database?

Logged in with a <a title="How to login with SQL Server with PSQL?" href="../Basic/Intro.md#how-to-login-with-sql-server-with-psql">superuser account</a> and <a title='How to create a user?' href="../Basic/pg-specific-cmds.md#how-to-create-a-user">create a new user</a> for the owner of this newly creating database and then execute the below cmd

Syntax:

```
=# CREATE DATABASE database_name WITH OWNER 'user_name'
```

Replace the database_name with actual database and name the database with singular noun. And replace the 'user_name' with new user which you are created from superuser.

## Create: How to create a table?

Syntax

```psql
=> CREATE TABLE table_name(
    col_1_name datatype(condition),
    col_2_name datatype(condition),
);
```

Example

```psql
=> CREATE TABLE user(
    name VARCHAR(128),
    email VARCHAR(128),
);
```

## Insert: How to add a new item in a table?

syntax

```
=> INSERT TABLE table_name (col_1, col_2) VALUES (col_1_value, col_2_value);
```