```c
#include <stdio.h>
#include <pthread.h>

#define ROWS 2
#define COLS 2
#define NUM_THREADS 2

int inCriticalSection = -1; // -1 means no thread is in critical section

int A[ROWS][COLS] = {{1,1}, {1,1}};
int B[COLS][ROWS] = {{1,1}, {1,1}};
int C[ROWS][ROWS];

void* calculateRow(void* arg) {
    long row = (long)arg;

    for (int j = 0; j < ROWS; j++) {
        int localSum = 0;
        for (int k = 0; k < COLS; k++) {
            localSum += A[row][k] * B[k][j];
        }

        while (inCriticalSection != -1); // Busy-wait until critical section is available
        inCriticalSection = (int)row;
        C[row][j] = localSum;
        inCriticalSection = -1; // Release critical section
    }

    return NULL;
}

int main() {
    pthread_t threads[NUM_THREADS];

    for (long i = 0; i < NUM_THREADS; i++) {
        pthread_create(&threads[i], NULL, calculateRow, (void*)i);
    }

    for (long i = 0; i < NUM_THREADS; i++) {
        pthread_join(threads[i], NULL);
    }

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
