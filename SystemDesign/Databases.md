# SQL or NoSQL - WIP

Retional data model - Highly-structured table organization with rigidly-defined data formats and recoed structure.
Document data model - collection of complex documents with arbitrary nested data formats and varying "record" format.

## SQL Normalization vs NoSQL Denormalization

Normalization is a database design technique that reduces data redundancy. 
Normalization rules divides larger tables into smaller tables and links them using relationships.
The purpose of Normalization in SQL is to eliminate redundant (repetitive) data and ensure data is stored logically.

Let's say for example that we have a database of movies rented out.

![MoviesTable](https://www.guru99.com/images/NormalizationTable1.png)

this is not well organized table, beacuse we have redundant data.

normalized database will look like this:

<br>

![MembersTable](https://www.guru99.com/images/2NFTable1.png)

<br>

![MoviesTable](https://www.guru99.com/images/2NFTable2.png)

<br>

![SalutationTable](https://www.guru99.com/images/2NFTable3.png)

## SQL join vs NoSQL

SQL queries offer a powerful JOIN clause. We can obtain related data in multiple tables using a single SQL statement.

NoSQL has no equivalent of JOIN. If we used normalized collections as described above, we would fetch all the documents from the first collection, retrive all associated
documents from the second collection and manually link the two in our program logic. This is one reason denomalization is often essential.


## Which one to choose?
Reasons from SQL:
* Structred data
* Strict Schema
* Relational data
* Need for xomplex joins
* Clear patterns for scaling
* Lookups by index are very fast

Reasons for NoSQL:
* Semi-structured data
* Dynamic or flexible schema
* Non-relational data
* No need for complex joins
* Very data intensive workload 
