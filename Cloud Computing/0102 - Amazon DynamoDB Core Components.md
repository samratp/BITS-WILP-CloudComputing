Amazon DynamoDB is composed of several core components that work together to provide a highly scalable and fully managed NoSQL database service. Here are the key components of Amazon DynamoDB:

1. **Tables:**
   - In DynamoDB, data is organized and stored in tables. A table is a collection of items, and each item is a collection of attributes. Tables in DynamoDB are schema-less, meaning that individual items within a table can have different attributes.

2. **Items:**
   - An item is a set of attributes that is uniquely identifiable among all other items in a table. Items are the basic units of data in DynamoDB. Each item must have a primary key attribute or a composite primary key that uniquely identifies it within the table.

3. **Attributes:**
   - Attributes are the fundamental data elements within an item. Each attribute has a name and a value. DynamoDB supports various data types for attributes, including scalar types (such as String, Number, Binary), Set types (String Set, Number Set, Binary Set), and document types (List and Map).

4. **Primary Key:**
   - Every table in DynamoDB must have a primary key, which can be either a single attribute (simple primary key) or a combination of two attributes (composite primary key). The primary key uniquely identifies each item in the table.

5. **Secondary Indexes:**
   - DynamoDB supports the creation of secondary indexes to provide more flexibility in querying the data. Secondary indexes allow you to query the table based on non-primary key attributes. There are two types of secondary indexes: Local Secondary Indexes (LSIs) and Global Secondary Indexes (GSIs).

   - **Local Secondary Index (LSI):**
     - An index with a range key that is different from the primary key. It is limited to tables with a composite primary key.

   - **Global Secondary Index (GSI):**
     - An index with a primary key that can be different from the table's primary key. It can span multiple partitions and allows for more flexible querying.

6. **Partitions and Partition Keys:**
   - DynamoDB automatically partitions data across multiple servers to ensure scalability and performance. Each partition is known as a partition key space. The partition key is used to distribute items across these partitions. Efficient partitioning is crucial for achieving high throughput.

7. **Streams:**
   - DynamoDB Streams capture changes to items in a table in real-time. Each stream record represents a change to an item and includes information such as the type of change (insert, modify, or delete) and the item's data.

8. **Read and Write Capacity Units:**
   - DynamoDB uses a provisioned throughput model, where you specify the read and write capacity units when creating a table. Capacity units represent the amount of throughput your table can handle. DynamoDB automatically scales resources based on the configured capacity units.

9. **On-Demand Capacity:**
   - In addition to provisioned throughput, DynamoDB offers on-demand capacity, where you pay per request rather than pre-provisioning capacity. On-demand capacity is suitable for workloads with unpredictable or variable traffic.

10. **DynamoDB Accelerator (DAX):**
    - DynamoDB Accelerator (DAX) is an optional, fully managed, in-memory caching service that can be used to accelerate the performance of read-intensive DynamoDB workloads.

11. **Point-in-Time Recovery:**
    - DynamoDB provides point-in-time recovery, allowing you to restore a table to any specific point in time within the retention period. This feature helps protect against accidental data loss or corruption.

12. **Global Tables:**
    - DynamoDB Global Tables enable multi-region, multi-master deployments. It allows you to create replicas of your tables in multiple AWS regions for low-latency access and improved disaster recovery.

These core components work together to provide a flexible, scalable, and fully managed NoSQL database solution in Amazon DynamoDB. Developers can leverage these components to build applications that require high-performance, low-latency data access.
