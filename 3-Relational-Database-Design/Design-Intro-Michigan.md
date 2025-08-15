# Relational Database Design from Michigan Charles

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

**Integer Reference Pattern** - We use integer column in table to reference rows in another table

```
+-------+          +----------+
| Album |          |  Track   |
+-------+  1       +----------+
| id    | ---|     | id       |
+-------+    |     | title    |
             |     | length   |
             | M   | rating ‎ ‎ |
             | --- |‎ album_id |
                   +----------+
```

Above table is the example of Many-to-One relationship, Think like many songs belong to one album

**Notes:** Above table generated in this [website](https://ozh.github.io/ascii-tables/)

## SQL Query to build ONE-to-Many relationship

Let consider this scenario where we want to store track (song) details, like song name (title), artist, album. Instead of storing all artist and album value repeating itself, we store each detail in separate table and link with them as foreign key in track table.

```sql title:"query=>"
-- artist table
CREATE TABLE artist(
  id SERIAL,
  name VARCHAR(128),
  PRIMARY KEY(id)
);

-- album table
CREATE TABLE album(
  id SERIAL,
  title VARCHAR(200) UNIQUE,
  artist_id INTEGER REFERENCES artist(id) ON DELETE CASCADE,
  PRIMARY KEY(id)
);
```

From above example we see that the album table storing the id of artist table with REFERENCES keyword, this is called as foreign key relation.

## Power of Relational Database

- By removing the replicated data and replacing it with references to a single copy of each bit of data, we build a "web" of information that the relational database can read through very quickly - even for very large amounts of data.
- Often when you want some data it comes from a number of tables linked by these foreign keys.

## SQL Query to build Many-to-Many relationship

- Best example of many to many relations is books and authors table, A author can write many books and A book was written by many authors.
- Many-to-Many is a technical name, there is no direct connection between 2 tables, instead we create the intermediate table, (through table, junction table, join table) and link the primary key of 2 tables.

```sql title:"query=>"
-- book table
CREATE TABLE book (
  id SERIAL,
  title VARCHAR(128),
  PRIMARY KEY(id)
)

-- author table
CREATE TABLE author (
  id SERIAL,
  name VARCHAR(128),
  PRIMARY KEY(id)
)

-- intermediate table
CREATE TABLE author_book (
  book_id INTEGER REFERENCES book(id) ON DELETE CASCADE,
  author_id INTEGER REFERENCES author(id) ON DELETE CASCADE,
)
```

[[PG4E-Full-Text-Search-Lecture-Notes.pdf|Full Text Search Lecture Notes >>]]