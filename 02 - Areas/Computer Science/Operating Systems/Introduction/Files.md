- Hierarchical structure similar to [[Process Hierarchies]] which can be expressed as a **trees**. However [[Process Hierarchies]] are usually short lived whereas [[Directory Hierarchies]] persist for years. 
- Processes have current working directories . 
- The top of the root note of the Directory Hierarchy is aptly named the root directory to which every child directory can be expressed relative to this directory. 
- The path of directory expressed relative to the root directory it is referred to as its absolute path. 
- To read and write to a file requires that the file be opened. This issues a [[System-Call]] which returns a small integer called a [[File-Descriptor]] to use in subsequent operations. In the case access is prohibited, an error code is returned instead. 
- the [[mount]] [[System-Call]] in Unix systems allows for the file system of an optical disc to be mounted onto some empty directory within the already present file-system. This target directory for the mounting process has to be empty as it must serve as the root directory of the optical disc. 
- [[Special Files]] are I/O devices which allow for interaction between them and the operating system using the same means available normal files ( Treated as files even though they aren't ). They exist in two forms 
	- [[Block Special Files]]: Used to model blocks of devices that are consist of a collection of randomly addressable blocks of memory, such as disks. ===By opening a block special file and reading, say, block 4, a program can directly access the fourth block on the device, without regard to the structure of the file system contained on it.=== 
	- [[Character Special Files]]: used to model printers, modems, and other devices that accept or output a character stream.
	- By convention these special files are kept within the `/dev` directory. 
- A [[Pipe]] is a sort of pseudofile that connects two processes and is indistinguishable by the processes as just another file. However a process can make a system call to see whether its an actual file or a pipe. 
___
Tags : #computer-architecture #operating-systems