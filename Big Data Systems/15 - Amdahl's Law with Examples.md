Amdahl's Law is a fundamental principle in parallel computing that quantifies the potential speedup in a program's execution time when a portion of it is parallelized. It states that the speedup of a program is limited by the sequential portion of the code. Here's the mathematical representation of Amdahl's Law:

$\[S = \frac{1}{(1 - P) + \frac{P}{N}}\]$

Where:
- \(S\) is the speedup of the program.
- \(P\) is the proportion of the program that can be parallelized.
- \(N\) is the number of processors.

Let's explore Amdahl's Law with some examples:

**Example 1: Speeding up Image Processing**

Suppose you have an image processing program that performs three main tasks: loading an image (30% of total time), applying filters (40%), and saving the result (30%).

1. **Sequential Version:**
   - Total time: 100 units
   - Load: 30 units, Filters: 40 units, Save: 30 units

2. **Parallel Version:**
   - Assume you can parallelize the filter application (40%).
   - So, \(P = 0.4\) and \(1 - P = 0.6\).

   - With 4 processors:
     - Speedup = $\(\frac{1}{(1 - 0.4) + \frac{0.4}{4}} = 1.67\)$ times faster.
     - Total time: $\(\frac{100}{1.67} \approx 60\)$ units.

   - With 8 processors:
     - Speedup = $\(\frac{1}{(1 - 0.4) + \frac{0.4}{8}} = 2.22\)$ times faster.
     - Total time: $\(\frac{100}{2.22} \approx 45\)$ units.

**Example 2: Database Queries**

Consider a database system where 20% of the time is spent on processing queries, and the remaining 80% is spent on disk I/O and other tasks.

1. **Sequential Version:**
   - Total time: 100 units
   - Query processing: 20 units, I/O and other tasks: 80 units

2. **Parallel Version:**
   - Assume you can parallelize the query processing (20%).
   - So, \(P = 0.2\) and \(1 - P = 0.8\).

   - With 4 processors:
     - Speedup = $\(\frac{1}{(1 - 0.2) + \frac{0.2}{4}} = 1.25\)$ times faster.
     - Total time: $\(\frac{100}{1.25} = 80\)$ units.

   - With 8 processors:
     - Speedup = $\(\frac{1}{(1 - 0.2) + \frac{0.2}{8}} = 1.43\)$ times faster.
     - Total time: $\(\frac{100}{1.43} \approx 70\)$ units.

These examples illustrate that Amdahl's Law highlights the diminishing returns of parallelization as the sequential portion of a program becomes a larger fraction of the total execution time. It emphasizes the importance of identifying and optimizing the critical paths in a program to achieve meaningful speedup.
