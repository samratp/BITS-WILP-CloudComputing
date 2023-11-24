Key-Value NoSQL databases store data as a collection of key-value pairs, where each key is unique and associated with a specific value. Here are the key characteristics and examples of Key-Value NoSQL databases:

**Characteristics:**

1. **Simplicity:** Key-Value stores are among the simplest NoSQL databases, focusing on efficient storage and retrieval of data based on unique keys.

2. **Schema-less:** These databases are schema-less, meaning that each key-value pair can have a different structure, and the database doesn't enforce a fixed schema.

3. **High Performance:** Key-Value stores are designed for high-speed reads and writes, making them suitable for caching and scenarios where rapid data access is critical.

4. **Scalability:** Many Key-Value stores are horizontally scalable, allowing for the distribution of data across multiple nodes to handle large amounts of data and high read/write throughput.

5. **Use of Redis Data Structures:** Some Key-Value stores like Redis provide additional data structures (e.g., lists, sets, hashes) and support complex operations on these structures.

**Examples of Key-Value NoSQL Databases:**

1. **Redis:**
   - **Key Features:** In-memory data store, supports various data structures (strings, lists, sets, hashes), persistence options, and pub/sub messaging.

2. **Amazon DynamoDB:**
   - **Key Features:** Fully managed, scalable NoSQL database service by AWS. Provides consistent, single-digit millisecond latency at any scale.

3. **Apache Cassandra:**
   - **Key Features:** Distributed and decentralized architecture, fault-tolerant, tunable consistency, and support for large-scale distributed deployments.

4. **Riak:**
   - **Key Features:** Distributed and fault-tolerant, designed for high availability and fault tolerance, supports eventual consistency.

5. **Berkeley DB:**
   - **Key Features:** Embeddable database, ACID transactions, supports various access methods including Key-Value.

Key-Value stores are suitable for use cases where the data model can be simplified to key-value pairs, and the emphasis is on fast and straightforward access to data based on unique identifiers. Common applications include caching, session storage, and distributed data storage.
