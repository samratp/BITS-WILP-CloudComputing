Below is an MPI program that converts a string to uppercase. Each process handles a portion of the string, and then the results are sent back to form the final uppercase string.



```c
#include <stdio.h>
#include <string.h>
#include <ctype.h>
#include <mpi.h>

int main(int argc, char *argv[]) {
    int rank, size;
    char str[100], local_str[100], final_str[100];

    MPI_Init(&argc, &argv);
    MPI_Comm_rank(MPI_COMM_WORLD, &rank);
    MPI_Comm_size(MPI_COMM_WORLD, &size);

    if (size < 2) {
        printf("This program requires at least two processes.\n");
        MPI_Finalize();
        return 1;
    }

    if (rank == 0) {
        printf("Enter a string: ");
        fflush(stdout);
        scanf("%[^\n]s", str);

        // Send the entire string to all processes
        for (int i = 1; i < size; i++) {
            MPI_Send(str, strlen(str)+1, MPI_CHAR, i, 0, MPI_COMM_WORLD);
        }
    } else {
        // Receive the entire string from process 0
        MPI_Recv(str, 100, MPI_CHAR, 0, 0, MPI_COMM_WORLD, MPI_STATUS_IGNORE);
    }

    // Calculate local portion of the string to convert to uppercase
    int chunk_size = strlen(str) / size;
    int start = rank * chunk_size;
    int end = (rank == size - 1) ? strlen(str) : start + chunk_size;
    strncpy(local_str, &str[start], end - start);
    local_str[end - start] = '\0';

    // Convert local portion of the string to uppercase
    for (int i = 0; i < strlen(local_str); i++) {
        local_str[i] = toupper(local_str[i]);
    }

    // Send back the converted portion to process 0
    if (rank != 0) {
        MPI_Send(local_str, strlen(local_str)+1, MPI_CHAR, 0, 0, MPI_COMM_WORLD);
    } else {
        // Copy local_str to final_str for process 0
        strcpy(final_str, local_str);

        // Receive the converted portions from other processes
        for (int i = 1; i < size; i++) {
            MPI_Recv(local_str, 100, MPI_CHAR, i, 0, MPI_COMM_WORLD, MPI_STATUS_IGNORE);
            strcat(final_str, local_str);
        }

        printf("Uppercase string: %s\n", final_str);
    }

    MPI_Finalize();
    return 0;
}
```

In this version, each process sends or receives the entire string as needed. Process 0 collects the converted portions from other processes and prints the final uppercase string.
