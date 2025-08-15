# Postgres & Python

**Background** - psql is a piece of software which connect to database server and execute commands. Similarly Python is another piece of software which connect to the postgres server with the help of this package called psycopg2, Python is best for string and data science and analytics.

## How it is working?

#### Install & Import Package

- First we need to install the psycopg2 connector with `pip install psycopg2` command, and import it in the module

#### Make a Connection

- Then we need to connect to the server, run this command
- For security reason we can create a dictionary of confidential data and import it and make a connection with it.

```py title:"How to connect py to postgres"
import psycopg2
from hidden import secret
conn = psycopg2.connect(
    host = secret['host'],
    port = 5432,
    database = secret['database'],
    user = secret['user'],
    password = secret['password'],
    connect_timeout = 3
)
```

#### Run the Query

- Once server are connected, we can run / execute sql statement with cursor, **don't forget** to add **;** semicolon at the end of each statement

```py title:"create cursor"
cur = conn.cursor()
sql = 'SELECT * FROM table_name;'
cur.execute(sql)
```

#### Make a Commit

- While inserting or updating the database sometime connection timeout or exceptions pop-up so to avoid it we make commit to the connection once a while to save the instance in the database.
- Flushes all to the database server

```py title:"save it to postgres"
conn.commit()
```

#### Close the Connection

- Once ever thing finished don't forgot to close the cursor and connection

```py title:"close the cursor & connection"
cur.close()
conn.close()
```

## How to do it?

### How to make a connection using psycopg2 to local server?

- These are the parameters needed host, port, user, password, database

```py title:"connect local server"
import psycopg2
conn = psycopg2.connect(
    host = 'localhost',
    port = 5432,
    user = 'pg4e',
    password = 'secret',
    database = 'music'
)
```

### How to replace the query with variable?

- Use `(%s)` for substitution parameter in query, which take tuple as a input

```py title:"working with variables"
for i in range(10):
        txt = 'Have a nice day' + str(i)
        sql = 'INSERT INTO pythonfun(line) VALUES (%s);'
        cur.execute(sql, (txt, ))
conn.commit()
# It is wired in python this is how to create one element tuple - ('Aravind', )
```

### How to select and display record(s) from the table?

- Use `fetchone() | fetchall() | fetchmany()`, we can select the records from database, the select statement return the record set (tuple), else it return `None`

```py title:"display record(s)"
cur.execute('SELECT * FROM table_name LIMIT 10')
print(cur.fetchall())
# print(cur.fetchone())
# print(cur.fetchmany(size=3))
```

### How to handle insert with return statement?

- Just run the insert statement and fetch the return value

```py title:"insert and get result"
cur.execute('INSERT INTO pythonfun(line) VALUES ("Hello World") RETURNING id;')
id = cur.fetchone()[0]
print('New id', id)
```