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

## Data Integrity

Most SQL databases allow you to enfore data integrity rules using foreign key constraints.
for example - your can unsure that every book will have an `author_id` code that 

## Transactions

As of today, transactions only exists in SQL databases.
A transaction is the propagation of one or more changes to the database. 
in essence, transactions are everything that happens between two commits (or a roll-back). You can do multiple updates to your db, and they are all saved once at the commit.
If one fails, the rest are being rolled-back and your database keeping his previous state.

Transactions have the following four standard properties, usually referred to by the acronym ACID.

***Atomicity*** − ensures that all operations within the work unit are completed successfully. Otherwise, the transaction is aborted at the point of failure and all the previous operations are rolled back to their former state.

***Consistency*** − ensures that the database properly changes states upon a successfully committed transaction.

***Isolation*** − enables transactions to operate independently of and transparent to each other.

***Durability*** − ensures that the result or effect of a committed transaction persists in case of a system failure.

In a NoSQL database, modification of a single document is atomic. In other word, if you're updating three values within a docuemnt. either all three are updated successfully or it remains unchanged. However, there's no transaction equivalent for updates multiple documents.


## Performance

NoSQL is regularly quoted as being faster than SQL.
Having said that, your project design and data requirements have a huge role.  A well-designed SQL database will almost certainly perform better than a badly designed NoSQL equivalent and vice versa.

## Scaling

## Knowledge & Community

The most popular NoSQL databases have been around just a few years, and they aren't mature like other SQL products.
Developers might find it harder to develop and maintain a NoSQL database, beacuse the knowledge there is much smaller community for those products.

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
