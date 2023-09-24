Locality of reference is a fundamental principle in computer science and refers to the tendency of a program to access the same set of memory locations frequently over a short period of time. There are two main types of locality:

1. **Temporal Locality:**
   - Temporal locality occurs when the same data is accessed multiple times over a short period of time.
   - Example: In a loop, if a variable `x` is accessed in each iteration, it exhibits temporal locality.

2. **Spatial Locality:**
   - Spatial locality occurs when data located near the current accessed data is also accessed in the near future.
   - Example: When accessing elements in an array, if `array[i]` is accessed, there's a good chance that `array[i+1]` will be accessed soon after, exhibiting spatial locality.

Here are some examples to illustrate these concepts:

### Temporal Locality:

**Example 1:**
```python
# Python code snippet
for i in range(1000):
    x = calculate_value(i)  # Accessing the same variable 'x' in each iteration
```

**Example 2:**
```C
// C code snippet
int factorial(int n) {
    if (n == 0 || n == 1) {
        return 1;  // Accessing the same code block frequently
    } else {
        return n * factorial(n - 1);
    }
}
```

### Spatial Locality:

**Example 1:**
```C
// C code snippet
int array[1000];
int sum = 0;
for (int i = 0; i < 1000; i++) {
    sum += array[i];  // Accessing elements in an array sequentially
}
```

**Example 2:**
```C
// C code snippet
struct Point {
    int x, y;
};

struct Point points[1000];
int sum = 0;
for (int i = 0; i < 1000; i++) {
    sum += points[i].x;  // Accessing struct members sequentially
}
```

Understanding and leveraging locality of reference is crucial for optimizing the performance of programs and data structures. It allows for the effective use of caches and can lead to significant improvements in execution speed. This principle is applied extensively in the design of algorithms, data structures, and computer architectures.
