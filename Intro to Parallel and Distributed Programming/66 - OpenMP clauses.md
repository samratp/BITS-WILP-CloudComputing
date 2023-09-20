OpenMP clauses are used to provide additional information to the compiler about how to parallelize specific parts of the code. Here are some commonly used OpenMP clauses with examples:

1. **`private`**:
   - Specifies variables that should be private to each thread.

   ```c
   int x = 0;
   #pragma omp parallel private(x)
   {
       x = omp_get_thread_num();
       printf("Thread %d: x = %d\n", omp_get_thread_num(), x);
   }
   ```

2. **`shared`**:
   - Specifies variables that should be shared among all threads.

   ```c
   int x = 0;
   #pragma omp parallel shared(x)
   {
       x = omp_get_thread_num();
       printf("Thread %d: x = %d\n", omp_get_thread_num(), x);
   }
   ```

3. **`firstprivate`**:
   - Specifies variables that should be private to each thread, but initialized with the value from the master thread.

   ```c
   int x = 42;
   #pragma omp parallel firstprivate(x)
   {
       x += 1;
       printf("Thread %d: x = %d\n", omp_get_thread_num(), x);
   }
   ```

4. **`lastprivate`**:
   - Specifies variables whose value from the last iteration of a loop should be shared after the loop.

   ```c
   int x;
   #pragma omp parallel for lastprivate(x)
   for (int i = 0; i < n; i++) {
       x = i;
   }
   printf("After loop: x = %d\n", x);
   ```

5. **`reduction`**:
   - Performs a reduction operation on a variable, such as sum or product.

   ```c
   int sum = 0;
   #pragma omp parallel for reduction(+:sum)
   for (int i = 0; i < n; i++) {
       sum += i;
   }
   printf("Sum = %d\n", sum);
   ```

6. **`num_threads`**:
   - Specifies the number of threads to use for a parallel region.

   ```c
   #pragma omp parallel num_threads(4)
   {
       // Code executed by 4 threads
   }
   ```

7. **`schedule`**:
   - Specifies how loop iterations should be divided among threads.

   ```c
   #pragma omp parallel for schedule(static, 2)
   for (int i = 0; i < n; i++) {
       // ...
   }
   ```

8. **`nowait`**:
   - Indicates that threads do not need to wait for all iterations to complete before moving on.

   ```c
   #pragma omp parallel for nowait
   for (int i = 0; i < n; i++) {
       // ...
   }
   ```

9. **`collapse`**:
   - Allows collapsing nested loops into a single loop for parallelization.

   ```c
   #pragma omp parallel for collapse(2)
   for (int i = 0; i < m; i++) {
       for (int j = 0; j < n; j++) {
           // ...
       }
   }
   ```

10. **`ordered`**:
    - Specifies that the iterations of a loop should be executed in the order in which they would occur in a sequential execution.

    ```c
    #pragma omp parallel for ordered
    for (int i = 0; i < n; i++) {
        #pragma omp ordered
        {
            // Code executed in order
        }
    }
    ```

These are some of the commonly used OpenMP clauses. They allow you to control various aspects of parallel execution in your code. Depending on the nature of your program, you may choose to use one or more of these clauses to achieve the desired parallelism.
