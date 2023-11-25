In Apache Spark, Resilient Distributed Datasets (RDDs) are the fundamental data structure representing distributed collections of objects that can be processed in parallel. RDD transformations are operations that create a new RDD from an existing one. Here are some common RDD transformations in Spark:

1. **`map(func)` Transformation:**
   - Applies a function to each element in the RDD, producing a new RDD.

   ```python
   rdd = sc.parallelize([1, 2, 3, 4, 5])
   mapped_rdd = rdd.map(lambda x: x * 2)
   # Output: [2, 4, 6, 8, 10]
   ```

2. **`filter(func)` Transformation:**
   - Selects elements from the RDD that satisfy a given condition.

   ```python
   filtered_rdd = rdd.filter(lambda x: x % 2 == 0)
   # Output: [2, 4]
   ```

3. **`flatMap(func)` Transformation:**
   - Similar to `map`, but each input item can be mapped to 0 or more output items.

   ```python
   flat_mapped_rdd = rdd.flatMap(lambda x: (x, x * 2))
   # Output: [1, 2, 2, 4, 3, 6, 4, 8, 5, 10]
   ```

4. **`union(other)` Transformation:**
   - Combines two RDDs into one.

   ```python
   other_rdd = sc.parallelize([6, 7, 8, 9, 10])
   union_rdd = rdd.union(other_rdd)
   # Output: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
   ```

5. **`distinct(numPartitions)` Transformation:**
   - Returns a new RDD with distinct elements.

   ```python
   distinct_rdd = union_rdd.distinct()
   # Output: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
   ```

6. **`groupByKey()` Transformation:**
   - Groups the values for each key in a key-value pair RDD.

   ```python
   key_value_rdd = rdd.map(lambda x: (x % 2, x))
   grouped_rdd = key_value_rdd.groupByKey()
   # Output: [(0, <pyspark.resultiterable.ResultIterable object at 0x...>), (1, <pyspark.resultiterable.ResultIterable object at 0x...>)]
   ```

7. **`reduceByKey(func)` Transformation:**
   - Aggregates values for each key using a specified reduce function.

   ```python
   sum_by_key_rdd = key_value_rdd.reduceByKey(lambda x, y: x + y)
   # Output: [(0, 30), (1, 25)]
   ```

8. **`sortByKey(ascending)` Transformation:**
   - Sorts key-value pairs by key.

   ```python
   sorted_rdd = key_value_rdd.sortByKey()
   # Output: [(0, 2), (0, 4), (0, 6), (0, 8), (0, 10), (1, 1), (1, 3), (1, 5), (1, 7), (1, 9)]
   ```

9. **`join(other, numPartitions)` Transformation:**
   - Performs an inner join between two key-value pair RDDs.

   ```python
   other_key_value_rdd = other_rdd.map(lambda x: (x % 2, x))
   joined_rdd = key_value_rdd.join(other_key_value_rdd)
   # Output: [(0, (2, 6)), (0, (2, 8)), (0, (4, 6)), (0, (4, 8)), (1, (1, 7)), (1, (3, 9)), (1, (5, 7)), (1, (5, 9))]
   ```

10. **`cogroup(other, numPartitions)` Transformation:**
    - Groups the values of several key-value pair RDDs by their keys.

    ```python
    cogrouped_rdd = key_value_rdd.cogroup(other_key_value_rdd)
    # Output: [(0, (<pyspark.resultiterable.ResultIterable object at 0x...>, <pyspark.resultiterable.ResultIterable object at 0x...>)), (1, (<pyspark.resultiterable.ResultIterable object at 0x...>, <pyspark.resultiterable.ResultIterable object at 0x...>))]
    ```

11. **`cartesian(other)` Transformation:**
    - Computes the Cartesian product of two RDDs.

    ```python
    cartesian_rdd = rdd.cartesian(other_rdd)
    # Output: [(1, 6), (1, 7), ..., (5, 8), (5, 9), (5, 10)]
    ```

These are some fundamental RDD transformations in Apache Spark. Each transformation creates a new RDD based on the operation applied to the original RDD. The actual output may vary depending on the Spark environment and the number of partitions in your RDD.
