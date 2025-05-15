___
1. The IBM 360 had a scheme of locking 2-KB blocks by assigning each one a 4-bit key and having the CPU compare the key on every memory reference to the 4-bit key in the PSW. Name two drawbacks of this scheme not mentioned in the text.
	- The [[Program Status Word]] acts as a [[Status Register]] and [[Program Counter]] and contains information pertaining to the currently running process.
	- When we say "locking" what does this refer to ?
	- I'd assume that this would have to be done per reference however that's just the same as having it stored within the actual page itself. 
2. What is the difference between a physical address and a virtual address?
   - *Physical Address*: actual location in main memory ( or disk if not loaded into main memory ). 
   - *Virtual Address*: Abstraction provided by the operating system to processes to give the effect of contiguous memory. 
   - For each of the following decimal virtual addresses, compute the virtual page number and offset for a 4-KB page and for an 8 KB page: 20000, 32768, 60000.
	   - *Virtual page number*: 20000 % 4096 = 3616 page number 4. 
3. The Intel 8086 processor did not have an MMU or support virtual memory. Nevertheless, some companies sold systems that contained an unmodified 8086 CPU and did paging. Make an educated guess as to how they did it. (Hint: Think about the logical location of the MMU.)
	- You can implement paging by placing an **external MMU** between the CPU and the memory bus. The 8086 issues physical addresses based on segment:offset translation, and since the address lines go out to external memory, an external MMU can **intercept and translate** those physical addresses on the fly, effectively implementing paging without modifying the CPU itself.
	- No memory abstraction without the MMU, the physical addresses get placed on the memory bus. 
4. What is the difference between physical addresses and physical frames ? 
5. What kind of hardware support is needed for a paged virtual memory to work? 
	1. MMU
____
Tags : #methodologies #programming 