Once we begin to concern ourselves with scheduling threads we get a new level of parallelism: processes and threads. Of course how threads are scheduled depends on their implementation ( [[User Level Versus Kernel Level Threads]] ). 


#### User-Level Thread Scheduling 
___
 If the threads were implemented at a [[User Level]], since the kernel is not aware of the threads, the scheduling of threads is left up to the user and are limited by whether the process is currently able to utilize the CPU or not. 
 
>*"Let us consider user-level threads first. Since the kernel is not aware of the ex istence of threads, it operates as it always does, picking a process, say, A, and giv ing A control for its quantum. The thread scheduler inside A decides which thread to run, say A1. Since there are no clock interrupts to multiprogram threads, this thread may continue running as long as it wants to. If it uses up the process’ entire quantum, the kernel will select another process to run. When the process A finally runs again, thread A1 will resume running. It will continue to consume all of A’s time until it is finished. However, its antisocial be havior will not affect other processes. They will get whatever the schedule"*

The scheduling algorithm used by the run-time system can be any of the ones described above. In practice, round-robin scheduling and priority scheduling are most common. The only constraint is the absence of a clock to interrupt a thread that has run too long. Since threads cooperate, this is usually not an issue

#### Kernel-Level Thread Scheduling 
___
In this case the kernel can schedule CPU time on a per-thread basis. Since this is the case the Operating system can assign a [[Quantum]] on a per-thread basis as well. 


#### Differences
___
The biggest difference lies in performance. Since the Kernel is aware of the threads when they are implemented in [[Kernel-Space]], it can take this into account when determine whether to perform a context switch to another process. For example, Process $A$ has a thread, $A_1$, which has blocked, however process $A$ also has a thread $A_2$ which is ready. Instead of performing a [[Context-Switch]] to a ready thread in a completely different process which is expensive ( Must clear the cache and load the resources ), since threads $A_1$ and $A_2$ share the same resources it is far more rational to just allow $A_2$ to run. 

Another important difference is the fact that User-Level Applications can more granularly specify which thread gets to run ( This is done through a per application thread scheduler created by the user).  

> *"Another important factor is that user-level threads can employ an applica tion-specific thread scheduler. Consider, for example, the Web server of Fig. 2-8. Suppose that a worker thread has just blocked and the dispatcher thread and two worker threads are ready. Who should run next? The run-time system, knowing what all the threads do, can easily pick the dispatcher to run next, so that it can start another worker running. This strategy maximizes the amount of parallelism in an environment where workers frequently block on disk I/O. With kernel-level threads, the kernel would never know what each thread did (although they could be assigned different priorities). In general, however, application-specific thread schedulers can tune an application better than the kernel can."*

___
Tags : #computer-architecture #operating-systems #processes