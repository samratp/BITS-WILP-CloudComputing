In Apache Spark, actions are operations on Resilient Distributed Datasets (RDDs) that trigger the execution of the Spark computation plan and return a result to the driver program or write data to an external storage system. Actions are the operations that actually perform the computations and produce final results. Here are some common RDD actions in Spark:

1. **`collect()` Action:**
   - Returns all the elements of the RDD as an array to the driver program.

   ```python
   rdd = sc.parallelize([1, 2, 3, 4, 5])
   result = rdd.collect()
   # Output: [1, 2, 3, 4, 5]
   ```

2. **`count()` Action:**
   - Returns the number of elements in the RDD.

   ```python
   count = rdd.count()
   # Output: 5
   ```

3. **`first()` Action:**
   - Returns the first element of the RDD.

   ```python
   first_element = rdd.first()
   # Output: 1
   ```

4. **`take(n)` Action:**
   - Returns the first `n` elements of the RDD.

   ```python
   first_three_elements = rdd.take(3)
   # Output: [1, 2, 3]
   ```

5. **`top(n)` Action:**
   - Returns the top `n` elements of the RDD in descending order.

   ```python
   top_three_elements = rdd.top(3)
   # Output: [5, 4, 3]
   ```

6. **`reduce(func)` Action:**
   - Aggregates the elements of the RDD using a specified associative and commutative function.

   ```python
   total_sum = rdd.reduce(lambda x, y: x + y)
   # Output: 15
   ```

7. **`foreach(func)` Action:**
   - Applies a function to each element of the RDD. This is typically used for side-effects.

   ```python
   def print_element(x):
       print(x)

   rdd.foreach(print_element)
   # Output: (prints each element)
   ```

8. **`countByKey()` Action:**
   - Counts the number of occurrences of each key in a key-value pair RDD.

   ```python
   key_value_rdd = sc.parallelize([(1, 'a'), (2, 'b'), (1, 'c'), (2, 'd')])
   count_by_key = key_value_rdd.countByKey()
   # Output: {1: 2, 2: 2}
   ```

9. **`collectAsMap()` Action:**
   - Returns the key-value pairs of a key-value pair RDD as a dictionary to the driver program.

   ```python
   key_value_pairs = key_value_rdd.collectAsMap()
   # Output: {1: 'c', 2: 'd'}
   ```

10. **`saveAsTextFile(path)` Action:**
    - Saves the elements of the RDD as a text file with the specified path.

    ```python
    rdd.saveAsTextFile('output_directory')
    # Output: (saves the RDD elements to text files in the 'output_directory' directory)
    ```

11. **`foreachPartition(func)` Action:**
    - Applies a function to each partition of the RDD. This is typically used for side-effects.

    ```python
    def process_partition(iter):
        for x in iter:
            print(x)

    rdd.foreachPartition(process_partition)
    # Output: (prints each element in each partition)
    ```

12. **`takeSample(withReplacement, num, seed)` Action:**
    - Returns a random sample of `num` elements from the RDD, with or without replacement.

    ```python
    random_sample = rdd.takeSample(False, 2, 42)
    # Output: (returns a random sample of 2 elements without replacement)
    ```

These actions trigger the execution of the Spark computation plan and produce results. It's important to note that actions are what initiate the actual computation, and they are typically preceded by transformations that define the sequence of operations to be performed on the RDD.
