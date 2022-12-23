## Caching

Caching will enable you to make vasly better use of the resources you already have as well as making otherwise unattainable product requirements feasible.
Caches take advantage of the locality of reference principle: ***recently requested data is likely to be requested agian***.

They are used in almost every layer of computing: hardware, os, web browsers, web applications and more.
A cache is like short-term memory: it has limited amount of space, but it typically faster than the original data source and contains the most recently accessed items.
Caches can exist at all level in architecture, but are often found at the level nearest to the front end where they are implemnted to return data quickly without taxing downstream levels.

Caching use cases: 
* Precalculating results (the number of visits from each referring domain for the previous day)
* pre-generating expensive indexes (suggested stories based on a user's click history)
* storing copies of frequently accessed data in a faster backend

### Application Server Cache

Placing a cache firectly on a request layer node enavles the local storage of response data. Each time a request is made to the service, the node will quickly return local cached data if it exists. If it is not in the cache, the requesting node will query the data from disk.

What happens when you expand this to many nodes? if the request layer is expanded to multiple nodes, it's still quite possible to have each node host its own cache.
However, if your load balancer randomly distributed request across the nodes, the same request will go to different nodes, thus increasing cache misses.
Two choices for overcoming this hurdle are global caches and distributed caches.

Global Cache - 

Distibuted Cache -

### Cache invalidation

Cache requires some maintenance for keeping it coherent with the source of truth (database). If the data is modified in the database it should be invalidated in the cache.
If not, this can couse inconsistent application behavior.

There are three main schemas to solve the invalid cache problem:

1. ***Write-through cache*** - Under this scheme, data is written into the cache and the corresponsing database at the same time, The cache data allows for fast retrieval and,
since the same data gets written in the permanent storagem we will have complete data consistency between the cache and the storage, Aksi this scheme ensures tha tnothing will get lost in case of a crash, power failure and so on.
On the other side, since every write operation must be done twice before returning success to the client, this scheme has the disadvantage of higher latency for write operations.

2. ***Write-around cache*** - This technique is similar to write trhough cache, but data is written directly to permanent storage, bypassing the cache. This can reduce the cache being flooded with write operations that will not subsequently be re-read, but has the disadvantage that a read request for recently written data will create a "cache miss"
and must be read from slower back-end storage and experience higher latency.

3. ***Write-back cache*** - Under this scheme, data is written to cache alone and completion is immediately confirmed to the client. The write to the permanent storage is done after specified intervals or under certain conditions. This results in low latency and high throughput fir write-intensive applications. however, this speed comes with the risk of data loss in case of a crash or other adverse event because the only copy of the written data is in the cache.

## Cache eviction

most common cache eviction policies:

1. First In First Out (FIFO)
2. Last In First Out (LIFO)
3. Least Recently Used (LRU)
4. Most Recently Used (MRU)
5. Least Frequently Used (LFU)
6. Random Replacment (RR)
