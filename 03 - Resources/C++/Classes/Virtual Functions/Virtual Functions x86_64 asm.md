#### C++ Code: 
___
```cpp
#include <iostream>

class Parent {
    public:
        virtual int sayHello() = 0;  
};

class Child : public Parent {
    public:
        int sayHello() override  {
            return 1 + 2;
        }
};

int main()
{
    Child x = Child();
    int y = x.sayHello();
}

```

#### ASM Output: 
___
```cpp
Child::sayHello():
        push    rbp // Two step instruction, decrement sp and put rbp there. 
        mov     rbp, rsp // Place memory address of rsp in rbp 
        mov     QWORD PTR [rbp-8], rdi // Compiler places this* ptr to obj in rdi 
        mov     eax, 3 // Move 3 into eax
        pop     rbp // pop rbp
        ret // return to caller 
```


#### Compiler does the de-virtualization for you. 
____
![[Pasted image 20250519185430.png]]

___
Tags : #programming #cpp 