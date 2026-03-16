#### The Three Types of Schedulers
- **Long-term Scheduler:** Selects which processes should be brought into the **ready** queue
- **Medium-term Scheduler:** A part of swapping that is in charge of handling swapped-out processes (Swapping processes out of RAM, when it gets too full)
- **Short-term Scheduler:** Selects the process to be executed next and allocates it to the CPU
---
### The Dispatcher & Context Switching
#### Dispatcher:
- The module that give control of the CPU to the process selected by the CPU scheduler
#### Functions of the Dispatcher:
To hand over control, the dispatcher performs three specific tasks:
1. **Switching Context:** Saving the state of the old process and loading the state of the new one
2. **Switching to User Mode:** Moving the system out of Kernel Mode so the user program can safely run
3. **Jumping to Location:** Moving the program counter to the proper location in the user program to restart it exactly where it left off
#### Dispatch Latency:
- The time it takes for the dispatcher to stop one process and start another
---
### Optimisation Goals:
A good scheduling algorithm aims to optimise the following:
###### CPU Utilisation (Maximise)
- Keep the CPU as busy as possible
###### Throughput (Maximise):
- The number of processes that successfully complete their execution per unit of time
###### Turnaround Time (Minimise):
- The total amount of time required to execute a particular process from start to finish (waiting time + execute time + I/O time)
###### Waiting Time (Minimise):
- The total amount of time a process spends sitting in the ready queue, waiting for its turn
###### Response Time (Minimise):
- The amount of time it takes from when a request was submitted until the _first_ response is produced (i.e., initial access to the CPU), not the time to complete the whole process
---
# Scheduling Algorithms

##### Pre-emptive:
- The OS can interrupt a running process to allocate the CPU to another process
---
### First Come, First Served (FCFS):
- The first process to request for CPU usage, is allocated the CPU until its completed
#### Algorithm Characteristics:
- **Implementation:** Simple to implement
- **Non Pre-emptive:** Once a process is allocated to the CPU, it runs to completion without interruption
##### Drawback:
- **Convoy Effect:** Where short processes are forced to wait behind a single long process. Average waiting time may be lengthy
##### Gantt Chart: (Convey Effect)
- Where $P_1$ takes 24ms, $P_2$ and $P_3$ take 3ms each
``` Plaintext
|========================|===|===|
0       P1               24  27  30
                         P2  P3
```
- **Average Weight Time:** $\frac{0 + 24 + 27}{3} = 17$
Moving the shorter processes to the front reduces the average weight time
``` Plaintext
|===|===|========================|
0   3   6                        30
 P2  P3            P1
```
- **Average Weight Time:** $\frac{6 + 0 + 3}{3} = 3$
---
### Shortest Job First (SJF)
- Sorts the processes by **CPU burst time** (a prediction of the length of the next CPU request), with the shortest first
#### Algorithm Characteristics:
- **Tie-breaking:** If two processes have the exact same length, FCFS (First Come First Serve) scheduling is used to break the tie
- **Non Pre-emptive:** Standard SJF is non pre-emptive. Once the CPU is given to the process, it cannot be pre-empted until the process has completed its CPU burst
- **Optimal:** SJF is theoretically optimal, it gives the minimum average waiting time for a given set of processes
#### Drawback:
- **Predictability:** Its hard to predict the length of the next CPU request before it actually runs
---
### Shortest Remaining Time First (SRTF)
- If a new process arrives in the ready queue with a **CPU burst length** less than the remaining time of the executing process, the running process is pre-empted and the new process is run
- **Simple Explanation:** A pre-emptive version of SJF. If a really quick job suddenly shows up while the CPU is working on a longer job, the CPU pauses the long job, finishes the quick one, and then goes back to where it left off
#### Algorithm Characteristics:
- **Pre-emptive:** Unlike standard SJF, it actively interrupts the current process if a better (shorter) process arrives
#### Example:
We have four processes arriving at different times:
- $P_{1}$: Arrives at $0$ms, needs $7$ms
- $P_{2}$: Arrives at $2$ms, needs $4$ms
- $P_{3}$: Arrives at $4$ms, needs $1$ms
- $P_{4}$: Arrives at $5$ms, needs $4$ms
##### Process:
1.  At time $0$, $P_{1}$ starts as it is the only process
2. At time $2$, $P_{2}$ arrives. $P_{1}$ has $5$ms remaining. $P_{2}$ only needs $4$ms , so $P_{1}$ is pre-empted and $P_{2}$ starts
3. At time $4$, $P_{3}$ arrives. $P_{2}$ has $2$ms remaining. $P_{3}$ only needs $1$ms , so $P_{2}$ is pre-empted and $P_{3}$ starts
4. At time $5$, $P_{3}$ finishes. $P_{2}$ ($2$ms remaining) resumes , as $P_{4}$ ($4$ms burst) and $P_{1}$ ($5$ms remaining) are longer
5. At time $7$, $P_{2}$ finishes. $P_{4}$ starts as it is shorter than the remaining time of $P_{1}$
6. At time $11$, $P_{4}$ finishes. $P_{1}$ finally resumes and finishes at $16$
![[Pasted image 20260316143948.png]]
---
### Round Robin (RR)
- Each process gets a small unit of CPU time (a time quantum or time slice), after which the process is pre-empted and added to the end of the ready queue
- **Simple Explanation:** Everyone takes turns, and each turn is of equal-length
#### Algorithm Characteristics:
- **Time Quantum $\textbf{(}q\textbf{)}$:** Usually set between $10$ to $100$ milliseconds
- **Fairness:** If there are $n$ processes in the ready queue, each process gets $1/n$ of the CPU time in chunks of at most $q$ time units at once
#### Performance Trade-off:
The performance of the RR algorithm depends heavily on the size of the time quantum:
- **Too Large:** If the time quantum is extremely large, the RR policy becomes exactly the same as the FCFS policy
- **Too Small:** If the time quantum is extremely small, the approach results in a massive number of context switches, which causes severe performance overhead
- **The Rule of Thumb:** $80$ percent of the CPU bursts should be shorter than the time quantum
#### Gantt Chart:
``` Plaintext
| P1 | P2 | P3 | P1 | P1 | P1 | P1 | P1 |
0    4    7   10   14   18   22   26   30
```
---
### Priority Scheduling
- An algorithm that associates a priority number (an integer) with each process, allocating the CPU to the process with the highest priority
#### Algorithm Characteristics:
- **Pre-emption:** This scheduling can be either pre-emptive (interrupting a lower-priority process currently running) or non pre-emptive
- **The Starvation Problem:** Also known as indefinite blocking. If high-priority processes keep arriving, a low-priority process may be pushed back continuously and never get to execute
#### Solutions to Starvation:
- **Ageing:** As time progresses, the system automatically increases the priority of a waiting process so it eventually gets processed
- **Combine with RR:** The system executes the highest-priority process first, but if multiple processes share that same priority level, it uses Round Robin scheduling amongst them
---
## Multilevel Queue & Feedback Queue Scheduling
### Multilevel Queue Scheduling
- The ready queue is partitioned into completely separate sub-queues based on process requirements (e.g. foreground/interactive processes vs. background/batch processes)
- **Independent Algorithms:** Each separate queue has its own scheduling algorithm. For example, the foreground queue might use Round Robin while the background queue uses FCFS
- **Inter-queue Scheduling:** The system must also schedule _between_ the queues using strict fixed priority (e.g., serve all foreground before any background) or time-slicing (e.g., 80% CPU time to foreground, 20% to background)
- **Drawback:** It is inflexible. A process remains permanently in the same queue regardless of how its requirements might adapt over time
---
### Multilevel Feedback Queue
- An adaption of the multilevel queue that allows processes to actively move between the various queues
- **Mechanism:** This is how modern systems (like Windows and macOS) implement ageing. If a process uses too much CPU time, it is demoted to a lower-priority queue. If it waits too long in a lower queue, it is gradually upgraded
- **Example Structure:** 1. Queue 0: RR with $q=8$ milliseconds. If it does not finish, it is demoted to Queue 1. 2. Queue 1: RR with $q=16$ milliseconds. If it still does not complete, it is demoted to Queue 2. 3. Queue 2: FCFS for the remaining heavy background tasks
---
### Algorithmic Evaluation
- A way of determining which scheduling algorithm is best for a particular system
#### 1. Deterministic Modelling
- This method takes a predetermined, specific workload (a set case of processes) and analytically calculates the performance of each algorithm against it
- **Example:** Given precise table of $5$ processes with fixed burst times to mathematically prove that SJF results in a lower average waiting time than FCFS for that exact scenario
#### 2. Queuing Models
- A mathematical approach using network analysis to estimate performance based on probabilities rather than fixed workloads
##### Little's Formula:
- A key equation used in queuing network analysis:$$n = \lambda \times W$$
    - $n$: The average long-term queue length
    - $\lambda$: The average arrival rate for new processes entering the queue
    - $W$: The average waiting time in the queue

- **Example Calculation:** If $7$ processes arrive every second ($\lambda = 7$) and there are normally $14$ processes in the queue ($n = 14$), you can rearrange the formula $(W = n / \lambda)$ to find that the average waiting time per process is $2$ seconds
#### 3. Simulation
- Creating a complex computer model of the system to simulate how the algorithms would perform under realistic conditions
- **Mechanism:** System designers use "trace tapes" (recorded logs of actual process execution, detailing exact CPU and I/O bursts) and feed them into the programmed model to generate highly accurate performance statistics for algorithms like RR or SJF
- **The Drawback:** Designers must beware of Bonini's paradox—the danger that the simulation model becomes just as complex and difficult to understand as the real-world system itself
#### 4. Post-Implementation (Live Testing)
- Examining the running operating system directly in a real-world environment
- **Application:** Also known as 'live' testing, this involves fully building the system, deploying the scheduling algorithm, and measuring its actual performance under day-to-day user workloads
---
