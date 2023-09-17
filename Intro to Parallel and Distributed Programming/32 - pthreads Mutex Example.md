Certainly! Here's a simple example demonstrating the use of a mutex to protect a critical section of code:

```c
#include <stdio.h>
#include <pthread.h>

// Global shared variable
int sharedVariable = 0;

// Mutex declaration
pthread_mutex_t myMutex;

void* threadFunction(void* arg) {
    for (int i = 0; i < 5; i++) {
        // Acquire the lock
        pthread_mutex_lock(&myMutex);

        // Critical section (protected resource)
        sharedVariable++;
        printf("Thread %ld: Incremented sharedVariable to %d\n", (long)arg, sharedVariable);

        // Release the lock
        pthread_mutex_unlock(&myMutex);

        // Simulate some work
        usleep(100000); // Sleep for 100ms
    }

    return NULL;
}

int main() {
    pthread_t thread1, thread2;

    // Initialize the mutex
    pthread_mutex_init(&myMutex, NULL);

    // Create threads
    pthread_create(&thread1, NULL, threadFunction, (void*)1);
    pthread_create(&thread2, NULL, threadFunction, (void*)2);

    // Wait for threads to finish
    pthread_join(thread1, NULL);
    pthread_join(thread2, NULL);

    // Destroy the mutex
    pthread_mutex_destroy(&myMutex);

    return 0;
}
```

In this example, we have two threads (`thread1` and `thread2`) that increment a shared variable (`sharedVariable`) in a critical section. The critical section is protected by a mutex (`myMutex`) to ensure that only one thread can access it at a time.

Here's what the program does:

1. Both threads are created and start executing the `threadFunction`.
2. In `threadFunction`, each thread acquires the lock using `pthread_mutex_lock`, performs the critical section operation (incrementing `sharedVariable`), and then releases the lock using `pthread_mutex_unlock`.
3. The program simulates some work using `usleep` to show that other threads can execute while one thread holds the lock.
4. After both threads finish, the program joins them, ensuring they complete their execution before the program terminates.

Compile and run this program, and you should see output demonstrating that the shared variable is safely incremented by both threads.
