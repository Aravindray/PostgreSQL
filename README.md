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
