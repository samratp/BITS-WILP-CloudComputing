### Sum of an Array

```c
#include <stdio.h>
#include <pthread.h>

#define ARRAY_SIZE 10
#define NUM_THREADS 5

int arr[ARRAY_SIZE] = {1,2,3,4,5,6,7,8,9,10};
int sum = 0;
pthread_mutex_t myMutex;

void* calculateSum(void* arg) {
    long start = (long)arg * (ARRAY_SIZE / NUM_THREADS);
    long end = start + (ARRAY_SIZE / NUM_THREADS);
    int localSum = 0;

    for (long i = start; i < end; i++) {
        localSum += arr[i];
    }

    pthread_mutex_lock(&myMutex);
    sum += localSum;
    pthread_mutex_unlock(&myMutex);

    return NULL;
}

int main() {
    pthread_t threads[NUM_THREADS];

    pthread_mutex_init(&myMutex, NULL);

    for (long i = 0; i < NUM_THREADS; i++) {
        pthread_create(&threads[i], NULL, calculateSum, (void*)i);
    }

    for (long i = 0; i < NUM_THREADS; i++) {
        pthread_join(threads[i], NULL);
    }

    pthread_mutex_destroy(&myMutex);

    printf("Sum of the array is %d\n", sum);

    return 0;
}
```
