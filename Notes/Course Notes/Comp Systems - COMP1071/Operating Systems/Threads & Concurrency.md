#### Thread:
- A sequence of instructions that belong to a **process**, executing within it. A single process can have multiple threads doing different tasks
---
#### Shared & Private Threads:
When a process has multiple threads, they must share resources to work together, but they also need their own private space to keep track of their specific tasks
- **Shared Resources:** Threads within the same process share the code, data (global variables), and files
- **Private Resources:** Every individual thread has its own set of CPU registers and its own stack (where local variables are stored)
---
##### Mutual Exclusion (Collisions):
When multiple threads share the same resources (like a specific memory location), they need to synchronise, If they don't, they might try to update the same data at the same time, leading to errors.
###### Example: (Counter Error)
- Imagine two threads are trying to add $+1$ to a counter $C$ (Currently $0$), to make $C = 2$
1. **Thread 1** reads $C (0)$ and increments it to $1$
2. **Thread 2** reads $C (0)$ before Thread 1 has updated the value
3. **Thread 1** writes $1$ to $C$ (Updating the value after Thread 2 taken an old copy)
4. **Thread 2** calculates $0+1 = 1$, and writes $1$ to $C$

_**Result:** Results in both Threads doing 0+1=1, instead of Thread 1 doing 0+1=1, then thread 2 doing 1+1=2_
###### Solution:
- **Plan**: Ensure that two threads are never in their "critical section" (accessing the same resource) at the same time
- **Application**: One thread "locks" the resource, does its work, then unlocks it for the next thread
---
#### Single-Threading & Multi-Threading
- **Single-Threading:** The OS does not recognise the separate concept of a thread, it supports a single user process with a single thread (e.g., MS-DOS)
- **Multi-threading:** The OS supports multiple threads running within a single process
---
#### Benefits of Multi-Threading:
- **Responsiveness:** It may allow continued execution even if a part of the process is blocked, which is especially important for user interfaces
- **Resource Sharing:** Threads naturally share the resources of the process, which is easier than setting up shared memory or message passing between entirely separate processes
- **Cheaper:** It is cheaper than process creation, and thread switching has a lower overhead than context switching between full processes
- **Scalability:** A multi-threaded process can take advantage of multiprocessor architectures
---
### Concurrency & Amdahl's Law
#### Concurrency & Parallelism:
- **Concurrency:** Occurs on a single-core system where tasks are interleaved to create the illusion of simultaneous execution. (For example: $T_{1}$, $T_{2}$, $T_{3}$, $T_{4}$, $T_{1}\dots$)
- **Parallelism:** Occurs on a multi-core system where tasks literally run at the exact same time on different processing cores. (For example: core 1 runs $T_{1}$ while core 2 runs $T_{2}$)
---
#### Amdahl's Law:
- A formula that identifies the performance gains from adding additional cores to an application that has both serial and parallel components
###### Formula:
$$speedup \le \frac{1}{S + \frac{(1-S)}{N}}$$
- $S$ **(Serial Portion):** The proportion of the application that _must_ be executed serially (sequentially), expressed as a decimal between $0$ and $1$
- $N$ **(Processing Cores):** The total number of processing cores available to execute the parallel portion of the application
**Limits:** As $N$ approaches infinity, the theoretical speedup approaches $1/S$
---
##### Example:
- If an application is $25\%$ serial $(S = 0.25)$, and you go from $1$ core to $2$ cores $(N = 2)$, then:
$$speedup \le \frac{1}{0.25 + \frac{0.75}{2}}$$$$speedup \le \frac{1}{0.25 + 0.375} = \frac{1}{0.625} = 1.6$$
- Therefore adding a second core results in a $1.6$ times speedup
---
$\underline{\textbf{Related Pages: }}$
- [[Fundamentals of Operating Systems]]
- [[Processes]]