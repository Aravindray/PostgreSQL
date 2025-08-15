# Postgres and JSON

JSON - **J**ava**s**cript **O**bject **N**otation is very much about data serialization.

There was a problem when we transferring data structures between programs in different language (or) same language running across network exchanging data, so we use JSON

```bash ln:false
                ˹----- Linear    | Python - List | JS - Array |
Data Structure -|
                ˻----- Key-Value | Python - Dict | Js - Object |
```

Sending data from one language to another language with some standards is called serialization. For example from Python dict to Js Object (My Understanding), Early days we use XML (Extensible Markup Language). AJAX - Asynchronous JavaScript And XML

**Technical Names**

- For sending - Marshal
- To receiving - Unmarshal

## Python and JSON

There was a default library in python which handle all the necessary for json

```py title:"json_example.py"
import json
# Use dump - process of converting / serializing Py dict to Json
json.dump(dict, indent=4)
# Use load - process of serializing json to Py dict
json.load(json)
```

## JSONB OPERATORS

| Operator | Meaning           | Description                 |
| -------- | ----------------- | --------------------------- |
| ->>      | Text Operator     | return jsonb as text        |
| @>       | Contains Operator | looking key-value pair      |
| ->       | JSONB Operator    | return jsonb                |
| ?        | Tag Operator      | To check if key is present? |

## How to do it?

### CREATE: How to create a jsonb table?

```sql title:"query=>"
CREATE TABLE IF NOT EXISTS jtrack (
  id SERIAL,
  body JSONB
);
```

### CREATE: How to populate the database from external json like files?

- Use postgres `\copy` command

```sql title:"query=>"
\copy jtrack(body) from 'library.jstxt' WITH CSV QUOTE E'\01' DELIMITER E'\02';
-- QUOTE, DELIMITER E'\01' - says ignore irrelevant non printable characters
```

### READ: How to select the JSONB value of the given key?

- Use ->> double arrow syntax | which convert the jsonb and the result as text

```sql title:"query=>"
SELECT body->>'name' FROM jtrack LIMIT 5;
-- 'name' is key of the json array, place with key with quotation
-- above query translate as - search for the 'name' key in the body column and return the value as text
```

### How to convert jsonb type to other type(s)?

| JSONB to TEXT                          | JSONB to TEXT | JSONB to INT |
| -------------------------------------- | ------------- | ------------ |
| Use **->>** double arrow text operator | jsonb::text   | jsonb::int   |

:LiBookOpenText: If you want to find the max of the 'count' key's value, use MAX() function, if not it treated as lexical order

### READ: How to retrieve JSONB column and displays the record(s)?

```sql title:"query=>"
-- looking into JSONB for a value
SELECT id, body FROM jtrack WHERE body ->> 'name' = 'Summer';

-- looking into key/value pair
SELECT id, body FROM jtrack WHERE body @> '{"name": "summer"}';
-- @> translate as - does this body contains this jsonb fragment?

-- using ? operator
SELECT COUNT(*) FROM jtrack WHERE body ? 'favorite';
-- it checks whether the key present or not and return the all the true rows
```

### UPDATE: How to update the json in jsonb column?

#### How to add new key-value pair in the jsonb column?

```sql title:"query=>"
UPDATE jtrack SET body = body || '{"favorite": "yes"}' WHERE id = 1;
```

#### How to update jsonb column with jsonb_set() function?

- take more steps at the time of lecture, check the official doc for more info

```sql title:"query=>"
UPDATE jtrack SET body = jsonb_set(body, '{count}', ((body->>'count')::int + 1)::text::jsonb) WHERE id = 1;
```

### INDEX: How to make indexes for jsonb type?

#### How to make B-Tree index?

```sql title:"query=>"
CREATE INDEX jtrack_btree ON jtrack USING BTREE((body->>'name'));
-- create the index for body 'name' key only
-- as you the WHERE clause express must be same as index expression
-- run EXPLAIN ANALYZE
```

#### How to make GIN index?

```sql title:"query=>"
CREATE INDEX jtrack_gin ON jtrack USING GIN(body);
-- create index for all the keys in the body for every row
-- it uses ? operator for checking the tag / key in WHERE clause
-- run EXPLAIN ANALYZE
```

#### How to make GIN_PATH_OPS index?

```sql title:"query=>"
CREATE INDEX jtrack_gin_path_ops ON jtrack USING GIN(body jsonb_path_ops);
-- create key-value pair index
-- it uses @> contains operator in WHERE clause
-- run EXPLAIN ANALYZE
```

## Assignment

```py title:"Assignment 1"
import psycopg2
from psycopg2.extras import Json
import requests

conn = psycopg2.connect(
    host='pg.pg4e.com',
    port=5432,
    user='pg4e_e8bc7beb32',
    password='pg4e_p_9f757c6c42db703',
    database='pg4e_e8bc7beb32',
)
print('connected')

cur = conn.cursor()


for i in range(1, 101):
    url = f'https://pokeapi.co/api/v2/pokemon/{i}'
    response = requests.get(url)
    if response.status_code == 200:
        data = response.json()
        new_data = Json(data)
        sql = "INSERT INTO pokeapi(body) VALUES (%s);"
        cur.execute(sql, (new_data, ))
        conn.commit()
        print(f'Inserted {i} into database from {type(data)} to {type(new_data)}')

cur.close()
conn.close()
print('disconnected')
```

```py title:"Simple / Sample"
import psycopg2
from psycopg2.extras import Json

conn = psycopg2.connect(
    host="localhost", port=5432, user="pg4e", password="secret", database="music"
)
print("connected")

cur = conn.cursor()

data = {"name": "Aravind", "age": 26}
print(type(data))

sql = "INSERT INTO sample_jsonb(info) VALUES (%s);"

new_data = Json(data)
print(type(new_data))
cur.execute(sql, (new_data,))

conn.commit()
cur.close()
conn.close()
print("disconnected")
```