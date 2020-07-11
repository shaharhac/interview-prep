## Sharding

Sharding is a method of splitting and storing a songle logical dataset in multiple databases.
In a nutshell, a database shard is a ***horizontal partition*** of data in a database.

Each individual partition is referred to as a shard or database shard. Each shard is held on a separate database server instance, to spread load.
Some data within a database remains present in all shards, but some appears only in a single shard. Each shard (or server) acts as the single source for this subset of data.


### The Need
By distributing the data among multiple machines, a cluster of database systems can store larger dataset and handle additional requests. Sharding is necessary if a dataset is too large to be stored
in a single database. Moreover, many sharding strategies allow additional machines to be added. Sharding allows a database cluster to scale along with its data and traffic growth.
