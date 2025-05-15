- **Soft Miss**: Not in TLB -> [[Page Table Walk]] occurs -> evict value out of the TLB -> write the new translation into the TLB. 
- **Hard Miss**: Different cases..
	- **Hard Miss**: Page not in [[Translation Lookaside Buffer]] nor is it mapped, however it is in use by another process so it can just be mapped . 
	- **Harder Miss**: Page not in [[Translation Lookaside Buffer]] nor is it mapped, and it also isn't in main memory so it must be loaded from disk. 
	- **Hardest Miss**: it is possible that the program simply accessed an invalid address and no mapping needs to be added in the TLB at all. In that case, the operating system typically kills the program with a segmentation fault.
____
Tags : #methodologies #programming 