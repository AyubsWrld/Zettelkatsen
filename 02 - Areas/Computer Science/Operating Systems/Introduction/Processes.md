- Basically a container for all the resources needed to execute a program. 
	- Associated with each process is a set of resources is a set of resources including the [[Program Counter]], [[Stack Pointer]], and [[Registers]]. 
	- Each process has an address space which is the memory allocated to the process can read and write to. 
- All information about the process apart from the data held within its address space is stored in an operating system table called the [[Process Table]]. The [[Process Table]] is usually an array of structures one for each process currently is existence. 
- A ( Suspended ) Process is thus thought of consisting of its [[Core Image]] ( The contents of it's address space ) as well as its entry in the [[Process Table]].
- A process which was created by another process is referred to as a [[Child Process]]. 
![[Pasted image 20250505160627.png]]
- Processes can issue [[System Calls]] to request more memory. 
- If a process needs to interact with another process this is referred to as [[Inter-process Communication]]. An example could be one process waiting for a response after sending a signal to another process. The process may request that the operating system notify it after a number of seconds has elapsed if no acknowledgement has been received. When the specified number of seconds elapses the operating system can send an [[Alarm Signal]] to the process. The signal causes the process to temporarily suspend whatever it was doing, save its registers on the stack, and start running a special signal-handling procedure
___
Tags : #computer-architecture #operating-systems