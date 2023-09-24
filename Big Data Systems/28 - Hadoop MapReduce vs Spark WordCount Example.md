Certainly! Let's compare a WordCount example implemented in both Hadoop MapReduce and Apache Spark:

### WordCount Example in Hadoop MapReduce:

```java
// Mapper Class
public class WordCountMapper extends Mapper<LongWritable, Text, Text, IntWritable> {
    private final static IntWritable one = new IntWritable(1);
    private Text word = new Text();

    public void map(LongWritable key, Text value, Context context) throws IOException, InterruptedException {
        String line = value.toString();
        String[] words = line.split(" ");

        for (String w : words) {
            word.set(w);
            context.write(word, one);
        }
    }
}

// Reducer Class
public class WordCountReducer extends Reducer<Text, IntWritable, Text, IntWritable> {
    private IntWritable result = new IntWritable();

    public void reduce(Text key, Iterable<IntWritable> values, Context context) throws IOException, InterruptedException {
        int sum = 0;
        for (IntWritable val : values) {
            sum += val.get();
        }
        result.set(sum);
        context.write(key, result);
    }
}
```

### WordCount Example in Apache Spark:

```scala
import org.apache.spark._
import org.apache.spark.SparkContext._

val conf = new SparkConf().setAppName("WordCount")
val sc = new SparkContext(conf)

val textFile = sc.textFile("input.txt")

val counts = textFile.flatMap(line => line.split(" "))
                     .map(word => (word, 1))
                     .reduceByKey(_ + _)

counts.saveAsTextFile("output")
```

### Comparison:

#### Code Complexity:
- **Hadoop MapReduce**: The MapReduce code involves writing separate Mapper and Reducer classes, which requires more boilerplate code.
- **Apache Spark**: The Spark code is concise and written in a high-level language (Scala in this example).

#### In-Memory Processing:
- **Hadoop MapReduce**: Disk-based processing (intermediate data written to disk between map and reduce phases).
- **Apache Spark**: In-memory processing, which can lead to significantly faster execution times.

#### Development Time:
- **Hadoop MapReduce**: Typically requires more development time due to the need to write and manage separate Mapper and Reducer classes.
- **Apache Spark**: Faster development time due to its high-level APIs and interactive shell.

#### Performance:
- **Hadoop MapReduce**: Slower due to disk-based processing and multiple I/O operations.
- **Apache Spark**: Faster due to in-memory processing and optimized execution plans.

#### Flexibility:
- **Hadoop MapReduce**: Well-suited for batch processing tasks.
- **Apache Spark**: More versatile, supporting batch processing, real-time streaming, machine learning, and graph processing.

#### Ecosystem Integration:
- **Hadoop MapReduce**: Integrates well with the Hadoop ecosystem.
- **Apache Spark**: Integrates with Hadoop components and has its own ecosystem (e.g., Spark SQL, MLlib, etc.).

Overall, Apache Spark provides a more modern, flexible, and high-performance alternative to Hadoop MapReduce for data processing tasks. It excels in scenarios where fast processing of large datasets and real-time streaming are required.
