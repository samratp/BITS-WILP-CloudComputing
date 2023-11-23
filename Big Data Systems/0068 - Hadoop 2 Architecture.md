Hadoop 2, also known as Apache Hadoop 2.x, introduced several significant changes and improvements over its predecessor, Hadoop 1.x. The major enhancements in Hadoop 2 architecture include the introduction of YARN (Yet Another Resource Negotiator), which decouples the resource management and job scheduling capabilities from the MapReduce programming model. This allows Hadoop to support multiple processing engines beyond MapReduce.

Here's a high-level overview of the Hadoop 2 architecture:

1. **Hadoop Common:**
   - The core libraries and utilities that are shared by other Hadoop modules.
   - It includes the Hadoop Distributed File System (HDFS) for storage and retrieval of large data sets.

2. **Hadoop YARN (Yet Another Resource Negotiator):**
   - YARN is a major addition in Hadoop 2, serving as the resource management layer.
   - It allows multiple distributed data processing engines to run on the same Hadoop cluster, making Hadoop more versatile.
   - YARN has two main components:
     - Resource Manager: Manages and allocates resources across various applications.
     - Node Manager: Manages resources on a single node in the cluster.

3. **MapReduce 2:**
   - MapReduce remains a key processing engine in Hadoop 2, but it runs on top of YARN.
   - The MapReduce application is split into two separate daemons: the Application Master (AM) and the actual Task containers.
   - The AM negotiates resources with the Resource Manager and manages the execution of tasks.

4. **HDFS Federation:**
   - HDFS Federation is introduced to improve scalability by allowing multiple independent namespaces (namespaces are collections of files and directories) in a single Hadoop cluster.
   - Each namespace has its own namespace ID and block pool ID.

5. **High Availability (HA) for HDFS:**
   - Hadoop 2 introduced HA capabilities for HDFS, addressing a critical limitation in Hadoop 1.x.
   - The HA setup involves multiple NameNodes where one is active and the other is in standby mode. If the active NameNode fails, the standby can take over.

6. **Other Components:**
   - Various other components and projects can be integrated with Hadoop 2, such as Apache Hive, Apache HBase, Apache Pig, Apache Oozie, Apache Spark, and more.

7. **Hadoop Ecosystem:**
   - The Hadoop ecosystem has expanded with additional projects and tools to complement Hadoop's capabilities, including Apache Spark for in-memory processing, Apache Flink for stream processing, Apache Kafka for messaging, and more.

Hadoop 2's architecture provides greater flexibility and scalability, enabling it to support a broader range of applications and workloads beyond traditional MapReduce jobs. The introduction of YARN and HDFS improvements were pivotal in making Hadoop a more versatile big data platform.
