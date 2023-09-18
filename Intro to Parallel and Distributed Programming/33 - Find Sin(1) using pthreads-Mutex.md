To find the value of `sin(1)` using pthreads, you can use the Taylor series expansion of `sin(x)`, which is:

```
sin(x) = x - (x^3/3!) + (x^5/5!) - (x^7/7!) + ...
```

Here's a C program that calculates `sin(1)` using multiple threads:

```c
#include <stdio.h>
#include <pthread.h>
#include <math.h>

#define TERMS 15

double result = 0.0;
pthread_mutex_t myMutex;

void* calculateSin(void* arg) {
    long term = (long)arg;
    double x = 1.0;
    double factorial = 1.0;

    for (long i = 2 * term + 1; i > 1; i--) {
        factorial *= i;
    }

    double contribution = pow(x, 2 * term + 1) / factorial;

    pthread_mutex_lock(&myMutex);
    result += term % 2 == 0 ? contribution : -contribution;
    pthread_mutex_unlock(&myMutex);

    return NULL;
}

int main() {
    pthread_t threads[TERMS];

    pthread_mutex_init(&myMutex, NULL);

    for (long i = 0; i < TERMS; i++) {
        pthread_create(&threads[i], NULL, calculateSin, (void*)i);
    }

    for (long i = 0; i < TERMS; i++) {
        pthread_join(threads[i], NULL);
    }

    pthread_mutex_destroy(&myMutex);

    printf("sin(1) is approximately %.10f\n", result);

    return 0;
}
```

In this program, we use multiple threads to calculate different terms of the Taylor series and then sum them up to get an approximation of `sin(1)`. Please note that this is just an approximation and may not be extremely accurate due to the finite number of terms used. The more terms you use, the more accurate the approximation will be.
