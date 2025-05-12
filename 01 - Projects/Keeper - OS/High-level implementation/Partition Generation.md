____
## OS Agnostic Idea:

#### Requirements: 
- Must work across platform operating systems ( Windows, OSX, Linux ). 
- Must be simple to follow and easy for the layman to use.
	- Must automatically scan which volume is best fit for the job. ( Query Disk Drivers ). 
- <mark style="background: #FF5582A6;">Must allocate enough auxiliary memory for the device to store all the dependencies</mark>
- Must keep track of where it was allocated for cleanup later. 
- Serialize this and store somewhere. 
##### Implementation: 
- **Executable** runs
- **Scan Partitions** and see what disks have enough space ( Sys-call to the hardware drivers might be hard to do on Windows and MacOS ) to allocate to the OS.
	- What good does calculating best fit partition allow ? Adds security and less user ability to game the system? ( On [[POSIX System]]s I believe you can mount relative to anywhere really, whether this )
	- It also keeps everything a bit more hands off from the user. 
- Once partition is created we must then place the operating system in the correct spot within the partition ( Where in memory it is placed matters ). 
- After that we serialize any metadata about the partition and store it for cleanup later. 
##### What could go wrong: 
- What happens if the process fails midway? 
____
## Windows ( Win32 API )
- 
#### Linux ( POSIX ). 
____

#### MacOS ( OS X )
____


____
Tags : #keeper #os