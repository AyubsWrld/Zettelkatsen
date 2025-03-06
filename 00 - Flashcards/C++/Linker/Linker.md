___
Tags: #cpp #progarmming 
___

What is the primary purpose of a linker in C++? ;; The primary purpose of a linker is to connect different object files together and resolve references to functions, variables, and other identifiers across these files.
<!--SR:!2025-03-07,1,230-->

What happens during the linking process in C++? ;; During the linking process, the linker combines object files, resolves external references, and creates an executable or a library.
<!--SR:!2025-03-09,3,250-->

What is an "external reference" in the context of linking? ;; An external reference is a function, variable, or symbol that is declared but not defined in the current file, requiring the linker to resolve its definition from another file.
<!--SR:!2025-03-07,1,230-->

What is the difference between "static linking" and "dynamic linking"? ;; Static linking includes all the required code into the final executable at compile-time, while dynamic linking defers the inclusion of code to runtime by linking to shared libraries.
<!--SR:!2025-03-07,1,230-->

**What is a "linker error" in C++? ;; A linker error occurs when the linker cannot resolve references, such as when it cannot find the definition for a function or variable declared in another file.**
<!--SR:!2025-03-07,1,230-->

What is a "symbol" in the context of linking? ;; A symbol refers to a function, variable, or object that is referenced or defined in the code, and the linker resolves these symbols to match declarations with their definitions.
<!--SR:!2025-03-09,3,250-->

What is a "relocation" in linking? ;; Relocation is the process of adjusting addresses in object files to match the location where the code or data is placed in memory during the linking process.
<!--SR:!2025-03-07,1,230-->

What is a "symbol table" used for during linking? ;; A symbol table is a data structure used by the linker to keep track of all the symbols (functions, variables, etc.) and their addresses during the linking process.
<!--SR:!2025-03-07,1,230-->

What is an "object file" in C++? ;; An object file is the output of the compiler after compiling a source file. It contains machine code but needs to be linked with other object files to create a final executable.
<!--SR:!2025-03-07,1,230-->

What happens if the linker cannot find a definition for an identifier in the program? ;; If the linker cannot find a definition for an identifier, it will issue an error indicating an unresolved external symbol or reference.
<!--SR:!2025-03-09,3,250-->

What is a linker? ;; A linker is a program that combines object files into a single executable or library, resolving references to functions, variables, and other symbols across different files.
<!--SR:!2025-03-07,1,230-->