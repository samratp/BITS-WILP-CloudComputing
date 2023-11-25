Causal consistency ensures that there is a causal relationship between operations. Here are the key properties:

1. **Read Your Writes (RYW):**
   - Any write operation performed by a process will be visible in all subsequent read operations by that same process.

2. **Monotonic Reads and Writes:**
   - If a process reads the value of a variable, it should not later read an earlier value of that same variable.
   - If a process writes a value, all subsequent writes by that process must be to values greater than or equal to the one it wrote.

3. **Write Follows Reads:**
   - If a process reads a value, any write it performs later will be based on the value it read.

### Example:

Let's consider two processes, A and B, and two variables, `counter` and `total`.

1. **Read Your Writes:**

```javascript
// Process A
await collection.updateOne({ _id: "counter" }, { $inc: { value: 1 } });
const resultA = await collection.findOne({ _id: "counter" });
console.log("Process A Counter:", resultA.value); // Output: Process A Counter: 1

// Process B
const resultB = await collection.findOne({ _id: "counter" });
console.log("Process B Counter:", resultB.value); // Output: Process B Counter: 1
```

In this case, both processes read the updated value of `counter` after their respective writes.

2. **Monotonic Reads and Writes:**

```javascript
// Process A
const resultA1 = await collection.findOne({ _id: "total" });
console.log("Process A Total 1:", resultA1.value); // Output: Process A Total 1: 0
await collection.updateOne({ _id: "total" }, { $inc: { value: 5 } });

// Process B
const resultB = await collection.findOne({ _id: "total" });
console.log("Process B Total:", resultB.value);   // Output: Process B Total: 5
await collection.updateOne({ _id: "total" }, { $inc: { value: 3 } });

// Process A
const resultA2 = await collection.findOne({ _id: "total" });
console.log("Process A Total 2:", resultA2.value); // Output: Process A Total 2: 8
```

In this case, the writes are monotonic, and each process reads a value greater than or equal to the previous value it wrote.

3. **Write Follows Reads:**

```javascript
// Process A
const resultA = await collection.findOne({ _id: "counter" });
await collection.updateOne({ _id: "total" }, { $inc: { value: resultA.value } });

// Process B
await collection.updateOne({ _id: "counter" }, { $inc: { value: 2 } });
const resultB = await collection.findOne({ _id: "total" });
console.log("Process B Total:", resultB.value);   // Output: Process B Total: 3
```

In this case, the write to `total` by Process B follows the read of the `counter` value by Process A.

Causal consistency ensures that these properties hold, maintaining a logical and causal relationship between operations across processes.
