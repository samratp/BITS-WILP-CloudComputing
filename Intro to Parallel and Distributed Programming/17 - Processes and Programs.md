Processes and programs are fundamental concepts in computer science and operating systems. They are closely related but distinct entities. Here's a breakdown of what they are:

### Program:

1. **Definition**:
   - A program is a set of instructions written in a programming language that can be executed by a computer.

2. **Stored Entity**:
   - It exists as a file on a storage medium (like a hard drive or flash memory) and is inert until it is loaded into memory for execution.

3. **Passive State**:
   - A program is in a passive state. It is a static entity that doesn't perform any actions on its own.

4. **Does Not Consume System Resources**:
   - When a program is not running, it doesn't consume any system resources (like CPU cycles or memory).

5. **Example**:
   - An executable file (e.g., a .exe file in Windows or a binary executable in Linux) is an example of a program.

### Process:

1. **Definition**:
   - A process is a running instance of a program in execution. It is the active state of a program.

2. **Dynamic Entity**:
   - A process is dynamic and can perform actions. It interacts with the system's resources, such as CPU, memory, files, and I/O devices.

3. **Consumes System Resources**:
   - When a process is running, it consumes system resources, including CPU time, memory, and other resources.

4. **Has Its Own Memory Space**:
   - Each process has its own memory space. It cannot directly access the memory of other processes.

5. **Can Interact with Other Processes**:
   - Processes can communicate and interact with each other through mechanisms like inter-process communication (IPC).

6. **Can Spawn Child Processes**:
   - A process can create new processes, known as child processes, which can run concurrently with the parent process.

7. **Can Be Multithreaded**:
   - A process can have multiple threads of execution, allowing for concurrent execution within the process.

8. **Managed by the Operating System**:
   - Processes are managed and scheduled by the operating system's process scheduler.

9. **Example**:
   - When you open a web browser, it creates a process that represents the running instance of the browser application.

### Relationship:

- A program becomes a process when it is loaded into memory and executed by the computer's processor.

- Multiple processes can be spawned from a single program. Each process will have its own execution state, memory space, and system resources.

- Processes allow for concurrent execution of different tasks on a computer system.

In summary, a program is a static set of instructions, while a process is a dynamic instance of a program in execution. Processes are the entities that actually do the work on a computer system, interacting with resources and executing instructions.
