
### Matrix Multiplication

```c
#include <stdio.h>
#include <pthread.h>

#define ROWS 2
#define COLS 2
#define NUM_THREADS 2

int A[ROWS][COLS] = {{1,1}, {1,1}};
int B[COLS][ROWS] = {{1,1}, {1,1}};
int C[ROWS][ROWS];
pthread_mutex_t myMutex;

void* calculateRow(void* arg) {
    long row = (long)arg;

    for (int j = 0; j < ROWS; j++) {
        int localSum = 0;
        for (int k = 0; k < COLS; k++) {
            localSum += A[row][k] * B[k][j];
        }

        pthread_mutex_lock(&myMutex);
        C[row][j] = localSum;
        pthread_mutex_unlock(&myMutex);
    }

    return NULL;
}

int main() {
    pthread_t threads[NUM_THREADS];

    pthread_mutex_init(&myMutex, NULL);

    for (long i = 0; i < NUM_THREADS; i++) {
        pthread_create(&threads[i], NULL, calculateRow, (void*)i);
    }

    for (long i = 0; i < NUM_THREADS; i++) {
        pthread_join(threads[i], NULL);
    }

    pthread_mutex_destroy(&myMutex);

    printf("Resultant Matrix C:\n");
    for (int i = 0; i < ROWS; i++) {
        for (int j = 0; j < ROWS; j++) {
            printf("%d ", C[i][j]);
        }
        printf("\n");
    }

    return 0;
}
```
