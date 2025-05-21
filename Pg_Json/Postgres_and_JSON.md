## Table of Content
- [Postgres and JSON](#postgres-and-json)
  - [Python and JSON](#python-and-json)
  - [JSONB OPERATORS](#jsonb-operators)

# Postgres and JSON

JSON - **J**ava**s**cript **O**bject **N**otation is very much about data serialization.

There was a problem when we transferring data structures between programs in different language (or) same language running across network exchanging data, so we use JSON

```
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

```py
>>> import json
# Use dump - process of converting / serializing Py dict to Json
>>> json.dump(dict, indent=4)
# Use load - process of serializing json to Py dict
>>> json.load(json)
```

## JSONB OPERATORS

| Operator | Meaning           |
| -------- | ----------------- |
| ->>      |                   |
| @>       | Contains Operator |