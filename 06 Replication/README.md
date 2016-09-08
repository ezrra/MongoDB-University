### Replica Set Data Synchronization
sync or replicate data from other members

Two forms: initial sync to populate new members with the full data set
and replication to apply ongoin changes to the entire data set.



### Replicaton
Secondary members replicate data continuously after the initial sync. Secondary members copy the oplog from their sync from source and apply theses operations in an synchronous process.

I most cases, secondaries sync from the primary. Secondaries may automatically change their sync from source if needed based on changes in the ping time and state of other members' replication.

Secondaries avoid syncing from delayed members and hidden members.

### Multithreaded Replication
MongoDB applies write operations in batches using multiple threads to improve concurrency.