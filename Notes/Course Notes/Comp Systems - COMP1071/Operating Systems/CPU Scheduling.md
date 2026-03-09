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
### Scheduling Algorithms
