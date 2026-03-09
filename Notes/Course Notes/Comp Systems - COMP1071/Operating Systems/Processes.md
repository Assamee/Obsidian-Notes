#### Process & Programs
- **Program:** A static file residing on a disk (passive)
- **Process:** A program that is currently being executed in memory (active)
##### Processes:
A process consists of two elements:
- **Threads:** A sequence of instructions that execute sequentially
- **Address Space:** A set of memory locations in main memory that the process can read from and write to
---
#### Process Resources & Activity
- **Resource Allocation:** A process could be allocated CPU time, memory, files, and I/O devices
- **Current Activity:** The OS tracks what the process is currently doing, represented by the program counter and the contents of the CPU's registers
---
#### Process Memory Layout
When a process is loaded into memory, its **address space** is partitioned into these sections:
- **Stack:** Holds temporary data such as local variables
- **Heap:** Contains memory that is dynamically allocated while the process is actively running
- **Data Section:** Stores the program's global variables
- **Text Section (Code):** Contains the actual code being executed
###### Diagram:
``` Plaintext
High Memory (max)
+------------------+
|      Stack       |  <-- Grows downwards
|        |         |
|        v         |
|                  |
|        ^         |
|        |         |
|      Heap        |  <-- Grows upwards
+------------------+
|      Data        |  <-- Global variables
+------------------+
|      Text        |  <-- Code
+------------------+
Low Memory (0)
```
---
### Process Control Block (PCB)
- A data structure where a process's information is stored by the operating system
_(also known as the task control block)_ 
---
#### Key Data Stored in the PCB:
- **Process ID:** A unique identifier for the process (PID - Process ID)
- **Process State:** The current phase of the process (e.g. new, ready, blocked)
- **Program Counter:** The address of the _next_ instruction to run (saved here when the process is paused)
- **CPU Registers:** A snapshot of all register values (so the process can resume exactly where it left off)
- **Memory Usage & Limits:** Info about the process's address space
- **Accounting & I/O Status:** Data on resources consumed (like time) and a list of open files
---
#### Process Table:
- A collection of all the PCBs forms a process table
- Real implementations involve hashing, chaining or allocation bitmaps for efficiency
---
### Process States & Life-Cycle
A process moves through different states based on scheduler decisions or events.
#### The 5 Process States:
- **New:** The process is currently being created
- **Ready:** The process is ready to be dispatched to the CPU
- **Running:** The process's instructions are currently being executed by the CPU
- **Waiting (Blocked):** The process is waiting an event to happen (like a user input) and cannot run, even if the CPU is free 
- **Terminated (Exit):** The process has completed its execution, or some other event has caused its termination
---
#### State Transitions (The Lifecycle):
1. **Admitted:** The process moves from **New** to **Ready**
2. **Scheduler Dispatch:** The OS selects a process from the **Ready** queue and moves it to **Running**
3. **Interrupt:** A **Running** process is forced back to the **Ready** state (e.g. its allocated time slice ran out)
4. **I/O or Event Wait:** A **Running** process requests I/O and moves to **Waiting**
5. **I/O or Event Completion:** The requested I/O finishes, waking the process up and moving it from **Waiting** back to **Ready**
6. **Exit:** A **Running** process finishes and moves to **Terminated**
##### Diagram:
``` Plaintext
				 +-------+
                 |  New  |
                 +-------+
                     | admitted
                     v
+---------+      +-------+  scheduler dispatch   +---------+      +------------+
| Waiting | <--- | Ready | <-------------------> | Running | ---> | Terminated |
+---------+      +-------+       interrupt       +---------+ exit +------------+
   ^   |                                            |
   |   | I/O or event completion                    | I/O or event wait
   |   +--------------------------------------------+
   +------------------------------------------------+
```
---
### Process Creation
##### Process Hierarchy:
- Parent processes can create child processes, which can in turn create their own children, forming a tree-like hierarchy
---
##### Resource Sharing Models:
When a child is created, resources can be handled in three ways:
1. The parent and child processes share all resources
2. The child process shares only a subset of the parent's resources
3. The parent and child processes share no resources at all
---
##### Execution Models:
Once the child is created, the system executes them in one of two ways:
1. The parent and child execute concurrently (at the same time)
2. The parent waits until the child terminates before continuing
---
##### UNIX Creation Flow & Address Space:
A child process duplicates the address space of its parent, which allows for easier communication between them. 

In UNIX systems (Linux), this follows a specific step-by-step flow:
1. **Fork:** The `fork()` system call creates a new process
2. **Exec:** The `exec()` system call is used after a `fork()` to replace the child process's memory space with a new program
---
### Process Termination
#### Normal Exit:
- A process executes its last statement and asks the OS to delete it using the `exit()` system call
- Data is output from the child to the parent (via `wait()`), and the child's resources are de-allocated by the OS
#### Forced Termination:
A parent may forcefully terminate a child process if:
- The child has exceeded its allocated resources
- The task assigned to the child is no longer required
- The parent itself is terminating (this is known as cascade termination, where all children and grandchildren are terminated)
#### Special Termination States:
- **Zombie Process:** A process that has terminated, but its parent has not yet invoked `wait()` to collect its exit status
- **Orphan Process:** A process that is still running, but its parent has terminated without invoking `wait()`
---
### Process Scheduling Queues
- The main aim is to maximise CPU use and quickly switch processes onto the CPU for time-sharing
#### The Three Queue Types:
The process scheduler selects among available processes for next execution by maintaining specific scheduling queues:
- **Job Queue:** The set of all processes currently in the system
- **Ready Queue:** The set of all processes residing in main memory that are ready and waiting to execute
- **Device Queue:** The set of processes waiting for an I/O device to become available
_Processes switch between these queues during their lifecycle_
---
$\underline{\textbf{Related Pages: }}$
- [[Fundamentals of Operating Systems]]
- [[Threads & Concurrency]]