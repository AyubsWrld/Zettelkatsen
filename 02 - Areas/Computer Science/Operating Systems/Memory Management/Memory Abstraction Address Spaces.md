#### The Notion of an Address Space
___
An address space is a set of addresses a process can use to address memory. 

##### Base and Limit Registers

- Each program has a **Base** and **Limit** register. 
 
- **Base Register**: stores the memory location of where the programs address space begins in physical memory. 
 
- **Limit Register**: stores the length of the program. 
 
- Whenever an instruction is made it is converted to the physical address and executed. If for example, a **JMP** instruction was issued to address 28 it would become **JMP 28 + Base** and then compared to the **Limit** register to see if the instruction landed out of bounds. 
 
- A disadvantage of relocation using base and limit registers is the need to per form an addition and a comparison on every memory reference. Comparisons can be done fast, but additions are slow due to carry-propagation time unless special addition circuits are used. 
##### Swapping

- We usually don't have enough space ( RAM ) to hold all the processes in a single space. To cater to all the processes we can move them in and out of RAM in what is known as **Swapping**. 
 
- We allocate memory for the process we desire to swap ( Sometimes it is desirable to allocate a process more little more memory than it initially requires in the case that it grows ) and then we move the process into **RAM** or swap it for another process. 

![[Pasted image 20250511141139.png]]

#### Managing Free Memory
___
When memory is assigned dynamically, the operating system must manage it. there are two ways to keep track of memory usage:
##### **Bit Maps** 

- *"Memory is divided into allocation units as small as a few words and as large as several kilobytes."* 
 
- Each allocation unit has a corresponding value within a bit map which, depending on whether it is 0 or 1, determines if the space is unit is occupied or not. 
##### Slab Allocators
____
Tags : #methodologies #programming 