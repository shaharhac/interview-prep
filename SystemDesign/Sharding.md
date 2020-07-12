### Scaling with Databases

Just like our application servers, we can scale our database servers. We can scale it ***horizontaly*** and ***vertically***.
Again, just like our other servers, horizontal scaling means to add another machines, and vertical scaling means to add another resources to our current machines.

A database can be split vertically - storing different tables and columns in a separate databade, or horizontally - storiung rows of a same table in multople database nodes.

![databse partitioning](https://miro.medium.com/max/700/1*yyHih3GveWruzwYgLxTu3w.png)

### Vertical Partitioning


### Sharding - Horizontal Partitioning

Sharding is a method of splitting and storing a songle logical dataset in multiple databases.
In a nutshell, a database shard is a ***horizontal partition*** of data in a database.

By distributing the data among multiple machines, a cluster of database systems can store larger dataset and handle additional requests. Sharding is necessary if a dataset is too large to be stored in a single database. Moreover, many sharding strategies allow additional machines to be added. Sharding allows a database cluster to scale along with its data and traffic growth.

Each individual partition is referred to as a shard or database shard. Each shard is held on a separate database server instance, to spread load.
Some data within a database remains present in all shards, but some appears only in a single shard. Each shard (or server) acts as the single source for this subset of data.

Almost all modern databases are natibely sharded. Cassandra, HBase and MongoDB are popular disributed databases.
Notable examples of non-sharded modren databases are Sqlite, redis, memcached and Zookeeper.

### Distribution Strategies  

There exist various strategies to distribute data into multiple databases.
Each strategy has pros and cons depending on various assumptions a strategy makes.
Operations may need to seatch through many databases to find the requested data. These are called ***cross-partition operations*** and they then to be ineffcient.
***Hotspots*** are another common problem - having uneven distribution of data and operations.
