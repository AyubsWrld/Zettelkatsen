Sometimes a programs required resources are not fully loaded into memory before execution begins, if a portion of execution relies on a resource not loaded into memory, the process is blocked and a system call to load the required resources into memory is issued. This is referred to as a page fault. 

This becomes especially problematic when you have a thread which causes a block to occur, to the Operating System, the entire process is viewed as being blocked and thus another process is scheduled to run even if there exists another thread that has the ability to run. 
___
Tags : #computer-architecture #operating-systems #processes