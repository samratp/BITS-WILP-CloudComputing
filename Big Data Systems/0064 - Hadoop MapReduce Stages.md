In a Hadoop MapReduce job, there are two main stages: the Map stage and the Reduce stage.

1. **Map Stage:**
   - **Input:** The input data is divided into fixed-size splits, and each split is processed by a separate map task.
   - **Map Function:** The user-defined map function is applied to each record in the split independently. The map function emits key-value pairs as intermediate output.
   - **Shuffle and Sort:** The framework sorts and groups the intermediate key-value pairs by key. This process is known as the shuffle and sort phase.
   - **Partitioning:** The intermediate key-value pairs are partitioned into different sets based on the key. Each partition is sent to a separate reduce task.

2. **Reduce Stage:**
   - **Input:** Each reduce task receives a set of key-value pairs from the map tasks, grouped by key.
   - **Reduce Function:** The user-defined reduce function is applied to each group of key-value pairs. The output of the reduce function is the final output of the MapReduce job.
   - **Output:** The final output is typically written to an HDFS directory or another storage system.

**Workflow:**
1. **Input Data Splitting:** The input data is divided into fixed-size splits, and each split is processed by a separate map task.
2. **Map Function Execution:** The map function is applied to each record in the split independently, generating intermediate key-value pairs.
3. **Shuffle and Sort:** The framework sorts and groups the intermediate key-value pairs by key, preparing them for the reduce stage.
4. **Partitioning and Data Transfer:** The intermediate key-value pairs are partitioned into sets based on the key and sent to the corresponding reduce tasks.
5. **Reduce Function Execution:** Each reduce task applies the reduce function to its set of key-value pairs, producing the final output.
6. **Final Output:** The final output is typically stored in HDFS or another storage system.

The key-value pairs produced by the map function and consumed by the reduce function are the essential components that facilitate the distribution of data processing in a parallel and scalable manner across a Hadoop cluster. The partitioning, shuffle, and sort phases are critical for optimizing data movement and reducing network traffic during the MapReduce job execution.
