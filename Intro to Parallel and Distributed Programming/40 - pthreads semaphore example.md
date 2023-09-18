Here's an example of using a semaphore in a pthreads program:

```c
#include <stdio.h>
#include <pthread.h>
#include <semaphore.h>

#define SIZE 10
#define NUM_THREADS 2

int sharedArray[SIZE];
sem_t semaphore;

void* threadFunction(void* arg) {
    int threadID = *(int*)arg;

    for (int i = 0; i < SIZE; i++) {
        // Wait on the semaphore
        sem_wait(&semaphore);

        // Critical section: Access shared resource (sharedArray)
        sharedArray[i] = threadID;

        // Release the semaphore
        sem_post(&semaphore);
    }

    pthread_exit(NULL);
}

int main() {
    pthread_t threads[NUM_THREADS];
    int threadIDs[NUM_THREADS];

    // Initialize semaphore
    sem_init(&semaphore, 0, 1); // Initial value of semaphore is 1

    for (int i = 0; i < NUM_THREADS; i++) {
        threadIDs[i] = i;
        pthread_create(&threads[i], NULL, threadFunction, (void*)&threadIDs[i]);
    }

    for (int i = 0; i < NUM_THREADS; i++) {
        pthread_join(threads[i], NULL);
    }

    // Display the shared array
    for (int i = 0; i < SIZE; i++) {
        printf("%d ", sharedArray[i]);
    }
    printf("\n");

    // Destroy semaphore
    sem_destroy(&semaphore);

    return 0;
}
```

In this example, we have an array `sharedArray` which is accessed by two threads. We use a semaphore `semaphore` to synchronize access to the critical section (array elements). The semaphore is initialized with an initial value of 1, allowing one thread to enter the critical section at a time.

The `threadFunction` is responsible for accessing and modifying the shared resource (`sharedArray`). It uses `sem_wait` to wait on the semaphore before entering the critical section, and `sem_post` to release the semaphore after leaving the critical section.

The `main` function creates two threads, each of which executes `threadFunction`. After the threads finish execution, the contents of `sharedArray` are displayed.

Please note that in this example, the output may vary because the order of execution of threads is not guaranteed. The critical section is protected by the semaphore, ensuring that only one thread can access it at a time.
