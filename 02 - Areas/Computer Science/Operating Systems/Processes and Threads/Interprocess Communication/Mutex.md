**Mutual Exclusion ( Mutex )** facilitated through an integer type that represents whether a shared resource is accessible for reading/writing. Can only be in one of two states, **Locked** and **Unlocked**. 

When a thread ( or process ) wishes to enter its critical region it calls `mutex_lock`, any thread or process which attempts to access the shared resource must first check the mutex, if it is in use the process busy wait until the mutex is freed again using `mutex_unlock` . This freeing of the mutex can and must be done when the process or thread has exited it's critical region. 

![[Pasted image 20250509123959.png]]
With all software, there is always a demand for more features, and synchronization primitives are no exception. For example, sometimes a thread package offers a call mutex trylock that either acquires the lock or returns a code for failure, but does not block. This call gives the thread the flexibility to decide what to do next if there are alternatives to just waiting.
___
Tags : #computer-architecture #operating-systems #processes