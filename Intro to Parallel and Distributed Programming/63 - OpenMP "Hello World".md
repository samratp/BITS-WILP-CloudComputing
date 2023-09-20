Here's a simple OpenMP "Hello World" program that includes the thread number:

```c
#include <stdio.h>
#include <omp.h>

int main() {
    #pragma omp parallel
    {
        int thread_id = omp_get_thread_num();
        int num_threads = omp_get_num_threads();
        printf("Hello World - Thread %d of %d\n", thread_id, num_threads);
    }

    return 0;
}
```

In this program, we use OpenMP's `parallel` directive to create a team of threads. Within the parallel region, each thread retrieves its own thread number using `omp_get_thread_num()` and the total number of threads in the team using `omp_get_num_threads()`. These values are then used to print out a "Hello World" message that includes the thread's ID and the total number of threads.

Compile and run this program using an OpenMP-enabled compiler, similar to the previous example. When you run it, you should see output lines like:

```
Hello World - Thread 1 of 4
Hello World - Thread 2 of 4
Hello World - Thread 0 of 4
Hello World - Thread 3 of 4
```

The exact output may vary depending on the number of available CPU cores and the scheduling of threads by the operating system.
