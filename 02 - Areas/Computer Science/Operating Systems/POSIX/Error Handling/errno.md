Global variable the operating system utilizes to write the result of a system call when it errors out. We can utilize `strerror()` passing in `errno` to get the readable representation of the error. 

_____
Tags : #operating-systems #posix #errors 