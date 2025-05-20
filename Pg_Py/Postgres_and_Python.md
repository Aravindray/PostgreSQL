## Table of Content
- [Postgres \& Python](#postgres--python)
  - [How it is working?](#how-it-is-working)
      - [Install \& Import Package](#install--import-package)
      - [Make a Connection](#make-a-connection)
      - [Run the Query](#run-the-query)
      - [Make a Commit](#make-a-commit)
      - [Close the Connection](#close-the-connection)

# Postgres & Python

**Background** - psql is a piece of software which connect to database server and execute commands. Similarly Python is another piece of software which connect to the postgres server with the help of this package called psycopg2, Python is best for string and data science and analytics.

## How it is working?

#### Install & Import Package

- First we need to install the psycopg2 connector with `pip install psycopg2` command, and import it in the module

#### Make a Connection

- Then we need to connect to the server, run this command
- For security reason we can create a dictionary of confidential data and import it and make a connection with it.

```py
>>> import psycopg2
>>> from hidden import secret
>>> conn = psycopg2.connect(
    host = secret['host'],
    database = secret['database'],
    user = secret['user'],
    password = secret['password'],
    connect_timeout = 3
)
```

#### Run the Query

- Once server are connected, we can run / execute sql statement with cursor, **don't forget** to add **;** semicolon at the end of each statement

```py
>>> cur = conn.cursor()
>>> sql = 'SELECT * FROM table_name;'
>>> cur.execute(sql)
```

#### Make a Commit

- While inserting or updating the database sometime connection timeout or exceptions pop-up so to avoid it we make commit to the connection once a while to save the instance in the database.
- Flushes all to the database server

```py
>>> conn.commit()
```

#### Close the Connection

- Once ever thing finished don't forgot to close the cursor and connection

```py
>>> cur.close()
>>> conn.close()
```