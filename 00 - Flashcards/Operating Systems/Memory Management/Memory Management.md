____

Tags : #methodologies #programming 

____

What is the problem with no memory abstraction ? ;; Only one program can run at a given time otherwise we run the chance that a program overrides another. 

Why were Base and Limit Registers used? ;; Used in memory management to allow programs to have their own private address spaces. The Base register holds where the program starts in physical memory and the limit register keeps track of the length of the program. 

How are physical memory addresses mapped onto private address spaces using Base and Limit registers ? ;; Take instruction + Base and see if it is within bounds of limit + base. 

What is Virtual Memory ? ;; Memory abstraction wherein each process has its own address space is loaded into memory in chunks called pages, Each page is a contiguous range of addresses. 

What is a Virtual Page ? ;; 


What is a Page Frame ? ;; 

What is RISC ? ;; 

What is the difference between Hardware Managed TLB and Software Managed TLB ? ;; 

What is a TLB ? ;; 


