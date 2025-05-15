Used for storing basic instructions and results produced by the [[Arithmetic Logic Unit]] as well as passing arguments to functions or syscalls. 
### 🧾 Example (x86_64):

| Register   | Typical Use                               |
| ---------- | ----------------------------------------- |
| `rax`      | Return value (accumulator)                |
| `rbx`      | Base register (caller-saved)              |
| `rcx`      | Counter register (looping)                |
| `rdx`      | Data register (used for division/mult.)   |
| `rsi`      | Source for memory operations              |
| `rdi`      | Destination for memory operations         |
| `rsp`      | Stack pointer                             |
| `rbp`      | Base/frame pointer (used in stack frames) |
| `r8`–`r15` | Extra registers (64-bit mode only)        |


___
Tags : #computer-architecture #operating-systems #assembly