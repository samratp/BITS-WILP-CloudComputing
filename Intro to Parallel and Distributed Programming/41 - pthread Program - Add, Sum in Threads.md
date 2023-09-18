Here's a pthread program in C that reads two numbers from the user and calculates their sum, difference, and product using separate threads:

```c
#include <stdio.h>
#include <pthread.h>

int num1, num2;
int sum, difference, product;

void* calculateSum(void* arg) {
    sum = num1 + num2;
    pthread_exit(NULL);
}

void* calculateDifference(void* arg) {
    difference = num1 - num2;
    pthread_exit(NULL);
}

void* calculateProduct(void* arg) {
    product = num1 * num2;
    pthread_exit(NULL);
}

int main() {
    pthread_t thread_sum, thread_difference, thread_product;

    printf("Enter two numbers: ");
    scanf("%d %d", &num1, &num2);

    pthread_create(&thread_sum, NULL, calculateSum, NULL);
    pthread_create(&thread_difference, NULL, calculateDifference, NULL);
    pthread_create(&thread_product, NULL, calculateProduct, NULL);

    pthread_join(thread_sum, NULL);
    pthread_join(thread_difference, NULL);
    pthread_join(thread_product, NULL);

    printf("Sum: %d\n", sum);
    printf("Difference: %d\n", difference);
    printf("Product: %d\n", product);

    return 0;
}
```

In this program:

1. Three separate threads (`thread_sum`, `thread_difference`, and `thread_product`) are created to calculate the sum, difference, and product, respectively.

2. The user is prompted to enter two numbers (`num1` and `num2`).

3. Each thread performs its respective calculation (`calculateSum`, `calculateDifference`, and `calculateProduct`).

4. The main thread waits for each of the three threads to finish their calculations using `pthread_join`.

5. Finally, the results (sum, difference, and product) are printed.

Compile and run this program, and it will prompt you to enter two numbers. It will then calculate and display the sum, difference, and product of those two numbers using separate threads.
