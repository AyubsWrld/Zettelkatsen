A piece of software which can is loaded into memory once but can be utilized by multiple different processes. 

When an executable using a DLL is ran the following process ensues: 
- **Windows Loader inspects the Import Table**
- It sees `user32.dll` listed
- If `user32.dll` is **not already in memory**:
____
Tags : #keeper #os #mingw