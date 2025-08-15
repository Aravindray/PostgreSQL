# What is Elastic Search

Elastic search is NoSQL database which work best on REST web server, which is similar to google search functionalities and more.

## How to use elastic search in python

- Install elasticsearch library using `pip install elasticsearch`
- Connect to the elastic search server with host, schema, user and password

```py title:"Elastic search setup"
from elasticsearch import Elasticsearch
es = Elasticsearch(
    [host],
    http_auth = '',
    url_prefix = '',
    scheme = '',
    port = '',
    connection_class = '',
)
```

- Then create the index table

```py
# In this example we use username as index name >>> indexname = secret['user']
# Remove any previous index with the same name
# To remove the index
res = es.indices.delete(index=indexname, ignore=[404, 400])
# To create a new index
res = es.indices.create(index=indexname)
```

- Then add the doc which is json object to the index table, which take 3 argument
  - first argument is the index table name
  - second argument is the primary key
    - It's your choice to choose the primary key format, like use serial numbers, uuids or any hashes
  - third argument is the body which is json

```py
res = es.index(index=indexname, id=pkey, body=doc)
```

- We can refresh the index if you want to (but this is a costly)

```py
res = es.indices.refresh(index=indexname)
```

## How to search a keyword in elastic search?

In this example instead of using the elastic search library, we will use the python requests library

Note: At the time May 24, 2025, I don't know how post() and get() working

Check out this official doc - https://www.elastic.co/guide/en/elasticsearch/reference/current/query-dsl-query-string-query.html

- First we send the query with requests.post() method
- Then it return the response

Below query search for the keyword and return the result

```py
body = json.dumps({ "query": {"query_string": {"query": user_keyword }}})
res = requests.post(queryurl, header, body)
```

## How to match all the keyword(s) in elastic search?

In this example instead of using the elastic search library, we will use the python requests library

```py
body = json.dumps( {"query": {"match_all": {}}} )
res = requests.post(queryurl, header, body)
```

## How to get the result by it's primary key?

In this example instead of using the elastic search library, we will use the python requests library

- Since we know get request goes with url (instead of body) the query is


```py
queryurl = url + '/_doc/' + user_keyword + '?pretty'
res = request.get(queryurl)
```

## Assignment

```py title:"Bookload"
from elasticsearch import Elasticsearch
import hidden

secrets = hidden.elastic()

# create connections
es = Elasticsearch(
    [secrets["host"]],
    http_auth=(secrets["user"], secrets["pass"]),
    url_prefix=secrets["prefix"],
    scheme=secrets["scheme"],
    port=secrets["port"],
)
print("connected to server")

indexname = secrets["user"]

# drop an index
res = es.indices.delete(index=indexname, ignore=[400, 404])
print("index deleted")
print(res)

# create an index
res = es.indices.create(index=indexname)
print("index created")
print(res)

# adding a doc
phara = ""
pcount = 0
with open("pg14091.txt", "r", encoding="utf-8") as file:
    for line in file:
        if line != "\n":
            phara += line.strip() + " "
        else:
            if phara != "":
                pcount += 1
                phara = phara.strip()
                res = es.index(index=indexname, id=pcount, body={"content": phara})
                phara = ""
                if pcount % 50 == 0:
                    print(pcount, res["result"])
                    res = es.indices.refresh(index=indexname)
                    print(res)

print("loaded", pcount, " paragraphs")
```

```py title:"tweet assignment"
from elasticsearch import Elasticsearch
import hidden
from datetime import datetime

secrets = hidden.elastic()

# create connections
es = Elasticsearch(
    [secrets["host"]],
    http_auth=(secrets["user"], secrets["pass"]),
    url_prefix=secrets["prefix"],
    scheme=secrets["scheme"],
    port=secrets["port"],
)
print("connected to server")

indexname = secrets["user"]

# drop an index
res = es.indices.delete(index=indexname, ignore=[400, 404])
print("index deleted")
print(res)

# create an index
res = es.indices.create(index=indexname)
print("index created")
print(res)

# adding a doc
tweets = [
    "Python program to count the words than it would be to manually scan the",
    "The even better news is that I already came up with a simple program to",
    "find the most common word in a text file I wrote it tested it and now",
    "I am giving it to you to use so you can save some time",
    "You dont even need to know Python to use this program You will need to",
]

id_count = 1
for tweet in tweets:
    doc = {
        "author": "aravind",
        "type": "tweet",
        "text": tweet,
        "timestamp": datetime.now(),
    }
    res = es.index(index=indexname, id=id_count, body=doc)
    print("Document added")
    print(res["result"])
    id_count += 1

res = es.indices.refresh(index=indexname)
print("Index refreshed")
print(res)
```