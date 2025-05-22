## Table of Content
- [Relational Database Design from Maryland](#relational-database-design-from-maryland)
  - [What you need to know](#what-you-need-to-know)
  - [Physical and Logical Models](#physical-and-logical-models)
  - [Schema Diagram](#schema-diagram)
    - [Schema Diagram with Foreign Keys](#schema-diagram-with-foreign-keys)

# Relational Database Design from Maryland

##  What you need to know

Before you can design a Relational Database, you need to understand a little more about its primary components.  You can use this page as a reference for all of the terms used in this course.

**Table or Relation:**  A Table in Relational Database is simpler to a table in Word or another word processor.  It is a simple list of data.  It has a name.  It can have multiple Columns, which in Relational Databases can also be called Fields or Attributes.  For example, you could have a table called Customer.

**Column, Field or Attribute:**  A Column makes up tables.  It has a name and a Datatype.  For example, a table called Customer might have columns named Name, Phone, and Balance.

**Datatype:**  Each Column has a datatype describing what data types can be stored in the column.  This could include letters, integers, and decimals.  In many cases, datatypes also describe the size of the data that can be stored.

**Row or Record:**  This is a single collection of data for a table.  It has values for each of the columns.  For example, a table called Customer might have a record with Name = “Bill Smith”, Phone = “123-456-7890” and a Balance = 150.55.  A table can have multiple rows.  Some databases have millions of rows.

**Primary Key:**  A primary key is one or more columns in a table that cannot have the same values repeated within rows.  It is often used to reference a specific row.  When you shop in stores you often see a product number on a product.  This is a primary key.  Their system might very well have a table in a database called Product.  There could be a column called ProductNo that is a primary key.  An example of a primary key with more than one field could be a table of classrooms on a college campus.  A table could be called Classroom, with columns Building and RoomNo.  Multiple classrooms have the same Building name, and multiple classrooms have the same room number.  But each Building and RoomNo together identify a unique classroom.

**Index:**  An index can be defined on one or more fields on a table to make retrieving data on that column(s) faster.  Have you ever contacted a company, and they tell you what data they can use to bring up your account?  They might say, “I can look up your account on the account # and phone number?”  That probably means that their system has an index on the account # and another index on the phone number.

**Foreign Key:**  A Foreign Key is when a Primary Key of one table is a column in another table.  This defines a relationship between the two tables.  For example, let us assume that I have a table Customer that has a primary key of CustomerNo.  It stored information about my customers.  But I have another table called Sales that has a primary key of SalesNo.  But who do I know which sales were made by which customers?  In the Sales table, I will put a column called CustomerNo.  If customer number 1 is “Bill Smith” and sales number 55 is an iPhone, but the customer number in the Sales table is 1, then I know that Bill Smith purchased that iPhone.  Foreign Keys are how we link different types of data across a database.

There are a few other components in relational databases, but this list is probably enough to understand how to create database designs.

## Physical and Logical Models

All database diagrams can be classified as Logical or Physical diagrams.  Logical diagrams attempt to explain the system (in this case, the database) in concepts and non-technically.  Physical diagrams show a design that matches how it will be implemented, in this case, a Relational Database.

They are intended for different audiences. Logical diagrams are:
- normally for less technical people
- produced earlier in the process

While physical diagrams are:
- very technical in nature
- produced once the conceptual view is decided upon

Let's look at an example.  Assume that we are building an accounting system.  During the design process, we want to review the database model with one of the users, an Accountant.  This is often done to make sure everything is correct before building.  One part of our model might say, AccountName Varchar (20).  You show this to the Accountant, and he is confused.  Why is there no space between "Account" and "Name"?  What is Varchar(20)?  People that build databases know that a table name cannot have a space in it and that Varchar(20) is a string field that can hold up to 20 characters.  But the Accountant knows none of this.  This can cause so much confusion that the entire review session with the Accountant can be sidetracked.

But what is the model said, Account Name String up to 20 characters.   This is a logical design.  This can reduce confusion.  Then, after reviews are completed, a physical diagram can be created from the logical diagram.

## Schema Diagram

A Schema Diagram is a basic diagram showing the tables and columns.  A Schema Diagram is a list of the tables in a database.  For each table, there is a horizontal bar with the attribute names.  No data types are provided, but we normally use the exact syntax for the attribute name (i.e., not spaces in the names). We often underline the attributes that make up the primary key.

Here is an example

Customers

| customer_id |	customer_name |

Orders

| order_id | customer_id | order_date |

Shipments

| shipment_id |	order_id | shipment_date |

This diagram shows that there will be a table called Customers.  It will have 2 attributes.  Customer_id is the primary key.  Customer_name is the second attribute.  Then there is a table for Orders.  It has 3 attributes:  Order_id (the primary key), customer_id and order_date.  The final table is Shipments.  It has 3 attributes:  shipment_id (the primary key), order_id and shipment_date.

### Schema Diagram with Foreign Keys

Referential integrity constraints are rules that the database enforces so that data does not get messed up.

We can add our referential integrity constraints to the diagram by showing where the foreign keys will be.  This is shown by arrow points from the attribute that has the foreign key to the attribute of where possible values can come from.