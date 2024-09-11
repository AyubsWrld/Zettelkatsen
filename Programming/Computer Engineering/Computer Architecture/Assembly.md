- **Low-Level Programming Language**: Assembly language is a low-level programming language that is closely related to machine code, the native language of a computer's central processing unit (CPU).
- **Human-Readable Format**: Unlike binary machine code, assembly language uses human-readable mnemonics and symbols to represent instructions and data.
#computer-architecture 
#### Key Characteristics

- **Processor-Specific**: Assembly language is specific to a particular computer architecture and processor. Different CPUs have different assembly languages.
- **Direct Hardware Control**: Allows programmers to write instructions that directly control the hardware. This provides fine-grained control over system resources.
- **Efficient and Fast**: Code written in assembly language can be very efficient and fast, as it is often optimized for the specific hardware it runs on.

#### Basic Components

- **Mnemonics**: Human-readable instruction codes that represent machine-level instructions (e.g., MOV, ADD, SUB).
- **Operands**: The data or addresses on which the instructions operate. Operands can be registers, memory locations, or immediate values.
- **Registers**: Small storage locations within the CPU used to hold data temporarily. Examples include AX, BX, CX, and DX in x86 assembly.
- **Labels**: Named locations in the code used for branching and looping (e.g., start, loop1).
- **Directives**: Instructions for the assembler itself, used for defining data, segments, and other structural elements (e.g., .data, .code).

#### Common Instructions

- **Data Movement**: MOV (move data), PUSH (push data onto stack), POP (pop data from stack).
- **Arithmetic**: ADD (addition), SUB (subtraction), MUL (multiplication), DIV (division).
- **Logical Operations**: AND, OR, XOR, NOT.
- **Control Flow**: JMP (unconditional jump), JE/JZ (jump if equal/zero), JNE/JNZ (jump if not equal/not zero), CALL (call subroutine), RET (return from subroutine).
- **Comparison**: CMP (compare two values), TEST (bitwise comparison).
## Fetch
1) Load MAR with the contents of the PC, and simultaneously increment the PC
2) Check if data is stored within that memory address . This results the instruction to be placed in the MDR 
3) After the instruction is moved from the MDR into the Instruction register within the control unit it decodes it 
## Decode 
1) Control unit decodes the data within the MDR 
## Evaluate address 
1) Computes the address of the memory location that is needed to process the instruction 
## Fetch Operands 
1) Load MAR with the address calculated in evaluate address
2) Read memory , placing source operand in MDR
ķ## Execute
1) Within ALU perform the operation
## Store
1) The store result phase writes to the designated destination . 
2) One store result is completed, a new instruction cycle starts (with the fetch Phase) . 
## Changing the Sequence of Execution 
We can change the the Pointer to the next instruction utilizing *jump* commands so that our programs are not strictly performed sequentially . *jump* <Address> 

#programming #computer-architecture 