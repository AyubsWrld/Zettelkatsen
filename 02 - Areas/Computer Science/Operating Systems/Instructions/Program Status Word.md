Holds critical information about the current status of the processor. 

When you write in C:

```c
if (a == b) { ... }
```

Behind the scenes:

1. The CPU compares `a` and `b` using `cmp` or `sub`
    
2. The **Zero Flag (ZF)** is set if they are equal
    
3. A conditional jump like `je` (jump if equal) checks ZF in the PSW
___
Tags : #computer-architecture #operating-systems #assembly