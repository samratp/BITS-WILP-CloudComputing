Below is an MPI program that converts a string to uppercase. Each process handles a portion of the string, and then the results are gathered to form the final uppercase string.

```c
#include <stdio.h>
#include <string.h>
#include <ctype.h>
#include <mpi.h>

int main(int argc, char *argv[]) {
    int rank, size;
    char str[100], local_str[100];

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
    }

    // Broadcast the string from rank 0 to all processes
    MPI_Bcast(str, 100, MPI_CHAR, 0, MPI_COMM_WORLD);

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

    // Gather the results back to rank 0
    MPI_Gather(local_str, strlen(local_str), MPI_CHAR, str, strlen(local_str), MPI_CHAR, 0, MPI_COMM_WORLD);

    if (rank == 0) {
        printf("Uppercase string: %s\n", str);
    }

    MPI_Finalize();
    return 0;
}
```

In this program, each process receives a portion of the string and converts it to uppercase. The results are then gathered back to rank 0, where the final uppercase string is printed.
