It is important to separate the **[[Scheduling Mechanism]]** from the **[[Scheduling Policy]]**, What this means is that the scheduling algorithm is parameterized in some way, but the parameters can be filled in by user processes.

> *"Suppose that the kernel uses a priority-scheduling algorithm but pro vides a system call by which a process can set (and change) the priorities of its children. In this way, the parent can control how its children are scheduled, even though it itself does not do the scheduling. Here the mechanism is in the kernel but policy is set by a user process. Policy-mechanism separation is a key idea."* 

This is because it is entirely possible that the parent process has some awareness of the precedence of its children so it should have some ability to tell the kernel how to schedule CPU time amongst its children.
___
Tags : #computer-architecture #operating-systems #processes