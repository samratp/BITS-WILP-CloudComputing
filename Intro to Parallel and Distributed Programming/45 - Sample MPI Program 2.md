In this example, multiple sender processes will send messages to the rank 0 process, which will then print them.

```c
#include <stdio.h>
#include <mpi.h>

int main(int argc, char *argv[]) {
    int rank, size;
    char message[100];

    MPI_Init(&argc, &argv);
    MPI_Comm_rank(MPI_COMM_WORLD, &rank);
    MPI_Comm_size(MPI_COMM_WORLD, &size);

    if (rank != 0) {
        // If not rank 0, send a message to rank 0
        sprintf(message, "Hello from process %d!", rank);
        MPI_Send(message, strlen(message)+1, MPI_CHAR, 0, 0, MPI_COMM_WORLD);
    } else {
        // If rank 0, receive messages from other processes
        for (int i = 1; i < size; i++) {
            MPI_Recv(message, 100, MPI_CHAR, i, 0, MPI_COMM_WORLD, MPI_STATUS_IGNORE);
            printf("%s\n", message);
        }
    }

    MPI_Finalize();

    return 0;
}
```

Explanation:

1. All processes (including rank 0) are involved in this program.

2. If the process is not rank 0, it sends a message to rank 0 using `MPI_Send`.

3. If the process is rank 0, it enters a loop to receive messages from other processes. It uses `MPI_Recv` to receive the messages.

4. The received messages are then printed.

5. Finally, MPI is finalized with `MPI_Finalize`.

Compile and run this program as before:

```bash
mpicc mpi_example.c -o mpi_example
mpirun -n 4 ./mpi_example
```

In this program, all processes (including rank 0) participate in sending and receiving messages. The rank 0 process acts as a receiver and prints the messages sent by the other processes.
