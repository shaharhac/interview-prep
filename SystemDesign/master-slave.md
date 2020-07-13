
## Master and Slave Databases

A database is "slaved" to a "master" when it receives a stream of updates from the master in near real-time, functioning as a copy of it.
The "slave" must simply apply the changes that the master validated and approved.


## Usage

### Scalability

Spreading the load among multiple slaves to improve performance.
All writes updates must take place on the master server (which later on will be passed to the slaves). Reads, however , may take place on one ot more slaves.
This model can improve the performance of writes (subce tge naster is dedicated to updates), while dramatically increasing read speed across an increasing number of slaves.

### Data Security

As data is replicated to the slave, and the slave can pause the replication process, it is possible to run backup services on the slave without corrupting the correspoinding master data.

### Analytics

live data can be created on the master, while the analysis of the imformation can take place on the slave without affecting the performance of the master

### Long Distance Data Distribution

If a branch office would like to work with a copy of our main datam we can use replication to create a local copu of the data for their use without requiring permanent access to the master.

## Disadvantages

* It's not very reliable because of asynchronous replication. It means that some committed data on master transactions may be not available on slave if the master fails
* Write requests can hardly be scaled. The only option to scale write requests is to increase computer capacity (RAM and CPU) of the master node
