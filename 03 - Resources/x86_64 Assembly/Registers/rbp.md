#### Purpose
___
- Base register pointer. Used to store the base of the current stack frame. It is usually set when a routine is invoked by saving the current stack pointer in it.
  
- It’s used to mark the **start of the current function's stack frame**.
    
- It makes it easier to reference local variables and function arguments using **fixed offsets**, like `[rbp - 4]`, `[rbp + 8]`.

#### Example
___

##### Observe the following `C` code: 

```c
bool proc( int x, int y ){
	return x == y ; 
}

void set(){
	proc( 1, 2 ); 
}
```

##### The assembly looks like this: 

```x86asm
proc: 
	push rsb  
	mov rsb , rsp  // Sets current stack frame base pointer.
	mov DWORD PTR[-4], 1
	mov DWORD PTR[-8], 2
	mov eax , DWORD PTR[-4]
	cmp eax , DWORD PTR[-8]
	sete al
	pop rsb
	ret
set: 
```


```scss
High memory
────────────────────────────
... previous function’s stack ...
────────────────────────────
[rbp + 16] → argument 2 (if needed)
[rbp + 8 ] → return address
[rbp     ] → saved old rbp
[rbp - 4 ] → local variable x
[rbp - 8 ] → local variable y
[rbp - N ] → more local vars...
────────────────────────────
           rsp → bottom of current stack frame (grows downward)
Low memory
```
___
Tags : #x86_64_asm