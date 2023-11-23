To implement a MapReduce algorithm to sort employees by salary in Java, you would typically have a set of Java classes for Mapper, Reducer, and the main driver program. Below is a simple example:

Assuming you have an Employee class like this:

```java
public class Employee {
    private String name;
    private double salary;

    // Constructors, getters, setters

    // toString() method for displaying output
    @Override
    public String toString() {
        return name + "\t" + salary;
    }
}
```

Here's how you can implement the MapReduce job:

1. **Mapper Class:**

```java
import java.io.IOException;
import org.apache.hadoop.io.LongWritable;
import org.apache.hadoop.io.Text;
import org.apache.hadoop.mapreduce.Mapper;

public class SalarySortMapper extends Mapper<LongWritable, Text, DoubleWritable, Text> {

    private final DoubleWritable salary = new DoubleWritable();
    private final Text employeeData = new Text();

    @Override
    protected void map(LongWritable key, Text value, Context context) throws IOException, InterruptedException {
        // Parse the input data (assuming tab-separated values)
        String[] tokens = value.toString().split("\t");

        if (tokens.length == 2) {
            String name = tokens[0];
            double salaryValue = Double.parseDouble(tokens[1]);

            // Set the salary as the key (for sorting)
            salary.set(salaryValue);
            // Set the employee data as the value
            employeeData.set(name);

            // Emit key-value pair
            context.write(salary, employeeData);
        }
    }
}
```

2. **Reducer Class:**

```java
import java.io.IOException;
import org.apache.hadoop.io.DoubleWritable;
import org.apache.hadoop.io.Text;
import org.apache.hadoop.mapreduce.Reducer;

public class SalarySortReducer extends Reducer<DoubleWritable, Text, Text, DoubleWritable> {

    @Override
    protected void reduce(DoubleWritable key, Iterable<Text> values, Context context)
            throws IOException, InterruptedException {

        // Iterate through the values (employee names)
        for (Text value : values) {
            // Emit name and salary
            context.write(value, key);
        }
    }
}
```

3. **Driver Class:**

```java
import org.apache.hadoop.fs.Path;
import org.apache.hadoop.io.DoubleWritable;
import org.apache.hadoop.io.Text;
import org.apache.hadoop.mapreduce.Job;
import org.apache.hadoop.mapreduce.lib.input.FileInputFormat;
import org.apache.hadoop.mapreduce.lib.output.FileOutputFormat;

public class SalarySortDriver {

    public static void main(String[] args) throws Exception {
        // Create a new MapReduce job
        Job job = Job.getInstance();
        job.setJarByClass(SalarySortDriver.class);
        job.setJobName("SalarySort");

        // Set the input and output paths
        FileInputFormat.addInputPath(job, new Path(args[0]));
        FileOutputFormat.setOutputPath(job, new Path(args[1]));

        // Set the Mapper and Reducer classes
        job.setMapperClass(SalarySortMapper.class);
        job.setReducerClass(SalarySortReducer.class);

        // Set the output key and value classes
        job.setOutputKeyClass(DoubleWritable.class);
        job.setOutputValueClass(Text.class);

        // Wait for the job to complete and print the result
        System.exit(job.waitForCompletion(true) ? 0 : 1);
    }
}
```

To run this program, you would compile the classes, create a JAR file, and then submit it to Hadoop with the necessary input and output paths. The input data should be tab-separated, with each line containing an employee name and salary. The output will be sorted by salary.
