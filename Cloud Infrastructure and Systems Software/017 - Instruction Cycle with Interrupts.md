The instruction cycle with interrupts involves additional steps to manage interrupt requests while executing instructions. Here's an overview of how the instruction cycle is modified when interrupts are present:

### 1. **Basic Instruction Cycle Phases**
The basic instruction cycle consists of three main phases: **Fetch**, **Decode**, and **Execute**. Here’s how each phase interacts with interrupts:

### 2. **Fetch Phase**
- **Standard Process**:
  - The CPU retrieves the next instruction from memory using the Program Counter (PC).
  - The instruction is stored in the Instruction Register (IR).

- **Interrupt Handling**:
  - During this phase, the CPU checks for any pending interrupts. This can occur after fetching an instruction or at specific intervals (e.g., after every instruction).
  - If an interrupt is detected, the CPU will save the state of the current instruction (e.g., PC, registers) before handling the interrupt.

### 3. **Decode Phase**
- **Standard Process**:
  - The Control Unit decodes the instruction in the IR to determine the operation to be performed.

- **Interrupt Handling**:
  - If an interrupt was detected during the fetch phase, the CPU may skip decoding the current instruction and instead move to the interrupt handling routine.

### 4. **Execute Phase**
- **Standard Process**:
  - The CPU performs the operation specified by the instruction.

- **Interrupt Handling**:
  - If the CPU is executing an instruction and an interrupt occurs, it will complete the current instruction (if designed to do so) before jumping to the interrupt service routine (ISR).
  - The ISR is a special routine that handles the interrupt, performing necessary tasks (e.g., reading data from a device).

### 5. **Returning from Interrupt**
- After executing the ISR:
  - The CPU restores the saved state (e.g., PC, registers) from before the interrupt occurred.
  - The CPU resumes the instruction cycle with the instruction that was interrupted.

### Flowchart of Instruction Cycle with Interrupts

Here's a simplified flowchart representing the instruction cycle with interrupts:

```
+------------------+
|      Fetch       |
| (Get instruction)|
+--------+---------+
         |
         v
+------------------+
|      Decode      |
| (Interpret code) |
+--------+---------+
         |
         v
+------------------+
|      Execute     |
| (Perform action) |
+--------+---------+
         |
         v
+------------------+
|   Check for      |
|   Interrupts     |
+--------+---------+
         |
  +------|-------+
  |              |
  |  Yes        | No
  v              v
+------------------+    +------------------+
|  Save State      |    |  Continue        |
| (Current PC,     |    |  Execute next    |
|  Registers)      |    |  instruction      |
+--------+---------+    +--------+---------+
         |                     |
         v                     v
+------------------+    +------------------+
|  Execute ISR     |    |    End Cycle     |
+--------+---------+    +------------------+
         |
         v
+------------------+
|  Restore State   |
| (Return to PC)   |
+--------+---------+
         |
         v
+------------------+
|      Repeat      |
|     Instruction   |
|        Cycle      |
+------------------+
```

### Summary
The instruction cycle with interrupts enhances the responsiveness of a CPU by allowing it to handle asynchronous events while executing instructions. This mechanism ensures that critical tasks, such as responding to I/O requests, can be prioritized without significant delays, leading to more efficient multitasking and resource management in computer systems.

![image](https://github.com/user-attachments/assets/98adcba1-423c-4534-91b4-6a7a5be48aee)
