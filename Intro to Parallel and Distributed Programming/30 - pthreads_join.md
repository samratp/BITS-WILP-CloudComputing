pThe `pthread_join` function is used to wait for a specific thread to finish its execution before proceeding with the rest of the program. It allows the calling thread to synchronize with the completion of another thread's execution. Here is the function signature:

```c
int pthread_join(pthread_t thread, void **retval);
```

- `thread`: The ID of the thread to wait for.
- `retval`: A pointer to a location where the return value of the thread function will be stored. This allows the thread to pass a value back to the calling thread.

**Return Value**:
- If successful, `pthread_join` returns 0.
- If an error occurs, it returns an error code.

**Usage**:

```c
#include <pthread.h>

void *thread_function(void *arg) {
    // Thread code
    return (void *)42; // Example return value
}

int main() {
    pthread_t thread;
    void *result;

    // Create and start the thread
    pthread_create(&thread, NULL, thread_function, NULL);

    // Wait for the thread to finish
    pthread_join(thread, &result);

    // Thread has finished, do something with the result
    int return_value = (int)result;

    return 0;
}
```

In this example:

1. We create a thread using `pthread_create` which starts executing `thread_function`.

2. In the `main` function, we use `pthread_join` to wait for the thread to finish.

3. The `&result` argument allows us to retrieve the return value from the thread.

4. Once `pthread_join` returns, we can use the value returned by the thread.

Keep in mind that `pthread_join` will block the calling thread until the specified thread completes its execution. If you don't need to wait for the thread to finish, you can simply let it run independently without calling `pthread_join`.
