Hadoop 2, also known as Apache Hadoop 2.x, introduced significant architectural changes and improvements over its predecessor, Hadoop 1.x. The major enhancement was the introduction of the YARN (Yet Another Resource Negotiator) architecture. Below is an overview of the key components of Hadoop 2.x architecture:

1. **HDFS (Hadoop Distributed File System)**:

   - **NameNode**:
     - The NameNode in Hadoop 2.x is similar to Hadoop 1.x. It manages the metadata and namespace of the file system. However, it no longer handles job scheduling for compute resources.

   - **DataNode**:
     - DataNodes are responsible for storing and managing the actual data blocks in the distributed file system.

   - **Secondary NameNode**:
     - The Secondary NameNode in Hadoop 2.x performs periodic checkpoints of the namespace to support faster recovery in case of NameNode failures. It does not play a role in job scheduling.

2. **YARN (Yet Another Resource Negotiator)**:

   - YARN is the most significant addition in Hadoop 2.x. It is a resource management layer that separates the processing and resource management functions. YARN consists of:

   - **Resource Manager**:
     - The Resource Manager manages resources across the entire Hadoop cluster. It negotiates resources from the NodeManagers and allocates them to various applications.

   - **NodeManager**:
     - NodeManagers are responsible for managing resources on individual nodes. They are responsible for launching and monitoring application containers, which are the actual processes that run the tasks.

   - **Application Master**:
     - Each application running on YARN has its own Application Master. The Application Master is responsible for negotiating resources with the Resource Manager and for managing task execution.

3. **MapReduce v2**:

   - MapReduce in Hadoop 2.x operates on top of YARN. It no longer requires the JobTracker to manage resources. Instead, MapReduce jobs are submitted to the YARN ResourceManager.

4. **Hadoop Common**:

   - This includes the libraries and utilities shared by all Hadoop components. It contains common tools and resources that are used by various Hadoop modules.

5. **Hadoop Ecosystem Components**:

   - Hadoop 2.x can integrate with a wide range of additional components and frameworks, such as Hive, Pig, HBase, Spark, and many others. These components can run on top of YARN and take advantage of the enhanced resource management capabilities.

6. **Other Components**:

   - In addition to the core components mentioned above, Hadoop 2.x may include other tools and frameworks based on specific use cases, such as Ambari for cluster management, Oozie for workflow scheduling, and more.

The introduction of YARN in Hadoop 2.x greatly expanded the capabilities of the Hadoop ecosystem by allowing it to support a wide variety of processing models beyond just MapReduce. This made it possible to run a diverse set of applications and frameworks in a unified and efficient manner on a Hadoop cluster.
