Here's a pthread program in C to convert a string of 20 characters from lowercase to uppercase using multiple threads:

```c
#include <stdio.h>
#include <stdlib.h>
#include <pthread.h>
#include <ctype.h>

#define STR_LENGTH 20
#define NUM_THREADS 4

char inputStr[STR_LENGTH];
char outputStr[STR_LENGTH];
pthread_mutex_t mutex = PTHREAD_MUTEX_INITIALIZER;

void* convertToUpper(void* arg) {
    int threadID = *(int*)arg;
    int startIndex = threadID * (STR_LENGTH / NUM_THREADS);
    int endIndex = startIndex + (STR_LENGTH / NUM_THREADS);

    for (int i = startIndex; i < endIndex; i++) {
        if (islower(inputStr[i])) {
            pthread_mutex_lock(&mutex);
            outputStr[i] = toupper(inputStr[i]);
            pthread_mutex_unlock(&mutex);
        } else {
            outputStr[i] = inputStr[i];
        }
    }

    pthread_exit(NULL);
}

int main() {
    pthread_t threads[NUM_THREADS];
    int threadIDs[NUM_THREADS];

    printf("Enter a string of 20 characters (lowercase): ");
    fgets(inputStr, sizeof(inputStr), stdin);

    for (int i = 0; i < NUM_THREADS; i++) {
        threadIDs[i] = i;
        pthread_create(&threads[i], NULL, convertToUpper, (void*)&threadIDs[i]);
    }

    for (int i = 0; i < NUM_THREADS; i++) {
        pthread_join(threads[i], NULL);
    }

    printf("Converted string (uppercase):\n%s\n", outputStr);

    return 0;
}
```

In this program:

1. We define `STR_LENGTH` as 20 to specify the length of the input string.

2. `NUM_THREADS` is set to 4 to perform the conversion using 4 threads.

3. The `convertToUpper` function is responsible for converting a portion of the input string to uppercase. Each thread processes a segment of the input string.

4. In the `main` function, the user is prompted to enter a string of 20 characters in lowercase.

5. Four threads are created, each running the `convertToUpper` function.

6. After all threads have finished, the converted string (in uppercase) is printed.

This program converts the user-input lowercase string to uppercase using multiple threads while ensuring thread-safe access to the shared `outputStr` using a mutex.
