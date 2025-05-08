- **Processes** can be in either of three states with respect to execution 
	- **Blocked**: Waiting on input from another process or event. The CPU is free to perform other tasks while this a process is in blocked state. 
	- **Ready**: The process is ready for execution however the CPU is incapable of executing it's instructions. This could be due to the processes [[Quanta]] being exceeding and the CPU deciding to allocated some time to another process. 
	- **Running**: The process is currently being executed. 
___
Tags : #computer-architecture #operating-systems #processes