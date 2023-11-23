Hadoop Streaming is a utility that comes with the Hadoop distribution and allows users to create and run MapReduce jobs with any executable or script as the mapper and/or reducer. This enables developers to use languages other than Java (such as Python, Perl, Ruby) to write their MapReduce programs.

Here's a simple example of using Hadoop Streaming with Python:

Assume you have a Python script named `mapper.py` for the mapper and `reducer.py` for the reducer.

1. **mapper.py:**

```python
#!/usr/bin/env python
import sys

# Input comes from standard input (stdin)
for line in sys.stdin:
    # Remove leading and trailing whitespaces
    line = line.strip()
    # Split the line into words
    words = line.split()
    
    # Emit each word with a count of 1
    for word in words:
        print(f"{word}\t1")
```

2. **reducer.py:**

```python
#!/usr/bin/env python
from operator import itemgetter
import sys

current_word = None
current_count = 0
word = None

# Input comes from standard input (stdin)
for line in sys.stdin:
    # Remove leading and trailing whitespaces
    line = line.strip()
    
    # Split the line into word and count
    word, count = line.split('\t', 1)
    
    # Convert count to an integer
    try:
        count = int(count)
    except ValueError:
        # If the count is not a valid integer, continue to the next line
        continue

    # If the current word is the same as the new word, update the count
    if current_word == word:
        current_count += count
    else:
        # If the current word is different, emit the result for the previous word (if it exists)
        if current_word:
            print(f"{current_word}\t{current_count}")
        # Reset variables for the new word
        current_word = word
        current_count = count

# Emit the result for the last word (if it exists)
if current_word:
    print(f"{current_word}\t{current_count}")
```

3. **Run the Hadoop Streaming command:**

Assuming your input data is in an HDFS directory named `/input` and you want the output in `/output`, you can run the following Hadoop Streaming command:

```bash
hadoop jar $HADOOP_HOME/share/hadoop/tools/lib/hadoop-streaming-*.jar \
-files mapper.py,reducer.py -mapper mapper.py -reducer reducer.py \
-input /input/* -output /output
```

This command specifies the mapper and reducer scripts using the `-files` option and indicates the input and output paths.

This is a basic example, and you can customize it based on your specific use case and requirements. The key point is that you can use non-Java languages for MapReduce tasks using Hadoop Streaming.
