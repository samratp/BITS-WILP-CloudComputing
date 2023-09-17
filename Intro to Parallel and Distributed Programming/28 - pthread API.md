The `pthread` API (POSIX Threads) is a standardized interface for working with threads in a multi-threaded programming environment. It provides a set of functions and data types for creating, managing, synchronizing, and terminating threads. Here are some key functions provided by the `pthread` API:

1. **pthread_create**:
   - Function Signature: `int pthread_create(pthread_t *thread, const pthread_attr_t *attr, void *(*start_routine)(void*), void *arg)`
   - Creates a new thread and starts execution of a specified function (`start_routine`).
   - Parameters:
     - `thread`: Pointer to a `pthread_t` structure that will hold the ID of the created thread.
     - `attr`: Thread attributes (optional, can be `NULL` for default attributes).
     - `start_routine`: Function that will be executed by the thread.
     - `arg`: Argument passed to the `start_routine`.

2. **pthread_join**:
   - Function Signature: `int pthread_join(pthread_t thread, void **retval)`
   - Waits for the specified thread to finish execution.
   - Parameters:
     - `thread`: ID of the thread to wait for.
     - `retval`: Pointer to a location where the return value of the thread function will be stored.

3. **pthread_exit**:
   - Function Signature: `void pthread_exit(void *retval)`
   - Terminates the calling thread and returns a value to the parent process.

4. **pthread_cancel**:
   - Function Signature: `int pthread_cancel(pthread_t thread)`
   - Requests cancellation of a thread.

5. **pthread_mutex_init** and **pthread_mutex_destroy**:
   - Functions to initialize and destroy a mutex, respectively.

6. **pthread_mutex_lock** and **pthread_mutex_unlock**:
   - Functions to lock and unlock a mutex, respectively, for synchronizing access to shared resources.

7. **pthread_cond_init** and **pthread_cond_destroy**:
   - Functions to initialize and destroy a condition variable, respectively.

8. **pthread_cond_wait**, **pthread_cond_signal**, and **pthread_cond_broadcast**:
   - Functions for condition variable operations used for thread synchronization.

9. **pthread_attr_init** and **pthread_attr_destroy**:
   - Functions to initialize and destroy thread attributes.

10. **pthread_attr_setdetachstate**:
    - Function to set the detach state of a thread (detached or joinable).

11. **pthread_attr_getschedpolicy** and **pthread_attr_setschedpolicy**:
    - Functions for setting and getting the thread scheduling policy.

These are some of the most commonly used functions from the `pthread` API. There are additional functions available for more advanced thread management and synchronization. When using `pthread`, it's important to handle synchronization properly to avoid race conditions and deadlocks.
