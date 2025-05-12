References to DLLs required to execute the code. These references are embedded into the executable to be loaded at runtime. 
- Your executable contains an **Import Address Table (IAT)** and a **hint/name table**.
    
- When your program starts, the **Windows loader** uses this information to load the required DLLs (if not already loaded) and resolves the function addresses into the IAT.
____
Tags : #keeper #os #mingw