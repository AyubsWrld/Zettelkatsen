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


#### Translation Lookaside Buffer
___
- Most processes reference a small number of pages frequently with the bulk being rarely referenced. 
- Given that this is the case the solution that has been devised is to equip computers with a small hardware device for mapping virtual addresses to physical addresses without going through the page table called a **Translation Lookaside Buffer**. 

> *"An example that might generate the TLB of Fig. 3-12 is a process in a loop that spans virtual pages 19, 20, and 21, so that these TLB entries have protection codes for reading and executing. The main data currently being used (say, an array being processed) are on pages 129 and 130. Page 140 contains the indices used in the array calculations. Finally, the stack is on pages 860 and 861."*

![[Pasted image 20250512141109.png]]
- If the MMU does a look-up and the value is not found within the **TLB** it evicts an entry from the table, replacing it with the value after some look-up. This is referred to as a **TLB Hit**.When an entry is purged from the TLB, the modified bit is copied back into the page table entry in memory. What happend to the other bits ? 
#### Software TLB Management
___
- In most [[RISC]] systems, the **Translation Lookaside Buffer** is managed by the the software. When a TLB fault occurs, instead of the MMU going to the page tables to find the page frame number, it just generates a fault and tosses the problem into the lap of the operating system. 

#### Page Table Entries
___
Each page table entry has the following bits...
- **Caching Disabled**: 
- **Modified Bit**: Signifies whether the original page has been altered, can be discarded once the MMU wishes to reclaim a page frame. If this bit is set, a write to disk ( syscall ) must occur before discarding it. 
- **Protection Bit**: Signifies Access Capabilities ( 3 bits RWX ) 
- **Referenced Bit**: The Referenced bit is set whenever a page is referenced, either for reading or for writing. Its value is used to help the operating system choose a page to evict when a page fault occurs.
- **Present/Absent Bit**: Signifies whether the page frame is loaded into memory. 
- **Caching Disabled**: This feature is important for pages that map onto device registers rather than memory. If the operating system is sitting in a tight loop waiting for some I/O device to respond to a command it was just given, it is essential that the hardware keep fetching the word from the device, and not use an old cached copy. With this bit, caching can be turned off. Machines that have a separate I/O space and do not use memory-mapped I/O do not need this bit. See [[Memory Mapped IO]]
____
Tags : #methodologies #programming 