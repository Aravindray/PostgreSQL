<a href='./Intro.md'><< Learn the Intro</a>

## Table of Content
- [PSQL Commands](#psql-commands)
    - [\\copy - How to copy data from external file and store it in table records in postgres?](#copy---how-to-copy-data-from-external-file-and-store-it-in-table-records-in-postgres)
    - [\\i - How to execute sql statements from external file(s)?](#i---how-to-execute-sql-statements-from-external-files)


# PSQL Commands

| Command           | Description                                                    |
| ----------------- | -------------------------------------------------------------- |
| `\l`              | To display all the databases                                   |
| `\dt`             | To display all the tables based on the logged-in user          |
| `\d+ table_name`  | Which display detailed schema about the table                  |
| `\copy`           | To copy data from external file and store it in database table |
| `\i`              | To read .sql file from the psql server                         |
| `\q`              | To quit (exit from current user session)                       |
| `\c`              | To change from one database to another                         |
| `EXPLAIN`         | To return details about query                                  |
| `EXPLAIN ANALYZE` | To return more details about query with runtime                |

**Notes:** [for more](https://www.postgresql.org/docs/current/app-psql.html)

### \copy - How to copy data from external file and store it in table records in postgres?

```sql
syntax=> \copy table_name (col_1, ...) FROM 'file_name.ext' WITH DELIMITER ',' CSV;
```

```sql
example=> \copy track_raw (title, artist, album, count, rating, len) FROM 'library.csv' WITH DELIMITER ',' CSV;
```

**Flags**
WITH DELIMITER ',' CSV
WITH DELIMITER ',' CSV HEADER - header means skip the first row
WITH DELIMITER E'\007'; - E'\007' is a BEL character -- need more info - insert each row in a one column?

**Note:** The file 'library.csv' must be same directory as the psql terminal running.

### \i - How to execute sql statements from external file(s)?

The psql \i command will read the sql statement from the file and execute the query.

```sql
syntax=> \i filename.ext
```

```sql
example=> \i 03-Technique-load.sql
```

**Note:** The file '03-Technique-load.sql' must be same directory as the psql terminal running.