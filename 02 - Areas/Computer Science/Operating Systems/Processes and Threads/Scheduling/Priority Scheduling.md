Processes are weighted based on importance this determines the time they can spend utilizing the CPU. 

It is often the case however that the processes still conform to running under a maximum time [[Quantum]], thus, when a processes has been running for longer than that assigned [[Quantum]], a [[Context Switch]] occurs regardless of the priority of the process. 

A simple algorithm for giving good service to I/O-bound processes is to set the priority to 1/ f , where f is the frac tion of the last quantum that a process used. A process that used only 1 msec of its 50-msec quantum would get priority 50, while a process that ran 25 msec before blocking would get priority 2, and a process that used the whole quantum would get priority 1.
___
Tags : #computer-architecture #operating-systems #processes