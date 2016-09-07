Introduction
How we Build & Run Modern Apps
The Nexus Architecture
MongoDB Flexible Storage Architecture
MongoDB Data Model
MongoDB Query Model
MongoDB Data Management
Consistency & Durability
Availability
Performance & Compression
Security
Database Management
MongoDB Atlas


lage-scale
high availability
robust systems
indexes
dynamic queries

-- Eliot Horowitz

## Structured, Semi-structured, unstructured and polymorplic data

## The Nexus Architecture

- Expressive query language & secondary indexes
- Strong consistency
- Enterprise Management and Integrations
- Flexible Data Model
- Scalability and Performance
- Always-On Global Deplayments

## MongoDB Flexible Storage Architecture

The default WiredTiger storage engine. For many application, WiredTiger's granular concurrency control and native compression will provide the best all round performance and storage efficiency for the broadest range of applications.

## MongoDB Data Model

Data As Documents
BSON

### Dynamic Schema without Compromising Data Governance
### Document Validation
### Schema Design
### MongoDB Query Model
#### Idiomatic Drivers
#### Interacting with the Database
#### Querying and Visualizing Data
Key-value queries: return results based on any field in the document, often the primary key
Range queries: return results based on values defined as inequalities (greater than, less than or equal to, between)
Geospatial queries:
Text Search:
Aggregation Framework:
MapReduce queries:

Data Visualization with BI Tools

### Indexing
optimizing system perofmance and scalibility
performance of some operations
By default, the WiredTiger storage engine compresses indexes in RAM, freeing up more of the working set for documents.

- Unique Indexes: MongoDB reject inserts of new documents or the update of a document with an existing value for the field for which the unique index has been crated. By default all indexes are not set as unique. If a compound index is specified as unique, the combination of values must be unique.

- Compound Indexex: An additional benefit of a compound index is that any leading field within the index can be used, so fewer indexes on single field may be necessary.

- Array Indexes: 

- TTL Indexes: Time to Live.

- Geospatial Indexes: Tow dimensional space, such as projection systems for the earth. Optimize queries for documents that contain points or a polygon that are closest to a given point or line. Circle, rectangle, or polygon.

- Partial Indexes: By specifying a filtering expression during index creating, a user can instruct MongoDB to include only documents that meet the desired conditions.

- Sparse Indexes: Sparse indexes only contain entries dor documents that contain the specified field. Sparse indexes allow for smaller, more efficient indexes when fields are not presen in all documents.

- Tex Search Indexes: 

### Query Optimization

Index intersection provides additional flexibility by enabling MongoDB to use more than one index to optimize an ad-hoc query at run time.

### Cover Queries
Queries that return results containing only indexed field are called covered queries.

## MongoDB Data Management
### Auto-Sharding
Sharding allows MongoDB deployments to address the hardware limitations of a single server, such as bottlenecks in RAM or disk I/O

To distribute data across a cluster according to query patterns or data locality.

#### Range-based Sharding: Documents are partitioned across shards according to the shard key value.

#### Hash-based Sharding: Documents are uniformly distributed according to an MD5 hash of the shard key value. This approah guarantees a uniform distribution of writes across shards, but is less optimal for range-based queries.

#### Location-aware Sharding: Documents are partitioned according to a user-specified configuration that associates shard key ranges with specific shards and hardware.

## Query Router

Sharding is transparent to applications

## Consistency

### Transaction Model & Configurable Write Availability
MongoDB is ACID compliant at the document level. One or more fields may be writtenin a single operation, including updates to multiple sub-documents and elements of an array. The ACID guarantees provided by MongoDB ensures complete isolation as a document is updated; any errors cause the operation to roll back and clients receive a consistent view of the document.

Write Concern. Write Availability. Desired durability goals, such as writing to at least two replicas in one data center and one replica in a second data center. Each query can specify the appropriate write concer, ranging from unacknowledged to acknowledgement that writes have been committed to all replicas.

## Availability
### Replication: MongoDB maintains multiple copies of data called replica sets using native replication.

### Replica Set Oplog
Operations that modify a database on the primary replica set member are replicated to the secondary members using the oplog (operations log).The oplog contains an ordered set of idempotent operations that are replayed on the secondaries. The size of the oplog is configurable and by default is %5 of the available free dis space.

### Elections And Failover
### Election Priority

## Performance & Compression
### In-Memory Performance With On-Disk Capacity

