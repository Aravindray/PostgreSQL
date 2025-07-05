# PostgreSQL
PostgreSQL - Learning Doc, Tips &amp; Tricks

## Naming Conventions

Select a naming convention method from snake_case, camelCase or PascalCase

- Database - Name it **singular** noun. Django model also uses the singular class name.
- Table - Name it **singular** noun. user **teacher** instead of teachers.
- Column - Name it **singular** noun. If you have table name order avoid naming the column order_id, order_date just name it **id**, **date**.

## Terminology

1. Database - one or more tables
2. Relation (Table) - contain Tuples and Attributes
3. Tuples (Row) - a set of fields which define an object like a person, or a music track / a single row
4. Attributes (Column or Field) - one of possibly many elements of data corresponding to the object represented by the row

## Notations

This is a Terminal prompt `$>` <br>
This is a Postgres super user prompt `=#` <br>
This is a Postgres normal user prompt `=>`

## Helpful articles

1. [Database, Table, and Column Naming Conventions](https://www.baeldung.com/sql/database-table-column-naming-conventions)

## Credits

> I've enrolled the **Postgres for Everybody** course, so don't be surprise if all note have strong influence Charles Lecture. Published at 2019.

> 2nd I've enrolled the course named **Relational Database Design** from University of Maryland. Published at 2022. This course based on this book **Database Design - 2nd Edition**

## Indexes

| File Name                                                                                                                            | Description                                 |
| ------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------- |
| [Intro.md](./Basic/Intro.md)                                                                                                         | Intro & Login details                       |
| [psql-specific-cmds.md](./Basic/psql-specific-cmds.md)                                                                               | psql commands                               |
| [SQL-Intro.md](./Learn-SQL/SQL-Intro.md)                                                                                             | Functions, data types, constrains and index |
| [SQL-Queries.md](./Learn-SQL/SQL-Queries.md)                                                                                         | How to do it questions                      |
| [Py_ElasticSearch.md](./Pg_ElasticSearch/Py_ElasticSearch.md)                                                                        | How to use elastic search in psql           |
| [PG4E - JSON - Lecture Notes.pdf](./Pg_Json/PG4E%20-%20JSON%20-%20Lecture%20Notes.pdf)                                               | Lecture Notes about json                    |
| [Postgres_and_JSON.md](./Pg_Json/Postgres_and_JSON.md)                                                                               | How to use json in postgres                 |
| [PG4E - Python and PostgreSQL - Lecture Notes.pdf](./Pg_Py/PG4E%20-%20Python%20and%20PostgreSQL%20-%20Lecture%20Notes.pdf)           | Lecture Notes about python                  |
| [Postgres_and_Python.md](./Pg_Py/Postgres_and_Python.md)                                                                             | How to use postgres in python               |
| [ACID_and_BASE.md](./Relational-Database-Design/ACID_and_BASE.md)                                                                    | ACID and BASE differences                   |
| [DB-Design-Maryland.md](./Relational-Database-Design/DB-Design-Maryland.md)                                                          | DB Design from Maryland lecture             |
| [Design-Intro-Michigan.md](./Relational-Database-Design/Design-Intro-Michigan.md)                                                    | Database Design                             |
| [PG4E - Full Text Search - Lecture Note.pdf](./Relational-Database-Design/PG4E%20-%20Full%20Text%20Search%20-%20Lecture%20Notes.pdf) | Lecture Notes about full text search        |