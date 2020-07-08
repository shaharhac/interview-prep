Try to answer those questions first, and then continue reading.

<details>
  <summary>Questions</summary>
  
  <details>
  <summary>Question 1</summary>
  
  Describe an SQL database
  <details>
  <summary>Answer</summary>
  
SQL databases (often called RDBMS) are table based databases that have predefined schemas. It uses SQL (structued query language) for defining and manipulating data.
SQL databases features relational joins, transactions and very good data integrity.
Popular SQL databases are: MySQL, MS-SQL, Oracle

  </details>
  </details>
  
  <details>
  <summary>Question 2</summary>
  
  Describe a NoSQL database
  <details>
  <summary>Answer</summary>
  
NoSQL ("non SQL", "not SQL", "not only SQL") databases are non-relational.
NoSQL databases are document based, ket-value pairs, graph datanases or wide-column stores.
NoSQL databases have dynamic schema and unstructerd data.
Popular SQL databases are: MongodB, redis, Cassandra, ChouchDB
  </details>
  </details>
  
  <details>
  <summary>Question 3</summary>
  
  What is normalization?
  <details>
  <summary>Answer</summary>
  
Normalization is a database design technique that reduces data redundancy. 
Normalization rules divides larger tables into smaller tables and links them using relationships.
The purpose of Normalization in SQL is to eliminate redundant (repetitive) data and ensure data is stored logically.
  </details>
  </details>
  
  <details>
  <summary>Question 4</summary>
  
  Why would you want that your NoSQL database will be denormalized?
  <details>
  <summary>Answer</summary>
  
No SQL databases features no JOIN clause. Therefore, if we want to mimic the JOIN clause effect on our normalized database, we'll need to do couple of different queries,
whereas in denormlized database - one query will be enough.
Ideally, a single document will be the sole source of all information about an item.
  </details>
  </details>
  
  <details>
  <summary>Question 5</summary>
  
  What is data integrity?
  <details>
  <summary>Answer</summary>
  
  Data integirty is the maintenance of, and the assurance of the accuracy and consistency of data over its entrie life-cycle.
  It is a critical aspect to the design, implementation and usage of any system which stores, processes or retrieves data.
  </details>
  </details>
  
  <details>
  <summary>Question 6</summary>
  
  How do we achieve data intergrity in SQL database? How do we do it with NoSQL database?
  <details>
  <summary>Answer</summary>
  
Most SQL databases allow you to enfore data integrity rules using foreign key constraints.
for example - your can unsure that every book will have an `author_id` code that matches one entry in the `authors` table.

The schema enforces these rules for the database to follow. It's impossible for developers or users to add, edit or remove records, which could result in invalid data or orphan records.

The same data intergrity options are not available in noSQL databases. You can store what you want regardless of any other documents. Ideally, a single document will be the sole source of all information about an item.
  </details>
  </details>
  
   <details>
  <summary>Question 7</summary>
  
  What are transactions?
  <details>
  <summary>Answer</summary>
  
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
  </details>
  </details>
  
  <details>
  <summary>Question 8</summary>
  
  Explain the difference in performance between SQL and NoSQL databases
  <details>
  <summary>Answer</summary>
  
NoSQL is regularly quoted as being faster than SQL.
Having said that, your project design and data requirements have a huge role.  A well-designed SQL database will almost certainly perform better than a badly designed NoSQL equivalent and vice versa.
  </details>
  </details>
  
  <details>
  <summary>Question 9</summary>
  
  Explain the difference in scaling between SQL and NoSQL databases
  <details>
  <summary>Answer</summary>
  
Most SQL databases are vertically scalable, which means that you can increase the load on single server by increasing components like RAM, SSD or CPU.
In Contrast, NoSQL databases are horizontally scalable, which means that they can increased traffic simply by adding more servers to the database. NOSQL databases have the ability to become larger and much more powerful, making them the preferred choice for large or constantly evolving data sets.

NoSQL databases give up a massive amount of functionality that a SQL database gives us by it's very nature.
Things like automatic enforcment of referential intergrity, transactions, etc. These all things that are very handy to have for some problems, and which require some unique techniques to scale outside of a single server (what happens if we need to lock two tables for an atomic transaction, and they are on different servers?)
  </details>
  </details>
  
  <details>
  <summary>Question 10</summary>
  
  State 3 reasons to choose SQL over NoSQL
  <details>
  <summary>Answer</summary>
  
  Reasons from SQL:
* Structred data
* Strict Schema
* Relational data
* Need for xomplex joins
* Clear patterns for scaling
* Lookups by index are very fast

  </details>
  </details>
  
  <details>
  <summary>Question 11</summary>
  
  State 3 reasons to choose NoSQL over SQL
  <details>
  <summary>Answer</summary>
  
Reasons for NoSQL:
* Semi-structured data
* Dynamic or flexible schema
* Non-relational data
* No need for complex joins
* Very data intensive workload 
  </details>
  </details>
</details>


# SQL or NoSQL

Retional data model - Highly-structured table organization with rigidly-defined data formats and recoed structure.
Document data model - collection of complex documents with arbitrary nested data formats and varying "record" format.

SQL databases (often called RDBMS) are table based databases that have predefined schemas. It uses SQL (structued query language) for defining and manipulating data.
SQL databases features relational joins, transactions and very good data integrity.
Popular SQL databases are: MySQL, MS-SQL, Oracle

NoSQL ("non SQL", "not SQL", "not only SQL") databases are non-relational.
NoSQL databases are document based, ket-value pairs, graph datanases or wide-column stores.
NoSQL databases have dynamic schema and unstructerd data.
Popular SQL databases are: MongodB, redis, Cassandra, ChouchDB

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
documents from the second collection and manually link the two in our program logic. This is one reason denormalization is often essential.

## Data Integrity

Most SQL databases allow you to enfore data integrity rules using foreign key constraints.
for example - your can unsure that every book will have an `author_id` code that matches one entry in the `authors` table.

The schema enforces these rules for the database to follow. It's impossible for developers or users to add, edit or remove records, which could result in invalid data or orphan records.

The same data intergrity options are not available in noSQL databases. You can store what you want regardless of any other documents. Ideally, a single document will be the sole source of all information about an item.

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

Most SQL databases are vertically scalable, which means that you can increase the load on single server by increasing components like RAM, SSD or CPU.
In Contrast, NoSQL databases are horizontally scalable, which means that they can increased traffic simply by adding more servers to the database. NOSQL databases have the ability to become larger and much more powerful, making them the preferred choice for large or constantly evolving data sets.

NoSQL databases give up a massive amount of functionality that a SQL database gives us by it's very nature.
Things like automatic enforcment of referential intergrity, transactions, etc. These all things that are very handy to have for some problems, and which require some unique techniques to scale outside of a single server (what happens if we need to lock two tables for an atomic transaction, and they are on different servers?)

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
