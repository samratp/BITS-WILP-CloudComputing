Here's a simple OpenMP program in C that calculates the sum of elements in an array using parallelization:

```c
#include <stdio.h>
#include <omp.h>

#define SIZE 1000

int main() {
    int arr[SIZE];
    int sum = 0;

    // Initialize the array with values
    for (int i = 0; i < SIZE; i++) {
        arr[i] = i + 1;
    }

    #pragma omp parallel for reduction(+:sum)
    for (int i = 0; i < SIZE; i++) {
        sum += arr[i];
    }

    printf("Sum of elements: %d\n", sum);

    return 0;
}
```

In this program, we're using OpenMP to parallelize the loop that calculates the sum of elements in the array. The `#pragma omp parallel for` directive instructs OpenMP to create a team of threads and distribute the loop iterations among them.

The `reduction(+:sum)` clause specifies that each thread will have its own private copy of `sum`, and at the end of the loop, these private copies will be combined using addition (`+`). The final result will be stored in the original `sum` variable.

To compile and run this program with OpenMP support, you'll need to use a compiler that supports OpenMP. For example, if you're using GCC, you can compile the program with the following command:

```
gcc -fopenmp openmp_example.c -o openmp_example
```

Then, you can run the program:

```
./openmp_example
```

You should see the sum of elements printed to the console. Keep in mind that the actual output may vary depending on the number of available CPU cores and the scheduling of threads by the operating system.
