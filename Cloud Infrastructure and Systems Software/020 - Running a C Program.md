Running a C program involves several stages, each transforming the code into an executable program. Here’s a breakdown of the stages involved:

### 1. **Preprocessing**
- **What Happens**: The preprocessor processes directives in the C code, such as `#include` and `#define`.
- **Output**: A modified source code file with all preprocessor directives resolved. For example, `#include <stdio.h>` will be replaced by the contents of the `stdio.h` header file.

**Command**: This stage is usually invoked automatically when you compile your code with `gcc`, but you can also run it explicitly:
```bash
gcc -E hello.c -o hello.i
```

### 2. **Compilation**
- **What Happens**: The compiler translates the preprocessed source code into assembly language.
- **Output**: An assembly code file (`.s`), which contains human-readable assembly instructions corresponding to the C code.

**Command**: You can generate the assembly file using:
```bash
gcc -S hello.i -o hello.s
```

### 3. **Assembly**
- **What Happens**: The assembler converts the assembly code into machine code (binary code).
- **Output**: An object file (`.o` or `.obj`), which contains machine code but is not yet a complete executable program.

**Command**: This stage is also usually performed automatically, but you can explicitly assemble the code:
```bash
gcc -c hello.s -o hello.o
```

### 4. **Linking**
- **What Happens**: The linker combines one or more object files (including libraries) into a single executable file. It resolves references between files and libraries, ensuring all function calls point to the correct locations.
- **Output**: An executable file (e.g., `a.out` or `hello.exe`).

**Command**: This stage is performed automatically when you compile:
```bash
gcc hello.o -o hello
```

### 5. **Loading**
- **What Happens**: The loader loads the executable file into memory, preparing it for execution. It sets up the program's environment, including memory allocation for code, data, and stack.
- **Output**: The program is ready to run in memory.

This stage is typically handled by the operating system when you execute the program.

### 6. **Execution**
- **What Happens**: The CPU executes the program instructions. The operating system manages the execution, handling input/output operations, managing memory, and responding to interrupts.
- **Output**: The program runs and produces output as defined by its code.

### Summary
The process of running a C program involves several stages: preprocessing, compilation, assembly, linking, loading, and execution. Each stage transforms the code, ultimately producing an executable program that the computer can run. Understanding these stages is crucial for debugging and optimizing C programs.
