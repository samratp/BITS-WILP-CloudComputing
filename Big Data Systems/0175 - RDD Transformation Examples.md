Below are some examples of RDD transformations in Apache Spark, along with details and expected outputs. Let's assume we have an RDD of integers for these examples.

```python
# Sample RDD
data = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
rdd = sc.parallelize(data)
```

1. **Map Transformation:**
   - Applies a function to each element in the RDD.

```python
mapped_rdd = rdd.map(lambda x: x * 2)
# Output: [2, 4, 6, 8, 10, 12, 14, 16, 18, 20]
```

2. **Filter Transformation:**
   - Filters elements based on a given condition.

```python
filtered_rdd = rdd.filter(lambda x: x % 2 == 0)
# Output: [2, 4, 6, 8, 10]
```

3. **FlatMap Transformation:**
   - Similar to `map`, but each input item can be mapped to 0 or more output items.

```python
flat_mapped_rdd = rdd.flatMap(lambda x: (x, x * 2))
# Output: [1, 2, 2, 4, 3, 6, 4, 8, 5, 10, 6, 12, 7, 14, 8, 16, 9, 18, 10, 20]
```

4. **Union Transformation:**
   - Combines two RDDs.

```python
other_data = [11, 12, 13, 14, 15]
other_rdd = sc.parallelize(other_data)
union_rdd = rdd.union(other_rdd)
# Output: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15]
```

5. **Intersection Transformation:**
   - Computes the intersection of two RDDs.

```python
intersection_rdd = rdd.intersection(other_rdd)
# Output: []
```

6. **Distinct Transformation:**
   - Returns a new RDD with distinct elements.

```python
distinct_rdd = union_rdd.distinct()
# Output: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15]
```

7. **GroupByKey Transformation:**
   - Groups the elements of the RDD by key.

```python
key_value_rdd = rdd.map(lambda x: (x % 2, x))
grouped_rdd = key_value_rdd.groupByKey()
# Output: [(0, <pyspark.resultiterable.ResultIterable object at 0x...>), (1, <pyspark.resultiterable.ResultIterable object at 0x...>)]
```

8. **ReduceByKey Transformation:**
   - Aggregates values for each key using a specified reduce function.

```python
sum_by_key_rdd = key_value_rdd.reduceByKey(lambda x, y: x + y)
# Output: [(0, 30), (1, 25)]
```

9. **MapValues Transformation:**
   - Applies a function to each value of a key-value pair.

```python
mapped_values_rdd = key_value_rdd.mapValues(lambda x: x * 2)
# Output: [(1, 2), (2, 4), (3, 6), (4, 8), (5, 10), (6, 12), (7, 14), (8, 16), (9, 18), (10, 20)]
```

10. **SortByKey Transformation:**
    - Sorts key-value pairs by key.

```python
sorted_rdd = key_value_rdd.sortByKey()
# Output: [(0, 2), (0, 4), (0, 6), (0, 8), (0, 10), (1, 1), (1, 3), (1, 5), (1, 7), (1, 9)]
```

11. **Cogroup Transformation:**
    - Groups the values of several key-value RDDs by their keys.

```python
other_key_value_rdd = other_rdd.map(lambda x: (x % 2, x))
cogrouped_rdd = key_value_rdd.cogroup(other_key_value_rdd)
# Output: [(0, (<pyspark.resultiterable.ResultIterable object at 0x...>, <pyspark.resultiterable.ResultIterable object at 0x...>)), (1, (<pyspark.resultiterable.ResultIterable object at 0x...>, <pyspark.resultiterable.ResultIterable object at 0x...>))]
```

12. **Cartesian Transformation:**
    - Computes the Cartesian product of two RDDs.

```python
cartesian_rdd = rdd.cartesian(other_rdd)
# Output: [(1, 11), (1, 12), (1, 13), ..., (10, 13), (10, 14), (10, 15)]
```

13. **Coalesce Transformation:**
    - Reduces the number of partitions in the RDD.

```python
coalesced_rdd = rdd.coalesce(2)
# Output: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
```

14. **Repartition Transformation:**
    - Increases or decreases the number of partitions in the RDD.

```python
repartitioned_rdd = rdd.repartition(3)
# Output: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
```

15. **Zip Transformation:**
    - Zips two RDDs together, creating key-value pairs.

```python
zipped_rdd = rdd.zip(other_rdd)


# Output: [(1, 11), (2, 12), (3, 13), (4, 14), (5, 15)]
```

16. **Pipe Transformation:**
    - Passes each partition of the RDD through a shell command.

```python
pipe_rdd = rdd.pipe("grep 1")
# Output: ['1', '10']
```

17. **MapPartitions Transformation:**
    - Applies a function to each partition of the RDD.

```python
def multiply_partition(iter):
    return (x * 2 for x in iter)

map_partitions_rdd = rdd.mapPartitions(multiply_partition)
# Output: [2, 4, 6, 8, 10, 12, 14, 16, 18, 20]
```

18. **Coalesce Transformation (with shuffle):**
    - Similar to `coalesce`, but with optional shuffle to balance data across partitions.

```python
coalesced_with_shuffle_rdd = rdd.coalesce(2, shuffle=True)
# Output: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
```

19. **Repartition Transformation (with shuffle):**
    - Similar to `repartition`, but with optional shuffle to balance data across partitions.

```python
repartitioned_with_shuffle_rdd = rdd.repartition(3, shuffle=True)
# Output: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
```

20. **MapPartitionsWithIndex Transformation:**
    - Applies a function to each partition of the RDD along with its index.

```python
def add_index(partition_index, iter):
    return ((partition_index, x) for x in iter)

map_partitions_with_index_rdd = rdd.mapPartitionsWithIndex(add_index)
# Output: [(0, 1), (0, 2), ..., (9, 10)]
```

Note: The actual output might differ depending on the Spark environment and the number of partitions in your RDD. Additionally, some transformations, like `groupByKey`, return iterators in the output, which are represented as `<pyspark.resultiterable.ResultIterable object...>` in the examples.
