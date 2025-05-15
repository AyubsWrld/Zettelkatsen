Systems which expose a common interface which allow for interaction with the underlying operating system. For portability ( Unix-like ) 

> *"This system conforms to the POSIX standard — it exposes a standardized interface for programs to interact with the operating system."* 

- It implements **POSIX-defined system calls** (like `fork()`, `exec()`, `open()`, etc.)
- It behaves in a **predictable and standardized** way for things like:
    - file I/O
    - process management
    - threading (via `pthread`)
    - signals
    - shell utilities

##### All this to say it conforms to an implementation contract. 

----

Tags : #Networking #system-design 