## Table of Content
- [Relational Database Design](#relational-database-design)
  - [Building a Data Model](#building-a-data-model)
  - [Keys](#keys)
    - [Primary Key](#primary-key)
    - [Foreign Key](#foreign-key)
    - [Logical Key](#logical-key)
  - [Data Normalization (3NF)](#data-normalization-3nf)
    - [Integer Reference Pattern](#integer-reference-pattern)

# Relational Database Design

## Building a Data Model

**Basic Rules:**
- Don't put the same string data in twice - use a relationship instead.
- When there is one thing in 'real world' there should only be one copy of that thing in the database.

**Ask yourself:**
- Is the column an object? or an attribute of another object?
- Once we define object, we need to define the relationship between objects.

## Keys

**Three kinds of keys**

### Primary Key

- Generally an auto increment integer field

### Foreign Key

- Generally an auto increment integer field
- A foreign key is when a table has a column containing a key that points to the primary key of another table.
- Mostly used naming convention for FK If album table store primary key of artist table the column name in album table will be 'artist_id'

### Logical Key

- What outside world uses for lookup
- Like a user search for text in html
- It's another way of telling the engine that we are going to use this column a lot, so create a index for this key and column.

**Basic Rules:**
- Never use your Logical key as your primary key
- Logical key can and do change, slowly so don't use it as primary key
- Relationships that are based on matching string (instead of integer) fields are less efficient, so don't use string field as primary key

## Data Normalization (3NF)

- Do not replicate data, Instead reference data and point at data.
- Use integer for keys and for reference.
- Add a special key column to each table, which you will make reference to.

### Integer Reference Pattern

- We use integer column in table to reference rows in another table


+-------+          +----------+
| Album |          |  Track   |
+-------+          +----------+
| id    | ---|     | id       |
+-------+    |     | title    |
             |     | length   |
             |     | rating |
             | --- |album_id  |
                   +----------+
