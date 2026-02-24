#### Operating System (OS):
- A program that acts as an intermediary between a user and the hardware
#### OS Kernel:
- The "single program that is loaded at boot-time and which has primary control of the processor"
- The kernel is always running in memory to manage memory, CPU security and hardware requests
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
