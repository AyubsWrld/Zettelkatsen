- When a parent process creates a child process, they are both within ready state, so it becomes of little importance which process runs next. 
- When a process exits, which process should be chosen to run next ? 
- When a process blocks on I/O, on a semaphore, or for some other rea son, another process has to be selected to run. Sometimes the reason for blocking may play a role in the choice.
- when an I/O interrupt occurs, a scheduling decision may be made. If the interrupt came from an I/O device that has now completed its work, some proc ess that was blocked waiting for the I/O may now be ready to run. It is up to the scheduler to decide whether to run the newly ready process, the process that was running at the time of the interrupt, or some third process.
___
Tags : #computer-architecture #operating-systems #processes