
___
Tags: #cpp #progarmming 
___

What does this code output ![[Pasted image 20250307225343.png]]? ;; 4


When we initialize a `int x = 4` , how many bytes in contiguous memory is allocated to x ? ;; 4 bytes 


Supposed we initialize `int x = 4`, then we initialize `int y = 3` right after , if x starts at `0x200` , what memory address will `y` be assigned and where will `y` end ? ;; x will end @ `0x203` and y will start @ `0x204` and end at `0x207` . 

What is an integer type? ;; and integer type is a number without a fractional part 

What is an Integral type ? ;; an integer-like type , `char` , `bool` . 

What does the data type do ? ;; It tells the compiler how to treat the data stored within the memory address . 

What is void ? ;; An incomplete type which represents no type  . 

What is an incomplete type ? ;; a type that has been declared but not yet defined . the compiler knows of the type but does not yet know how much memory to allocate for that type . 


How many bits are in a byte ? ;; 8 bits 

What does byte addressable mean ? ;; It means we can address every byte separately . 

What is the minimum addressable unit of memory ? ;; A byte ( 8 or 4 bits ) 

What is the size of a Boolean ? ;; 1 byte

What is the size of a char ? ;; 1 byte

what is the size of a short ? ;; 2 bytes 

How many numbers can you represent with a short ? ;; $2^{16}$

How large is an int ? ;; 4 bytes 

How large is an long ? ;; 4 or 8 bytes 

How large is an long long ? ;; 8 bytes 

How large is a floating point number? ;; 4 bytes 

How large is a double ? ;; 8 bytes ?? 

How large is a pointer and why is it that large ? ;; A pointer stores an address . Since the address space on a 64bit machine is 64bits -> it implies that to store a pointer to any specific address you need to store 8 bytes ( 64 bits ) . 

What would the range of a 5-bit signed integer be? ;; ( -16 , 15 ) 

What is the range of an unsigned int ? ;; since an integer is 4 bytes , and unsigned integer is $2^{32}$ or 0 to 4294967295 . 

Why should we refrain from utilizing unsigned integers ? ;; We should refrain from using unsigned integers as the overflow caused by regular operations likes subtraction may lead to unexpected behavior . 

What does this code snippet output ![[Pasted image 20250307235012.png]] ;; 3 

