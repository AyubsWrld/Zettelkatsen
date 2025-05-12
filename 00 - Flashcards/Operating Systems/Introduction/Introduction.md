_____
Tags: #operating-systems #flash-cards
____

What is the purpose of a processor ? ;; To perform Arithmetic and Logical operations on operands as well as control instructions. 


What is a register ? ;; A memory storage location within the CPU.

What is the size of a register ? ;; Directly related to the architecture. 64bit architecture -> 64bit registers. 

What are the two types of registers? ;; General purpose & special registers

What is Kernel Mode ? ;; **Kernel mode** is a **CPU execution mode** that grants software **full access to all hardware resources and system memory**, including the **privileged instructions and memory regions** that are off-limits in user mode. It is where the **core parts of the operating system run**, including device drivers, memory managers, schedulers, and system call handlers.

What is User Mode ? **User mode** is the **CPU execution mode** in which **applications** (like browsers, editors, games, etc.) run — **not the operating system kernel**.


True or false ? If a user wants to install a new portion of the kernel they can ;; False, the Kernel cannot be changed. 

True or false ? A process running in User Mode of CPU execution can never have access to the underlying hardware. ;; False, through the use of a System Call the user can gain access to the underlying hardware. 

How can a Software running in User Mode request access to the underlying hardware ? ;; Through the use of a system call. 

Are errors made while the CPU is in Kernel Mode of execution recoverable? ;; No, it will cause the system to crash. 

What happens after a System Call is fulfilled ? ;; CPU resumes execution from the instruction after the system call.

What are the components of memory in order of speed ? ;; Registers, Cache ( L1, L2, L3 ), RAM ( Main Memory ), Non-volatile memory.


What is a device driver ? A piece of software which serves as an interface between the controller of a piece of hardware and the Operating Systems Kernel. 

What is a Procedure Call ? ;; A Procedure Call is a normal control flow operation which does not require switching between **User Mode** and **Kernel Mode**. 

What are the two main functions of an operating system? ;; To provide an abstraction for software to interact with the underlying hardware. And to manage hardware resources. 

What is the difference between timesharing and multiprogramming systems? ;; **Multiprogramming** is about keeping the CPU busy, while **timesharing** is about keeping **users happy and the system responsive**. They also differ in what metric is used to determine whether their processes is currently being executed by the operating system. 

How is process execution determined in a time-sharing system? ;; Based on time referred to as a quanta, after which the kernel wakes up and schedules another process to be executed. 


How is process execution determined in a process-sharing system? ;; A process is interleaved based on whether it is blocked by some I/O operation ( Fulfilling a Syscall ). 

What is a Cache line ? ;; 