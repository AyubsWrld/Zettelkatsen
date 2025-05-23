In x86-64 assembly, the `call` instruction is used to invoke a function. It pushes the return address onto the stack and then jumps to the function's entry point. The return address is the instruction following the `call` instruction. After the function finishes executing, the `ret` instruction pops the return address from the stack and jumps back to the caller's code.
___
Tags : #x86_64_asm