Below is a C program that prompts the user to enter the number of threads they want to create. Each thread will then print a "Hello from Thread" message along with its ID.

```c
#include <stdio.h>
#include <pthread.h>
#include <stdlib.h> // Added for atoi

void *thread_func(void *arg) {
    int thread_id = *((int *)arg);
    printf("Thread %d: Hello from Thread %d!\n", thread_id, thread_id);
    return NULL;
}

int main() {
    int num_threads;

    printf("Enter the number of threads to create: ");
    scanf("%d", &num_threads);

    if (num_threads <= 0) {
        fprintf(stderr, "Invalid number of threads. Please provide a positive integer.\n");
        return 1;
    }

    pthread_t threads[num_threads];

    for (int i = 0; i < num_threads; i++) {
        if (pthread_create(&threads[i], NULL, thread_func, (void *)&i) != 0) {
            fprintf(stderr, "Error creating thread %d\n", i);
            return 1;
        }
    }

    for (int i = 0; i < num_threads; i++) {
        pthread_join(threads[i], NULL);
    }

    return 0;
}
```

Explanation:

1. We include the necessary headers for using threads (`stdio.h`, `pthread.h`, and `stdlib.h`).

2. We define a function `thread_func` that takes an integer argument representing the thread ID. This function prints a message indicating the thread's ID.

3. In `main`, we prompt the user to enter the number of threads they want to create using `printf` and `scanf`.

4. We check if the provided number of threads is a positive integer. If not, we display an error message and exit.

5. We then create the specified number of threads using a loop. Each thread is assigned a unique thread ID.

6. Each thread executes the `thread_func` and prints its thread ID along with a message.

7. Finally, the main program waits for all threads to finish using `pthread_join`.

When you run this program, it will ask you for the number of threads you want to create, and then it will create and execute those threads.
