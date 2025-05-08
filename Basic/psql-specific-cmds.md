<a href='./Intro.md'><< Learn the Intro</a>

## Table of Content
- [PSQL Commands](#psql-commands)
    - [\\copy - How to copy data from external file and store it in table records in postgres?](#copy---how-to-copy-data-from-external-file-and-store-it-in-table-records-in-postgres)
    - [\\copy - How to execute sql statements from external file(s)?](#copy---how-to-execute-sql-statements-from-external-files)


# PSQL Commands

| Command          | Description                                                    |
| ---------------- | -------------------------------------------------------------- |
| `\l`             | To display all the databases                                   |
| `\dt`            | To display all the tables based on the logged-in user          |
| `\d+ table_name` | Which display detailed schema about the table                  |
| `\copy`          | To copy data from external file and store it in database table |
| `\i`             | To read .sql file from the psql server                         |
| `\q`             | To quit (exit from current user session)                       |


### \copy - How to copy data from external file and store it in table records in postgres?

Syntax
```
=> \copy table_name (col_1, ...) FROM 'file_name.ext' WITH DELIMITER ',' CSV;
```

Example
```
=> \copy track_raw (title, artist, album, count, rating, len) FROM 'library.csv' WITH DELIMITER ',' CSV;
```

**Note:** The file 'library.csv' must be same directory as the psql terminal running.

### \copy - How to execute sql statements from external file(s)?

The psql \i command will read the sql statement from the file and execute the query.

Syntax
```
=> \i filename.ext
```

Example
```
=> \i 03-Technique-load.sql
```

**Note:** The file '03-Technique-load.sql' must be same directory as the psql terminal running.