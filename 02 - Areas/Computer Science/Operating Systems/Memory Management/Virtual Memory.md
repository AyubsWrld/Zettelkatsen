**Virtual Memory** is an abstraction which offers programs their own private address spaces which are broken up into chunks called pages. Each page can either be loaded into memory or outside memory of memory in which case the process requests it and the operating system loads it into memory. 


##### Paging 

Most **Virtual Memory** system use a technique called paging. When programs run they generate **Virtual Addresses** ( When a MOV or JMP instruction is made to a specific location in memory ). **Virtual Memory Addresses** are then ran through the **[[Memory Management Unit]]** which translates these virtual addresses into physical ones and then put the **Physical Memory Address** onto the memory bus. 
  
The **Virtual Address Space** is divided up into fix units called **Page Frames** the **Pages** and **Page Frames** are usually the same size.

When a **Program** tries to reference an **Unmapped Address** for example, by using the instruction `MOVREG,32780` which is byte 12 within virtual page 8 (starting at 32768)? The MMU notices that the page is unmapped (indicated by a cross in the figure) and causes the CPU to [[Trap]] to the operating system. These [[Trap]]s are referred to as [[Page Fault]]s 

Now let us look inside the MMU to see how it works and why we have chosen to use a page size that is a power of 2. In Fig. 3-10 we see an example of a virtual address, 8196 (0010000000000100 in binary), being mapped using the MMU map of Fig. 3-9. The incoming 16-bit virtual address is split into a 4-bit page number and a 12-bit offset. With 4 bits for the page number, we can have 16 pages, and with 12 bits for the offset, we can address all 4096 bytes within a page. The page number is used as an index into the page table, yielding the number of the page frame corresponding to that virtual page. If the Present/absent bit is 0, a trap to the operating system is caused. If the bit is 1, the page frame number found in the page table is copied to the high-order 3 bits of the output register, along with the 12-bit offset, which is copied unmodified from the incoming virtual address. Together they form a 15-bit physical address. The output register is then put onto the memory bus as the physical memory address.

##### Paging Tables

> *"In a simple implementation, the mapping of virtual addresses onto physical ad dresses can be summarized as follows: the virtual address is split into a virtual page number (high-order bits) and an offset (low-order bits)."*

![[Pasted image 20250511152016.png]]

____
Tags : #methodologies #programming 