MapReduce is a programming model designed for processing and generating large datasets in a distributed computing environment. Here is a pseudo-code example of a simple MapReduce job along with an explanation:

### MapReduce Pseudo Code:

```plaintext
// Map Function
function map(key, value):
    // key: input file name
    // value: input file content
    
    for each word in value:
        emitIntermediate(word, 1)

// Reduce Function
function reduce(key, values):
    // key: word
    // values: list of counts
    
    total = 0
    for each count in values:
        total += count
    
    emit(key, total)
```

### Explanation:

#### Map Function:
- The `map` function takes a key (usually the input file name) and its corresponding value (content of the input file).
- It processes the input data and emits intermediate key-value pairs.
- In this example, the `map` function processes a text document and emits a key-value pair for each word. The key is the word, and the value is always `1` (indicating the occurrence of that word).

#### Reduce Function:
- The `reduce` function takes a key (in this case, a word) and a list of values (counts).
- It aggregates the values for each key and emits the final result.
- In this example, the `reduce` function takes the word as the key and sums up the counts to get the total occurrences of that word.

### Example:

Let's say we have a text document with the content: "Hello world, hello MapReduce world."

#### Map Phase:
- The `map` function processes this input and emits intermediate key-value pairs:

    ```
    (Hello, 1)
    (world, 1)
    (hello, 1)
    (MapReduce, 1)
    (world, 1)
    ```

#### Shuffle and Sort Phase:
- The MapReduce framework groups and sorts the intermediate key-value pairs by keys:

    ```
    (Hello, [1])
    (MapReduce, [1])
    (hello, [1])
    (world, [1, 1])
    ```

#### Reduce Phase:
- The `reduce` function processes these grouped pairs and calculates the total count for each word:

    ```
    (Hello, 1)
    (MapReduce, 1)
    (hello, 1)
    (world, 2)
    ```

This is a basic example of a MapReduce job for counting word occurrences in a text document. In a real-world scenario, the Map and Reduce functions would be more complex, and the framework would handle the distribution of tasks across a cluster of machines.
