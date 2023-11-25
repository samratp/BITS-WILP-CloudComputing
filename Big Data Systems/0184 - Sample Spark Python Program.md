Let's assume you have a text file named `sample.txt` with the following content:

**sample.txt:**
```
1
2
3
4
5
6
7
8
9
10
```

Now, let's create a Python program (`spark_example.py`) to read this file, perform some operations using Spark, and print the output:

**spark_example.py:**
```python
from pyspark import SparkContext, SparkConf

# Create a Spark configuration and set the application name
conf = SparkConf().setAppName("SparkExample")
sc = SparkContext(conf=conf)

# Load data from the sample file into an RDD
file_path = "sample.txt"
data = sc.textFile(file_path)

# Transformation: Map - Convert each line to an integer
integer_rdd = data.map(lambda x: int(x))

# Transformation: Filter - Keep only even numbers
even_rdd = integer_rdd.filter(lambda x: x % 2 == 0)

# Action: Collect - Retrieve the results to the driver program
result = even_rdd.collect()

# Print the result
print("Even numbers in the file:", result)

# Stop the SparkContext
sc.stop()
```



**Output:**
When you run the program using `spark-submit spark_example.py`, the output should be:

```
Even numbers in the file: [2, 4, 6, 8, 10]
```

This output indicates that the program has successfully read the file, converted each line to an integer, filtered out the even numbers, and collected the result for printing. The resulting list contains the even numbers present in the `sample.txt` file.
