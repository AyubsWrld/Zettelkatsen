_____
#### System Calls Brief 

- **Procedure Calls**: A procedure call is a normal control flow operation that typically executes within the same privilege level (user or kernel mode), and does _not_ require switching from user mode to kernel mode. ( Function call ) 
- **System Calls**: A procedure call is a control flow operation that requires the CPU to enter Kernel Mode to execute. **System Calls** allow [[User Mode]] programs to hand over control of execution to the Kernel so that it may fulfil some operation. 
- **How System Calls Happen**: 
- ![[Pasted image 20250506094358.png]]
  
____
#### System Calls for Process Management

| Call                                  | Description                                    |
| ------------------------------------- | ---------------------------------------------- |
| pid = fork()                          | Create a child process identical to the parent |
| pid = waitpid(pid, &statloc, options) | Wait for a child to terminate                  |
| s = execve(name, argv, environp)      | Replace a process' core image                  |
| exit(status)                          | Terminate process execution and return status  |

---

📂 File Management

| Call                                 | Description                               |
| ------------------------------------ | ----------------------------------------- |
| fd = open(file, how, ...)            | Open a file for reading, writing, or both |
| s = close(fd)                        | Close an open file                        |
| n = read(fd, buffer, nbytes)         | Read data from a file into a buffer       |
| n = write(fd, buffer, nbytes)        | Write data from a buffer into a file      |
| position = lseek(fd, offset, whence) | Move the file pointer                     |
| s = stat(name, &buf)                 | Get a file’s status information           |

---

📁 Directory and File-System Management

| Call                           | Description                                  |
| ------------------------------ | -------------------------------------------- |
| s = mkdir(name, mode)          | Create a new directory                       |
| s = rmdir(name)                | Remove an empty directory                    |
| s = link(name1, name2)         | Create a new entry, name2, pointing to name1 |
| s = unlink(name)               | Remove a directory entry                     |
| s = mount(special, name, flag) | Mount a file system                          |
| s = umount(special)            | Unmount a file system                        |

---

🔧 Miscellaneous

| Call                     | Description                             |
| ------------------------ | --------------------------------------- |
| s = chdir(dirname)       | Change the working directory            |
| s = chmod(name, mode)    | Change a file’s protection bits         |
| s = kill(pid, signal)    | Send a signal to a process              |
| seconds = time(&seconds) | Get the elapsed time since Jan. 1, 1970 |
___

#### Windows vs. Unix Sys-calls #important 

| UNIX    | Win32               | Description                                 |
| ------- | ------------------- | ------------------------------------------- |
| fork    | CreateProcess       | Create a new process                        |
| waitpid | WaitForSingleObject | Can wait for a process to exit              |
| execve  | (none)              | CreateProcess = fork + execve               |
| exit    | ExitProcess         | Terminate execution                         |
| open    | CreateFile          | Create a file or open an existing file      |
| close   | CloseHandle         | Close a file                                |
| read    | ReadFile            | Read data from a file                       |
| write   | WriteFile           | Write data to a file                        |
| lseek   | SetFilePointer      | Move the file pointer                       |
| stat    | GetFileAttributesEx | Get various file attributes                 |
| mkdir   | CreateDirectory     | Create a new directory                      |
| rmdir   | RemoveDirectory     | Remove an empty directory                   |
| link    | (none)              | Win32 does not support links                |
| unlink  | DeleteFile          | Destroy an existing file                    |
| mount   | (none)              | Win32 does not support mount                |
| umount  | (none)              | Win32 does not support umount               |
| chdir   | SetCurrentDirectory | Change the current working directory        |
| chmod   | (none)              | Win32 does not support security (except NT) |
| kill    | (none)              | Win32 does not support signals              |
| time    | GetLocalTime        | Get the current time                        |

___
Tags : #operating-systems #system-calls