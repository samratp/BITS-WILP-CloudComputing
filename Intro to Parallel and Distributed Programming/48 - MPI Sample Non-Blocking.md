Here's the simplified MPI program with a non-blocking send from rank 1 to rank 0:

```c
#include <stdio.h>
#include <mpi.h>

int main(int argc, char *argv[]) {
    int rank, size;
    int send_buf, recv_buf;
    MPI_Status status;
    MPI_Request send_req, recv_req;

    MPI_Init(&argc, &argv);
    MPI_Comm_rank(MPI_COMM_WORLD, &rank);
    MPI_Comm_size(MPI_COMM_WORLD, &size);

    if (size < 2) {
        printf("This program requires at least two processes.\n");
        MPI_Finalize();
        return 1;
    }

    if (rank == 0) {
        MPI_Irecv(&recv_buf, 1, MPI_INT, 1, 0, MPI_COMM_WORLD, &recv_req);

        // Continue with other work while communication proceeds in the background.
        // ...

        // Wait for the non-blocking receive operation to complete.
        MPI_Wait(&recv_req, &status);

        printf("Process 0 received %d from process 1.\n", recv_buf);
    } else if (rank == 1) {
        send_buf = 100;
        MPI_Isend(&send_buf, 1, MPI_INT, 0, 0, MPI_COMM_WORLD, &send_req);

        // Continue with other work while communication proceeds in the background.
        // ...

        // Wait for the non-blocking send operation to complete.
        MPI_Wait(&send_req, &status);
    }

    MPI_Finalize();
    return 0;
}
```

In this program, rank 1 sends an integer (`send_buf`) to rank 0 using a non-blocking send operation (`MPI_Isend`). Rank 0 initiates a non-blocking receive operation (`MPI_Irecv`) to receive the integer from rank 1. Both processes then continue with their work, and each waits for their respective non-blocking operation to complete before printing the result.
