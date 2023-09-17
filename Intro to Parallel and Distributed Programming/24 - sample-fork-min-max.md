In this example, the parent process will call a `max()` function to find the maximum value in an array, while the child process will call a `min()` function to find the minimum value in the same array.

```c
#include <stdio.h>
#include <unistd.h>

int max(int arr[], int size) {
    int max_val = arr[0];
    for (int i = 1; i < size; i++) {
        if (arr[i] > max_val) {
            max_val = arr[i];
        }
    }
    return max_val;
}

int min(int arr[], int size) {
    int min_val = arr[0];
    for (int i = 1; i < size; i++) {
        if (arr[i] < min_val) {
            min_val = arr[i];
        }
    }
    return min_val;
}

int main() {
    pid_t pid;
    int numbers[] = {3, 1, 4, 1, 5, 9, 2, 6, 5, 3, 5};
    int num_count = sizeof(numbers) / sizeof(numbers[0]);

    pid = fork();

    if (pid < 0) {
        fprintf(stderr, "Fork failed\n");
        return 1;
    } else if (pid == 0) {
        // This code is executed by the child process

        int min_val = min(numbers, num_count);
        printf("Child process. Minimum value: %d\n", min_val);
    } else {
        // This code is executed by the parent process

        int max_val = max(numbers, num_count);
        printf("Parent process. Maximum value: %d\n", max_val);
    }

    return 0;
}
```

In this example:

1. We define two functions `max()` and `min()` to find the maximum and minimum values in an array, respectively.

2. The parent process calls `max()` to find the maximum value.

3. The child process calls `min()` to find the minimum value.

Both processes execute their respective tasks independently. When you run this program, you'll see the output from both the parent and child processes showing the maximum and minimum values, respectively.
