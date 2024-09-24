### **Amdahl's Law**

**Amdahl's Law** is a formula that provides insight into the potential speedup that can be achieved when only a portion of a program is parallelized. It highlights the limits of parallelization and illustrates the diminishing returns of adding more processors to a system when part of the task must still be performed serially.

### **The Formula**

Amdahl’s Law can be expressed as:

$\[
S(n) = \frac{1}{(1 - P) + \frac{P}{n}}
\]$

Where:
- **S(n)** = Speedup of the system with **n** processors.
- **P** = Proportion of the program that can be parallelized (between 0 and 1).
- **1 - P** = Proportion of the program that must remain serial (cannot be parallelized).
- **n** = Number of processors used in parallel.

### **Key Points of Amdahl’s Law**:
- If **P = 1** (i.e., the entire program is parallelizable), the speedup is proportional to the number of processors.
- If **P = 0** (i.e., none of the program can be parallelized), adding more processors won’t speed up the execution.
- The serial portion, **1 - P**, becomes the bottleneck as more processors are added, limiting the overall speedup.

### **Example 1: Simple Calculation of Speedup**

Suppose a program is 60% parallelizable (**P = 0.6**) and 40% of the program is serial (**1 - P = 0.4**).

Let's calculate the speedup for different numbers of processors **n**.

#### **Case 1: Single Processor (n = 1)**
$\[
S(1) = \frac{1}{(1 - 0.6) + \frac{0.6}{1}} = \frac{1}{0.4 + 0.6} = 1
\]$
No speedup since only one processor is used.

#### **Case 2: Two Processors (n = 2)**
$\[
S(2) = \frac{1}{(1 - 0.6) + \frac{0.6}{2}} = \frac{1}{0.4 + 0.3} = \frac{1}{0.7} \approx 1.43
\]$
With two processors, the program is 1.43 times faster.

#### **Case 3: Four Processors (n = 4)**
$\[
S(4) = \frac{1}{(1 - 0.6) + \frac{0.6}{4}} = \frac{1}{0.4 + 0.15} = \frac{1}{0.55} \approx 1.82
\]$
With four processors, the program is 1.82 times faster.

#### **Case 4: Ten Processors (n = 10)**
$\[
S(10) = \frac{1}{(1 - 0.6) + \frac{0.6}{10}} = \frac{1}{0.4 + 0.06} = \frac{1}{0.46} \approx 2.17
\]$
With ten processors, the program is 2.17 times faster. Notice how the speedup increases at a slower rate as more processors are added due to the serial portion of the program.

### **Example 2: Visualization of Diminishing Returns**

Let’s consider a hypothetical scenario where:
- **80% of the program can be parallelized** (**P = 0.8**).
- The remaining **20% is serial** (**1 - P = 0.2**).

#### **Speedup for Different Numbers of Processors**:

1. **n = 1 processor**:
   $\[
   S(1) = \frac{1}{0.2 + 0.8} = 1
   \]$
   No speedup with a single processor.

2. **n = 2 processors**:
   $\[
   S(2) = \frac{1}{0.2 + \frac{0.8}{2}} = \frac{1}{0.2 + 0.4} = \frac{1}{0.6} \approx 1.67
   \]$
   1.67 times faster with two processors.

3. **n = 4 processors**:
   $\[
   S(4) = \frac{1}{0.2 + \frac{0.8}{4}} = \frac{1}{0.2 + 0.2} = \frac{1}{0.4} = 2.5
   \]$
   2.5 times faster with four processors.

4. **n = 8 processors**:
   $\[
   S(8) = \frac{1}{0.2 + \frac{0.8}{8}} = \frac{1}{0.2 + 0.1} = \frac{1}{0.3} \approx 3.33
   \]$
   3.33 times faster with eight processors.

5. **n = 16 processors**:
   $\[
   S(16) = \frac{1}{0.2 + \frac{0.8}{16}} = \frac{1}{0.2 + 0.05} = \frac{1}{0.25} = 4
   \]$
   4 times faster with 16 processors.

As you can see, even with an infinite number of processors, the maximum theoretical speedup would be:

$\[
S(\infty) = \frac{1}{(1 - P)} = \frac{1}{0.2} = 5
\]$

No matter how many processors are added, the maximum speedup is capped by the serial portion of the program.

### **Takeaways from Amdahl's Law**:
1. **Limited Speedup**: Adding more processors will eventually lead to diminishing returns. This is because the serial portion of the program cannot be improved through parallelization.
   
2. **Parallelizable Portion is Crucial**: The more of the program that can be parallelized, the more you can benefit from additional processors. If most of the program is serial, parallelizing it will have little impact on performance.

3. **Practical Limitations**: In real-world scenarios, communication overhead and synchronization between processors also limit speedup, which is not captured in Amdahl’s Law but further emphasizes the challenges of parallelism.

### **Conclusion**
Amdahl's Law illustrates that the speedup of a program using multiple processors is limited by the portion of the program that remains serial. It emphasizes the need to reduce the serial parts of a program to maximize the benefits of parallelization but shows that even with infinite processors, speedup will be bounded by the program’s inherent serial portion.
