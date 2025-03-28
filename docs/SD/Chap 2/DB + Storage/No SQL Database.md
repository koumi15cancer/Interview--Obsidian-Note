NoSQL is a broad category that includes any database that doesn't use SQL as its primary data access language. These types of databases are also sometimes referred to as non-relational databases. Unlike in relational databases, data in a NoSQL database doesn't have to conform to a pre-defined schema. NoSQL databases follow [BASE consistency model](https://karanpratapsingh.com/courses/system-design/acid-and-base-consistency-models#base).

Below are different types of NoSQL databases:

### [](https://kps.hashnode.dev/system-design-the-complete-course?ref=dailydev#heading-document "Permalink")Document

A document database (also known as a document-oriented database or a document store) is a database that stores information in documents. They are general-purpose databases that serve a variety of use cases for both transactional and analytical applications.

**Advantages**

- Intuitive and flexible
- Easy horizontal scaling
- Schemaless

**Disadvantages**

- Schemaless
- Non-relational

**Examples**

- [MongoDB](https://www.mongodb.com/)
- [Amazon DocumentDB](https://aws.amazon.com/documentdb)
- [CouchDB](https://couchdb.apache.org/)

### [](https://kps.hashnode.dev/system-design-the-complete-course?ref=dailydev#heading-key-value "Permalink")Key-value

One of the simplest types of NoSQL databases, key-value databases save data as a group of key-value pairs made up of two data items each. They're also sometimes referred to as a key-value store.

**Advantages**

- Simple and performant
- Highly scalable for high volumes of traffic
- Session management
- Optimized lookups

**Disadvantages**

- Basic CRUD
- Values can't be filtered
- Lacks indexing and scanning capabilities
- Not optimized for complex queries

**Examples**

- [Redis](https://redis.io/)
- [Memcached](https://memcached.org/)
- [Amazon DynamoDB](https://aws.amazon.com/dynamodb)
- [Aerospike](https://aerospike.com/)

### [](https://kps.hashnode.dev/system-design-the-complete-course?ref=dailydev#heading-graph "Permalink")Graph

A graph database is a NoSQL database that uses graph structures for semantic queries with nodes, edges, and properties to represent and store data instead of tables or documents.

The graph relates the data items in the store to a collection of nodes and edges, the edges representing the relationships between the nodes. The relationships allow data in the store to be linked together directly and, in many cases, retrieved with one operation.

**Advantages**

- Query speed
- Agile and flexible
- Explicit data representation

**Disadvantages**

- Complex
- No standardized query language

**Use cases**

- Fraud detection
- Recommendation engines
- Social networks
- Network mapping

**Examples**

- [Neo4j](https://neo4j.com/)
- [ArangoDB](https://www.arangodb.com/)
- [Amazon Neptune](https://aws.amazon.com/neptune)
- [JanusGraph](https://janusgraph.org/)

### [](https://kps.hashnode.dev/system-design-the-complete-course?ref=dailydev#heading-time-series "Permalink")Time series

A time-series database is a database optimized for time-stamped, or time series, data.

**Advantages**

- Fast insertion and retrieval
- Efficient data storage

**Use cases**

- IoT data
- Metrics analysis
- Application monitoring
- Understand financial trends

**Examples**

- [InfluxDB](https://www.influxdata.com/)
- [Apache Druid](https://druid.apache.org/)

### [](https://kps.hashnode.dev/system-design-the-complete-course?ref=dailydev#heading-wide-column "Permalink")Wide column

Wide column databases, also known as wide column stores, are schema-agnostic. Data is stored in column families, rather than in rows and columns.

**Advantages**

- Highly scalable, can handle petabytes of data
- Ideal for real-time big data applications

**Disadvantages**

- Expensive
- Increased write time

**Use cases**

- Business analytics
- Attribute-based data storage

**Examples**

- [BigTable](https://cloud.google.com/bigtable)
- [Apache Cassandra](https://cassandra.apache.org/)
- [ScyllaDB](https://www.scylladb.com/)

### [](https://kps.hashnode.dev/system-design-the-complete-course?ref=dailydev#heading-multi-model "Permalink")Multi-model

Multi-model databases combine different database models (i.e. relational, graph, key-value, document, etc.) into a single, integrated backend. This means they can accommodate various data types, indexes, queries, and store data in more than one model.

**Advantages**

- Flexibility
- Suitable for complex projects
- Data consistent

**Disadvantages**

- Complex
- Less mature

**Examples**

- [ArangoDB](https://www.arangodb.com/)
- [Azure Cosmos DB](https://azure.microsoft.com/en-in/services/cosmos-db)
- [Couchbase](https://www.couchbase.com/)

# [](https://kps.hashnode.dev/system-design-the-complete-course?ref=dailydev#heading-sql-vs-nosql-databases "Permalink")SQL vs NoSQL databases

In the world of databases, there are two main types of solutions, SQL (relational) and NoSQL (non-relational) databases. Both of them differ in the way they were built, the kind of information they store, and how they store it. Relational databases are structured and have predefined schemas while non-relational databases are unstructured, distributed, and have a dynamic schema.

## [](https://kps.hashnode.dev/system-design-the-complete-course?ref=dailydev#heading-high-level-differences "Permalink")High-level differences

Here are some high-level differences between SQL and NoSQL:

### [](https://kps.hashnode.dev/system-design-the-complete-course?ref=dailydev#heading-storage "Permalink")Storage

SQL stores data in tables, where each row represents an entity and each column represents a data point about that entity.

NoSQL databases have different data storage models such as key-value, graph, document, etc.

### [](https://kps.hashnode.dev/system-design-the-complete-course?ref=dailydev#heading-schema "Permalink")Schema

In SQL, each record conforms to a fixed schema, meaning the columns must be decided and chosen before data entry and each row must have data for each column. The schema can be altered later, but it involves modifying the database using migrations.

Whereas in NoSQL, schemas are dynamic. Columns can be added on the fly, and each _row_ (or equivalent) doesn't have to contain data for each _column_.

### [](https://kps.hashnode.dev/system-design-the-complete-course?ref=dailydev#heading-querying "Permalink")Querying

SQL databases use SQL (structured query language) for defining and manipulating the data, which is very powerful.

In a NoSQL database, queries are focused on a collection of documents. Different databases have different syntax for querying.

### [](https://kps.hashnode.dev/system-design-the-complete-course?ref=dailydev#heading-scalability "Permalink")Scalability

In most common situations, SQL databases are vertically scalable, which can get very expensive. It is possible to scale a relational database across multiple servers, but this is a challenging and time-consuming process.

On the other hand, NoSQL databases are horizontally scalable, meaning we can add more servers easily to our NoSQL database infrastructure to handle large traffic. Any cheap commodity hardware or cloud instances can host NoSQL databases, thus making it a lot more cost-effective than vertical scaling. A lot of NoSQL technologies also distribute data across servers automatically.

### [](https://kps.hashnode.dev/system-design-the-complete-course?ref=dailydev#heading-reliability "Permalink")Reliability

The vast majority of relational databases are ACID compliant. So, when it comes to data reliability and a safe guarantee of performing transactions, SQL databases are still the better bet.

Most of the NoSQL solutions sacrifice ACID compliance for performance and scalability.

## [](https://kps.hashnode.dev/system-design-the-complete-course?ref=dailydev#heading-reasons "Permalink")Reasons

As always we should always pick the technology that fits the requirements better. So, let's look at some reasons for picking SQL or NoSQL based database:

**For SQL**

- Structured data with strict schema
- Relational data
- Need for complex joins
- Transactions
- Lookups by index are very fast

**For NoSQL**

- Dynamic or flexible schema
- Non-relational data
- No need for complex joins
- Very data-intensive workload
- Very high throughput for IOPS