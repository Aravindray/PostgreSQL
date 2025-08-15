# PostgreSQL

Learning Doc, Tips & Tricks

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

This is a Terminal prompt `$>`
This is a Postgres super user prompt `=#`
This is a Postgres normal user prompt `=>`

## Helpful articles

1. [Database, Table, and Column Naming Conventions](https://www.baeldung.com/sql/database-table-column-naming-conventions)

## Credits

> I've enrolled the **Postgres for Everybody** course, so don't be surprise if all note have strong influence Charles Lecture. Published at 2019.

> 2nd I've enrolled the course named **Relational Database Design** from University of Maryland. Published at 2022. This course based on this book **Database Design - 2nd Edition**

## File Structure

- ├── 0-Assets /
- ├── 1-Basic /
  - └── [Intro & Login details](./1-Basic/Intro.md)
  - └── [psql commands](./1-Basic/psql-specific-cmds.md)
- ├── 2-Learn-SQL /
  - └── [Functions, data types, constrains and index](./2-Learn-SQL/SQL-Intro.md)
  - └── [How to do it questions](./2-Learn-SQL/SQL-Queries.md)
- ├── 3-Relational-Database-Design /
  - └── [ACID and BASE differences](./3-Relational-Database-Design/ACID_and_BASE.md)
  - └── [DB Design from Maryland lecture](./3-Relational-Database-Design/DB-Design-Maryland.md)
  - └── [Database Design](./3-Relational-Database-Design/Design-Intro-Michigan.md)
  - └── [Lecture Notes about full text search](./3-Relational-Database-Design/PG4E-Full-Text-Search-Lecture-Notes.pdf)
- ├── 4-JSON /
  - └── [Lecture Notes about JSON](./4-JSON/PG4E-JSON-Lecture-Notes.pdf)
  - └── [How to use JSON in Postgres](./4-JSON/Postgres_and_JSON.md)
- ├── 4-Python /
  - └── [Lecture Notes about Python](./4-Python/PG4E-Python-and-PostgreSQL-Lecture-Notes.pdf)
  - └── [How to use Postgres in Python](./4-Python/Postgres_and_Python.md)
- ├── 5-ElasticSearch /
  - └── [How to use elastic search in psql with Python](./5-ElasticSearch/Py_ElasticSearch.md)
- ├── 99-Workout (ignored) /
- ├── 100-Notes /
  - └── [PSQL-Notes.md](./100-Notes/PSQL-Notes.md)
- └── [credentials.md (ignored)](./credentials.md)
