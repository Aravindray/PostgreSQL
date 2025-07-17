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

## File Structure

- ├── 0-Assets /
- ├── 1-Basic /
  - └── <a href="https://github.com/Aravindray/PostgreSQL/blob/main/1-Basic/Intro.md" title="Intro & Login details">Intro.md</a>
  - └── <a href="https://github.com/Aravindray/PostgreSQL/blob/main/1-Basic/psql-specific-cmds.md" title="psql commands">psql-specific-cmds.md</a>
- ├── 2-Learn-SQL /
  - └── <a href="https://github.com/Aravindray/PostgreSQL/blob/main/2-Learn-SQL/SQL-Intro.md" title="Functions, data types, constrains and index">SQL-Intro.md</a>
  - └── <a href="https://github.com/Aravindray/PostgreSQL/blob/main/2-Learn-SQL/SQL-Queries.md" title="How to do it questions">SQL-Queries.md</a>
- ├── 3-Relational-Database-Design /
  - └── <a href="https://github.com/Aravindray/PostgreSQL/blob/main/3-Relational-Database-Design/ACID_and_BASE.md" title="ACID and BASE differences">ACID_and_BASE.md</a>
  - └── <a href="https://github.com/Aravindray/PostgreSQL/blob/main/3-Relational-Database-Design/DB-Design-Maryland.md" title="DB Design from Maryland lecture">DB-Design-Maryland.md</a>
  - └── <a href="https://github.com/Aravindray/PostgreSQL/blob/main/3-Relational-Database-Design/Design-Intro-Michigan.md" title="Database Design">Design-Intro-Michigan.md</a>
  - └── <a href="https://github.com/Aravindray/PostgreSQL/blob/main/3-Relational-Database-Design/PG4E-Full-Text-Search-Lecture-Notes.pdf" title="Lecture Notes about full text search">PG4E-Full-Text-Search-Lecture-Notes.pdf</a>
- ├── 4-JSON /
  - └── <a href="https://github.com/Aravindray/PostgreSQL/blob/main/4-JSON/PG4E-JSON-Lecture-Notes.pdf" title="Lecture Notes about JSON">PG4E-JSON-Lecture-Notes.pdf</a>
  - └── <a href="https://github.com/Aravindray/PostgreSQL/blob/main/4-JSON/Postgres_and_JSON.md" title="How to use JSON in Postgres">Postgres_and_JSON.md</a>
- ├── 4-Python /
  - └── <a href="https://github.com/Aravindray/PostgreSQL/blob/main/4-Python/PG4E-Python-and-PostgreSQL-Lecture-Notes.pdf" title="Lecture Notes about Python">PG4E-Python-and-PostgreSQL-Lecture-Notes.pdf</a>
  - └── <a href="https://github.com/Aravindray/PostgreSQL/blob/main/4-Python/Postgres_and_Python.md" title="How to use Postgres in Python">Postgres_and_Python.md</a>
- ├── 5-ElasticSearch /
  - └── <a href="https://github.com/Aravindray/PostgreSQL/blob/main/5-ElasticSearch/Py_ElasticSearch.md" title="How to use elastic search in psql with Python">Py_ElasticSearch.md</a>
- ├── 99-Workout (ignored) /
- ├── 100-Notes /
  - └── [PSQL-Notes.md](https://github.com/Aravindray/PostgreSQL/blob/main/100-Notes/PSQL-Notes.md)
- └── [credentials.md (ignored)](./credentials.md)


## Table of Content
- [PostgreSQL](#postgresql)
  - [Naming Conventions](#naming-conventions)
  - [Terminology](#terminology)
  - [Notations](#notations)
  - [Helpful articles](#helpful-articles)
  - [Credits](#credits)
  - [File Structure](#file-structure)
  - [Table of Content](#table-of-content)

<style>
    ul {
      list-style-type: none;
    }
</style>