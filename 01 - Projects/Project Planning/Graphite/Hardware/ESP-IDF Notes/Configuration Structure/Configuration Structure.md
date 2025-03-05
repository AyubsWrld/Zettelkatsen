Initialization ( `_init()` ) , configuration ( `_config()` ) , Installation ( `_Install()` ) functions take a [[Configuration Structure Pointer]] as an argument . 

These functions never store the pointer to the configuration structure, so it is safe to allocate the structure on the stack.
____
Tags : #programming #computer-architecture #graphite