CMake has a concept of scope. Variables set within a function are local to that function and are only accessible from within that function. Same goes for files within a sub directory. You can set a variable in the scope immediately above your current one with `PARENT_SCOPE` at the end.
___
Tags : #programming #cmake