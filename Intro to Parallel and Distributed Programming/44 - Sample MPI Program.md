Here's a simple MPI program in C that demonstrates the use of MPI for sending a message from one process to another:

```c
#include <stdio.h>
#include <mpi.h>

int main(int argc, char *argv[]) {
    int rank, size;
    char message[100];

    // Initialize MPI
    MPI_Init(&argc, &argv);

    // Get the rank (process ID)
    MPI_Comm_rank(MPI_COMM_WORLD, &rank);

    // Get the total number of processes
    MPI_Comm_size(MPI_COMM_WORLD, &size);

    if (rank == 0) {
        // Process 0 sends a message to process 1
        sprintf(message, "Hello from process %d!", rank);
        MPI_Send(message, strlen(message)+1, MPI_CHAR, 1, 0, MPI_COMM_WORLD);
    } else if (rank == 1) {
        // Process 1 receives the message from process 0
        MPI_Recv(message, 100, MPI_CHAR, 0, 0, MPI_COMM_WORLD, MPI_STATUS_IGNORE);
        printf("Received message: %s\n", message);
    }

    // Finalize MPI
    MPI_Finalize();

    return 0;
}
```

Explanation:

1. The program includes the necessary header files for MPI.

2. `MPI_Init(&argc, &argv)` initializes MPI.

3. `MPI_Comm_rank(MPI_COMM_WORLD, &rank)` retrieves the rank (process ID) of the current process.

4. `MPI_Comm_size(MPI_COMM_WORLD, &size)` retrieves the total number of processes.

5. In process with rank 0, a message is formatted and sent to process with rank 1 using `MPI_Send`.

6. In process with rank 1, a message is received from process with rank 0 using `MPI_Recv`.

7. The received message is printed.

8. `MPI_Finalize()` finalizes MPI before the program exits.

To compile and run this program, you would typically use an MPI compiler wrapper like `mpicc`. For example:

```
mpicc mpi_example.c -o mpi_example
mpirun -n 2 ./mpi_example
```

This program demonstrates basic message passing between two processes. Process 0 sends a message to process 1 using MPI_Send, and process 1 receives the message using MPI_Recv.
