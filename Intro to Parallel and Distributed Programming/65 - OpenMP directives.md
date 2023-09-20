Here is a list of commonly used OpenMP directives along with examples:

1. **`#pragma omp parallel`**:
   - Creates a team of threads to execute the enclosed code in parallel.
   
   ```c
   #pragma omp parallel
   {
       // Code executed in parallel by multiple threads
   }
   ```

2. **`#pragma omp for`**:
   - Distributes loop iterations among available threads.
   
   ```c
   #pragma omp parallel
   {
       #pragma omp for
       for (int i = 0; i < n; i++) {
           // Code inside the loop is executed in parallel by multiple threads.
       }
   }
   ```

3. **`#pragma omp sections`**:
   - Divides the enclosed code into sections that can be executed in parallel by different threads.
   
   ```c
   #pragma omp parallel
   {
       #pragma omp sections
       {
           #pragma omp section
           {
               // Code for section 1
           }
           #pragma omp section
           {
               // Code for section 2
           }
       }
   }
   ```

4. **`#pragma omp single`**:
   - Specifies that the enclosed code should be executed by only one thread.
   
   ```c
   #pragma omp parallel
   {
       #pragma omp single
       {
           // Code inside here will be executed by only one thread.
       }
   }
   ```

5. **`#pragma omp task`**:
   - Creates a task that can be executed by any available thread.
   
   ```c
   #pragma omp parallel
   {
       #pragma omp single
       {
           #pragma omp task
           {
               // Code for the task
           }
       }
   }
   ```

6. **`#pragma omp critical`**:
   - Specifies a critical section, which can be accessed by only one thread at a time.
   
   ```c
   #pragma omp parallel
   {
       #pragma omp critical
       {
           // Code inside this critical section is executed by only one thread at a time.
       }
   }
   ```

7. **`#pragma omp barrier`**:
   - Synchronizes the threads, ensuring that no thread proceeds beyond the barrier until all threads have arrived.
   
   ```c
   #pragma omp parallel
   {
       // Code before barrier
       #pragma omp barrier
       // Code after barrier
   }
   ```

8. **`#pragma omp master`**:
   - Specifies that the enclosed code should be executed only by the master thread.
   
   ```c
   #pragma omp parallel
   {
       #pragma omp master
       {
           // Code executed only by the master thread
       }
   }
   ```

9. **`#pragma omp ordered`**:
   - Specifies a structured block in which the iterations of a loop must be executed in the order in which they would occur in a sequential execution.
   
   ```c
   #pragma omp parallel for ordered
   for (int i = 0; i < n; i++) {
       #pragma omp ordered
       {
           // Code executed in order
       }
   }
   ```

10. **`#pragma omp atomic`**:
    - Provides a mechanism for performing atomic operations on shared variables.
    
    ```c
    #pragma omp parallel
    {
        #pragma omp atomic
        x++;
    }
    ```

11. **`#pragma omp threadprivate`**:
    - Declares variables that are private to each thread.
    
    ```c
    #pragma omp threadprivate(x)
    int x = 0;
    ```

12. **`#pragma omp flush`**:
    - Synchronizes memory between threads.
    
    ```c
    #pragma omp parallel
    {
        // Code executed by multiple threads
        #pragma omp flush
        // Synchronize memory
    }
    ```

These are some of the commonly used OpenMP directives. Each directive serves a specific purpose and can be used to parallelize different parts of your code. Depending on the nature of your program, you may choose to use one or more of these directives to achieve parallelism.
