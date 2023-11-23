To create a MapReduce program using the Hadoop Python library, you can use the `mrjob` library. Below is an example of a word count program using `mrjob`.

**1. WordCountMRJob:**
```python
from mrjob.job import MRJob
import re

class WordCountMRJob(MRJob):

    def mapper(self, _, line):
        # Tokenize the input line and emit each word with a count of 1
        words = re.findall(r'\b\w+\b', line)
        for word in words:
            yield (word.lower(), 1)

    def reducer(self, key, values):
        # Sum the counts for each word
        yield (key, sum(values))

if __name__ == '__main__':
    WordCountMRJob.run()
```

**2. Driver Script: wordcount.sh**
```bash
#!/bin/bash
# Driver script to run the MapReduce job using WordCountMRJob

# Set input and output paths
INPUT_PATH="hdfs://input_path/input.txt"
OUTPUT_PATH="hdfs://output_path/output"

# Run the Hadoop Python MapReduce job
python WordCountMRJob.py -r hadoop $INPUT_PATH --output-dir=$OUTPUT_PATH
```

Make sure to replace `hdfs://input_path/input.txt` and `hdfs://output_path/output` with your actual input and output paths.

To run the job, execute the driver script:
```bash
bash wordcount.sh
```

Ensure that you have `mrjob` installed in your Python environment:
```bash
pip install mrjob
```

This example uses the `mrjob` library to simplify the creation of MapReduce jobs in Python. The `WordCountMRJob` class defines the mapper and reducer functions, and the driver script (`wordcount.sh`) specifies the input and output paths.
