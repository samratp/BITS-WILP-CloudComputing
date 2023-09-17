Below is a simple C program that demonstrates process creation using the `fork()` system call:

```c
#include <stdio.h>
#include <unistd.h>

int main() {
    pid_t pid; // Variable to store the process ID

    // Fork a new process
    pid = fork();

    if (pid < 0) {
        fprintf(stderr, "Fork failed\n");
        return 1;
    } else if (pid == 0) {
        // This code is executed by the child process

        printf("Child process. PID: %d\n", getpid());
    } else {
        // This code is executed by the parent process

        printf("Parent process. Child PID: %d\n", pid);
    }

    return 0;
}
```

Here's what this program does:

1. It includes the necessary header files `stdio.h` for standard input/output functions and `unistd.h` for system calls.

2. It defines a variable `pid_t pid` to store the process ID.

3. In the `main()` function:
   - It calls `fork()` to create a new process. The return value of `fork()` is the PID of the child process in the parent process, and 0 in the child process.

   - If `fork()` fails, it prints an error message.

   - In the parent process, it prints the PID of the child process. In the child process, it prints a message indicating that it is the child process.

4. The program returns 0 to indicate successful execution.

When you compile and run this program, it will create a new process. The parent process will print the PID of the child process, and the child process will print its own PID. This demonstrates the creation of a new process using the `fork()` system call.
