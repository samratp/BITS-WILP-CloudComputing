In Apache Spark, transformations on Resilient Distributed Datasets (RDDs) are categorized into two types based on their impact on the number of partitions: narrow transformations and wide transformations.

### Narrow Transformations:

Narrow transformations are those transformations where each input partition contributes to at most one output partition. The computation can be performed independently on each partition, without shuffling or redistributing data across partitions.

#### Example 1: `map`

```python
rdd = sc.parallelize([1, 2, 3, 4, 5])
mapped_rdd = rdd.map(lambda x: x * 2)
# Output: [2, 4, 6, 8, 10]
```

#### Example 2: `filter`

```python
filtered_rdd = rdd.filter(lambda x: x % 2 == 0)
# Output: [2, 4]
```

#### Example 3: `flatMap`

```python
flat_mapped_rdd = rdd.flatMap(lambda x: (x, x * 2))
# Output: [1, 2, 2, 4, 3, 6, 4, 8, 5, 10]
```

### Wide Transformations:

Wide transformations are those transformations that may result in a shuffling of data across partitions, and each output partition depends on multiple input partitions. They involve redistributing and reshuffling the data, often across the network.

#### Example 1: `groupByKey`

```python
key_value_rdd = rdd.map(lambda x: (x % 2, x))
grouped_rdd = key_value_rdd.groupByKey()
# Output: [(0, <pyspark.resultiterable.ResultIterable object at 0x...>), (1, <pyspark.resultiterable.ResultIterable object at 0x...>)]
```

#### Example 2: `reduceByKey`

```python
sum_by_key_rdd = key_value_rdd.reduceByKey(lambda x, y: x + y)
# Output: [(0, 30), (1, 25)]
```

#### Example 3: `join`

```python
other_rdd = sc.parallelize([(1, 'a'), (2, 'b'), (1, 'c'), (2, 'd')])
other_key_value_rdd = other_rdd.map(lambda x: (x[0], x[1]))
joined_rdd = key_value_rdd.join(other_key_value_rdd)
# Output: [(1, (2, 'a')), (1, (2, 'c'))]
```

### Explanation:

- **Narrow Transformations:**
  - These transformations operate on a single partition of the RDD at a time.
  - They don't require data to be shuffled across the network.
  - Examples include `map`, `filter`, `flatMap`, etc.
  - Narrow transformations are more efficient in terms of computation.

- **Wide Transformations:**
  - These transformations involve shuffling and redistributing data across partitions.
  - They may result in data movement across the network, impacting performance.
  - Examples include `groupByKey`, `reduceByKey`, `join`, etc.
  - Wide transformations are often associated with the `shuffle` stage in Spark.

It's important to choose the right transformations based on the nature of the computation and the requirements of the task. While narrow transformations are generally faster, wide transformations are necessary for operations that involve combining or aggregating data across multiple partitions. The choice of transformations impacts the efficiency and performance of Spark jobs.
