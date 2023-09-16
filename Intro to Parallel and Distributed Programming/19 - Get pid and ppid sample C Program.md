Certainly! Below is a simple C program that retrieves and prints the Process ID (PID) and Parent Process ID (PPID):

```c
#include <stdio.h>
#include <unistd.h>

int main() {
    // Get the Process ID (PID)
    pid_t pid = getpid();
    
    // Get the Parent Process ID (PPID)
    pid_t ppid = getppid();
    
    // Print the PID and PPID
    printf("PID: %d\n", pid);
    printf("PPID: %d\n", ppid);
    
    return 0;
}
```

Here's what this program does:

1. It includes the necessary header files `stdio.h` for standard input/output functions and `unistd.h` for system calls.

2. In the `main()` function:
   - It uses `getpid()` to retrieve the current process's PID and assigns it to the variable `pid`.
   
   - It uses `getppid()` to retrieve the PID of the parent process (the process that created the current process) and assigns it to the variable `ppid`.
   
   - It then prints out the PID and PPID using `printf()`.

3. The program returns 0 to indicate successful execution.

When you compile and run this program, it will display the PID and PPID of the current process. Keep in mind that the PPID will be the PID of the process that executed this program (typically a shell or terminal).
