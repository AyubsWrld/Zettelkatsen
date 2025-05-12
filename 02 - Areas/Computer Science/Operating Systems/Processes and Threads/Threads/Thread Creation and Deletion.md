Multithreaded Programs usually start off with a singular thread which then has the ability to call a routine to create another thread such as `thread_create`. This routine usually takes a procedure as an argument for the thread to carry out. The created thread is now schedulable and is assigned a thread ID to reference the thread.

When the thread has finished carrying out its procedure or the designer sees that the thread no longer serves a purpose, the thread can be destroyed through the use of a library defined deletion routine such as `thread_exit`. The thread is then no longer schedulable. 
___
Tags : #computer-architecture #operating-systems #processes