### TCP Echo Server

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <arpa/inet.h>
#include <unistd.h>

#define PORT 8080

int main() {
    int server_fd, new_socket;
    struct sockaddr_in address;
    int addrlen = sizeof(address);
    char buffer[1024] = {0};

    // Creating socket file descriptor
    if ((server_fd = socket(AF_INET, SOCK_STREAM, 0)) == 0) {
        perror("socket failed");
        exit(EXIT_FAILURE);
    }

    address.sin_family = AF_INET;
    address.sin_addr.s_addr = INADDR_ANY;
    address.sin_port = htons(PORT);

    if (bind(server_fd, (struct sockaddr *)&address, sizeof(address)) < 0) {
        perror("bind failed");
        exit(EXIT_FAILURE);
    }

    if (listen(server_fd, 3) < 0) {
        perror("listen");
        exit(EXIT_FAILURE);
    }

    if ((new_socket = accept(server_fd, (struct sockaddr *)&address, (socklen_t*)&addrlen)) < 0) {
        perror("accept");
        exit(EXIT_FAILURE);
    }

    int valread;

    while(1) {
        valread = read(new_socket, buffer, 1024);
        send(new_socket, buffer, strlen(buffer), 0);
        memset(buffer, 0, sizeof(buffer));
    }

    return 0;
}
```

#### Explanation:

1. **Include Libraries**: Include necessary C libraries for socket programming.

2. **Define Port Number**: Define a constant `PORT` to specify the port on which the server will listen for connections.

3. **Main Function**: Start of the program.

4. **Socket Creation**:
   - `server_fd`: File descriptor for the server socket.
   - `socket()`: Creates a socket. AF_INET specifies IPv4, SOCK_STREAM specifies TCP.

5. **Initialize Address Structure**:
   - `address`: Structure to hold server address information.
   - `INADDR_ANY`: Binds to all available interfaces.

6. **Bind Socket to Address**:
   - `bind()`: Binds the socket to the specified address and port.

7. **Listen for Incoming Connections**:
   - `listen()`: Listens for incoming connections with a maximum queue size of 3.

8. **Accept a New Connection**:
   - `accept()`: Accepts a new incoming connection.

9. **Receive and Echo Messages**:
   - `read()`: Receives data from the client.
   - `send()`: Sends data back to the client.
   - The server runs in an infinite loop, continuously receiving and echoing messages.

### TCP Echo Client

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <arpa/inet.h>
#include <unistd.h>

#define PORT 8080

int main(int argc, char const *argv[]) {
    struct sockaddr_in address;
    int sock = 0, valread;
    struct sockaddr_in serv_addr;
    char *hello = "Hello from client";
    char buffer[1024] = {0};

    if ((sock = socket(AF_INET, SOCK_STREAM, 0)) < 0) {
        printf("\n Socket creation error \n");
        return -1;
    }

    memset(&serv_addr, '0', sizeof(serv_addr));
    serv_addr.sin_family = AF_INET;
    serv_addr.sin_port = htons(PORT);

    if(inet_pton(AF_INET, "127.0.0.1", &serv_addr.sin_addr)<=0) {
        printf("\nInvalid address/ Address not supported \n");
        return -1;
    }

    if (connect(sock, (struct sockaddr *)&serv_addr, sizeof(serv_addr)) < 0) {
        printf("\nConnection Failed \n");
        return -1;
    }

    while(1) {
        printf("Enter message : ");
        fgets(buffer, sizeof(buffer), stdin);
        send(sock , buffer , strlen(buffer) , 0 );
        valread = read(sock , buffer, 1024);
        printf("%s\n",buffer );
        memset(buffer, 0, sizeof(buffer));
    }

    return 0;
}
```

#### Explanation:

1. **Include Libraries**: Include necessary C libraries for socket programming.

2. **Define Port Number**: Define a constant `PORT` to specify the port on which the server is running.

3. **Main Function**: Start of the program.

4. **Socket Creation**:
   - `sock`: File descriptor for the client socket.
   - `socket()`: Creates a socket. AF_INET specifies IPv4, SOCK_STREAM specifies TCP.

5. **Initialize Server Address**:
   - `serv_addr`: Structure to hold server address information.
   - `memset()`: Fills `serv_addr` with zeros.

6. **Convert IPv

4 Address**:
   - `inet_pton()`: Converts IP address from text to binary form.

7. **Connect to Server**:
   - `connect()`: Establishes a connection to the server.

8. **Send and Receive Messages**:
   - `send()`: Sends data to the server.
   - `read()`: Receives data from the server.
   - The client runs in an infinite loop, continuously sending and receiving messages.

Remember to compile and run the server and client separately in different terminal windows. The server should be running before the client connects.
