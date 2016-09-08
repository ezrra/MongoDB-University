Sharded Collection
Primary Shard

### Sharded cluster

* Can I change the shard key after sharding a collection?

No

there is no automatic support on MongoDB.


* Why are my documents not distributed across the shards?

Once the distribution of chunks has reached certain thresholds


* How does mongos detect changes in the sharded cluster configuration?

mongos instances maintains a cache of the config database thath holds the metadata for the sharded cluster.

* How does mongos use connections?

Each mongos instance maintains a pool of connections to the members of the sharded cluster.
Client requests use theses connections one at a time; requests are not multiplexed or pipelined.