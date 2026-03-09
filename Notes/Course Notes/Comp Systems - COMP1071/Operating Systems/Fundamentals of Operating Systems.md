#### Operating System (OS):
- A program that acts as an intermediary between a user and the hardware
#### OS Kernel:
- The "single program that is loaded at boot-time and which has primary control of the processor"
- The kernel is always running in memory to manage memory, CPU security and hardware requests
###### Command-Line Interfaces (CLI):
- Fetches a command from the User and executes it. It can be implemented in the kernel or by systems programs
---
### Main Roles of an Operating System
- **Resource Allocator:** Responsible for the management of the computer system resources. It ensures that resources like CPU time and memory are used fairly and efficiently.
- **Control Program:** Controls the execution of user programs and the operation of input/output (I/O) devices. It is designed to prevent errors and the improper use of the computer.
- **Abstract Machine (Virtualisation):** Abstracts complex hardware into clean, easy-to-use interfaces. 
	- **Example:** It presents a mechanical hard disk (with tracks and sectors) as a neat, organised file system
---
### Computer System Structure
This is the layered architecture of a computer system
1. **Hardware:** Provides the basic computing resources, including the CPU, memory, and I/O devices
2. **Operating Systems:** Controls and coordinates the use of the hardware among various applications and users
3. **Application Programs:** Define the specific ways in which the system resources are used to solve the computing problems of the users. Examples include compilers, web browsers, and database systems
4. **Users:** The entities interacting with the system, which can be people, machines, or other computers
---
### OS Operations, Dual-Mode & Privileged Instructions
#### Dual-Mode Operation:
- A hardware-supported architecture that divides system execution into two distinct modes to protect the operating system and other system components. 
- **Simpler Definition:** Its a Security boundary that ensures regular applications cannot accidentally or maliciously crash the computer. They must ask the OS to handle anything important
#### Privileged Instructions
- Specific machine instructions that can only be executed when the processor is operating in Kernel Mode
---
### The Two Modes:
##### User Mode (Mode Bit = 1):
- The restricted environment where standard application programs execute.
##### Kernel Mode (Mode Bit = 0):
- The privileged environment where the OS executes, possessing full access to all hardware and instructions. (Also referred to as supervisor, system, or privileged mode)
##### Mode Bit:
- A hardware flag that allows the system to distinguish whether it is currently running user code or kernel code
---
#### Switching from User to Kernel Mode:
Switching from User Mode to Kernel Mode happens automatically when a system call changes the mode to kernel, and returning from the call resets it back to user mode. 
**Switching from User to Kernel Mode occurs when:**
1. **System Call:** A user process explicitly requests a service from the OS that requires a privileged instruction
2. **Hardware Interrupt:** A device (like a keyboard) signals the CPU that an event has occurred
3. **Software Error (Trap):** An error condition (like a crash) occurs within a user process
4. **Privilege Violation:** A user program attempts to execute a privileged instruction while still in User Mode
---
### Operating System Types
###### Multi-User:
- Allows two or more users to run programs at the same time
###### Multi-Programming:
- Organises jobs (code and data) so the CPU always has a job to execute (efficiency). A subset of total jobs in the system is kept in memory. When a job has to wait (e.g. an I/O operation), the OS switches to another job
###### Multi-Tasking (Timesharing):
- The CPU switches jobs so frequently that users can interact with each job while it is running, creating an interactive computing environment
###### Multi-Threading:
- Allows different parts of a single program to run concurrently
###### Real Time:
- Designed to respond to inputs instantly
---
### Operating System Services
The OS provides an environment for the execution of programs, offering services beneficial to both programs and users
#### Services beneficial the User:
###### User Interface: 
- Almost all OS provide a UI, like Command-line (CLI), GUI, or Batch interfaces
###### Program Execution:
- The OS must be able to load a program into memory, run it, and end execution (either normally or abnormally, indicating an error)
###### I/O Operations:
- A running program may require input/output, which could involve a file or an I/O device
###### File-system Manipulation:
- Programs need to read, write, create, and delete files and directories. This includes searching them, listing file information, and managing permissions
###### Communication:
- Exchanging information either on the same computer or on a network. This is done with shared memory or message passing (where packets are moved by the OS)
###### Error Detection:
- The OS must constantly be aware of possible errors occurring in the CPU, memory hardware, I/O devices, or user programs. It must take appropriate action to ensure correct computing, and provide debugging facilities
---
#### Services for Efficient System Operation (Resource Sharing)
###### Resource Allocation:
- When multiple users or jobs run concurrently, resources (like CPU cycles, main memory, and file storage) must be allocated to each of them
###### Accounting:
- Keeps track of how much computer resources each user uses, and the types of computer resources that they are using
###### Protection & Security:
- Ensures that all access to system resources is controlled. Concurrent processes must not interfere with each other, and the system must be secured from outsiders via user authentication
---
#### OS Design Principles
When building an OS we have to consider:
1. **Policy:** What will be done?
2. **Mechanism:** How to do it?

_Separating these two concepts allows for maximum flexibility if policy decisions need to be changed later._

---
#### Operating System Structures
##### 1. Simple Structure
- **Concept:** Written to provide the most functionality in the least amount of space
- **Characteristics:** It isn't divided into modules. Its interfaces and levels of functionality aren't well separated
- **Example:** MS-DOS
---
###### 2. Monolithic Structure
- **Concept:** A single file, single address space approach. Often referred to as the "spaghetti nest" approach because everything is tangled up with everything else
- **Characteristics:** The OS consists of two separable parts: Systems programs and the Kernel. The Kernel handles everything below the system-call interface and above the physical hardware (e.g. file system, CPU scheduling, memory management) all in one large level
- **Examples:** Original UNIX, Linux, and Windows
---
##### 3. Layered Approach:
- **Concept:** The operating system is divided into a number of discrete layers (levels)
- **Characteristics:** The bottom layer (layer 0) is the hardware, and the highest (layer N) is the user interface. It relies heavily on modularity, where each layer uses the functions and services of only the lower-level layers
- **Drawback:** It is generally considered unrealistic to perfectly layer a modern OS in practice
---
###### 4. Microkernel Structure:
- **Concept:** Moves as much functionality as possible from the kernel into user space
- **Characteristics:** Communication takes place between user modules using message passing rather than direct kernel interaction
- **Drawback:** There is a performance overhead caused by the constant communication required between user space and kernel space
- **Examples:** Mach, and the Mac OS X kernel (Darwin), which is partly based on Mach
---
$\underline{\textbf{Related Pages: }}$
- [[Processes]]
- [[Threads & Concurrency]]