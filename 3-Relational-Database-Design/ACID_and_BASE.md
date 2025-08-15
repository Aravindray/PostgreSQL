# ACID & BASE

For RDBMS (Relational Database Management System) Architectures we learned about Data Normalization (3NF) like
- Do not replicate data - Instead reference data, point at data
- Use Integer for keys & references
- Add a special key column to each table, which you will make reference to

But the problem with ACID like RDB is scaling.

- Master / Read only replica is similar to BASE like features
- Multi Master / 2 master database are linked coordinated together
- Multiple Store type - 2 database one for relation database and another for file system
- Multi Tenant / 'pretend cloud'

**While designing the database for the application ask: ACID or BASE?**

ACID stand for Atomicity, Consistency, Isolation, Durability
BASE - Basically Available Soft State Eventual Consistency

One of my know example of eventual consistency is YouTube video like system, it will raise up and go down for different users.

Database software

| for ACID   | for BASE |
| ---------- | -------- |
| Oracle     | Mongo    |
| PostgreSQL | Casandra |
| MySQL      | BigTable |
| SQLite     |          |
| SQLServer  |          |

Compromises

| ACID                      | BASE                                 |
| ------------------------- | ------------------------------------ |
| SERIAL INTEGER KEY        | GUIDs - Globally Unique IDs          |
| Transactions              | Design for Stale data in application |
| Unique Constraints        | Application Post-Check and resolve   |
| One Perfect sql statement | Retrieve & throw away                |

**Scaling ACID Relational Database?**

1. Vertical Scaling
   - More disk drives or disk array / RAID
   - More Processors
   - More Memory
   - Switching from spinning to solid state drives
     - Modern SSD Drivers have scatter / gather
   - Has been solidly successful over the year

**To SQL or To NoSQL**

ACID - we use primary key serialized
BASE - we don't use PK instead we use GUIDs - Combination of random number and current time

Emergence of BASE solution (i.e. NoSQL) which is 2nd generation cloud application
- Everything is distributed - Fast Network
- No lock
- Lots of fast / small memory CPUs
- Lots of disks
- Indexes follow data shards
- Documents - not rows / columns
- Schema on read - not schema on write

SSD developed scatter / gather on a single driver with 32 + simultaneous read to different area of the drive (SSD is good for random access)

# My Notes

ACID + BASE - There is some table that doesn't need ACID like features (schematics) so we implement BASE (schematics) like table with in the same application. In postgres which also allow BASE table.

# New rules for ACID + BASE Database

Begin BASE like in ACID RDBMS follow this rules:

1. Do not normalize - Replicate (allow duplicate)
2. Don't use SERIAL - Use UUID / GUIDs
3. Columns are for indexing
4. Do not use Foreign keys or don't mark them as such
5. Design your schema / indexes to enable reading a single row on Query (exactly one row)

| BASE  | ACID    |
| ----- | ------- |
| GUID  | id (PK) |
| JSONB | body    |

6. Use software migrations instead of ALTER TABLE
7. Query for records by PRIMARY KEY (but in 4th point ?) or by Indexed column
8. Don't use JOINs
9. Don't use Aggregations

Extra: Learn how to model Data?

## Summary

- NoSQL is doing well
  - More for specialized applications
  - Less conversation about the "end of SQL"
  - Breathless is becoming pragmatic
  - There is a learning curve - production experience
  - SASS from cloud vendors makes it "easier"
- Some applications converting back
  - "Move from MongoDB to PostgreSQL"