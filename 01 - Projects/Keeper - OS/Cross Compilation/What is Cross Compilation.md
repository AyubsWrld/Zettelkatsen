A cross compiler generates an executable for a target platform utilizing the source code generated on the hosts platform. This is because the binary instructions which are executed for syscalls differ between operating systems ( Although the syscalls themselves conform to whatever ISA the machine is running on ). Other reasons include: 

| What It Handles                          | How                                       |
| ---------------------------------------- | ----------------------------------------- |
| Syscall mappings                         | Links against correct headers and stubs   |
| Calling conventions (stack/register use) | Applies target’s ABI rules                |
| Linking to OS-specific libraries         | Uses target `.lib`, `.a`, or `.dll` stubs |
| Generating correct binary format         | ELF for Linux, PE32/PE64 for Windows      |

For example when I make a call to Malloc(), the syscalls and what occurs when I call differ significantly between target Operating Systems. 
____
Tags : #keeper #os #cross-compilation