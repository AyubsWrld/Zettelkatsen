As with any task we need instructions as well as an entity to carry out these instructions . The task in this case is the program which is a set of instructions we would like the computer to carry out , and we also need a computer which will be carrying out the instructions . 

___

**The ALU processes data** elements of a fixed size, known as the word length, which varies by computer architecture. Most modern microprocessors in PCs and workstations have a word length of 64 bits or 32 bits, while the LC-3 has a word length of 16 bits.

To perform operations like ADD, the ALU receives two words as input and produces a single word as output. Microprocessors in smartphones also typically have 64-bit word lengths, while those in inexpensive applications can have word lengths as small as 16 or 8 bits.

Temporary storage close to the ALU, such as registers, is essential for storing intermediate results to avoid slower memory access times. The LC-3 has eight 16-bit registers, while current microprocessors usually contain 32 registers of 32 or 64 bits each, with some having special-purpose registers of 128 bits for specific needs.

Sort of like when you give someone instructions you want to make sure that your instructions are finite and are in a specific language , these instructions may vary from person to person . 

**Temporary Storage** 
- Registers close to the ALU which serve as temporary storage for data that will be used soon , since writing to memory is more costly because we have to write enable the flip flops and set the bits , storing the data within *Registers* is a lot less costly . ( (A + B) $\times$ C , the result of A + B is stored within a register to be later multiplied by C) . 
- The size of the registers = the word size of the architecture .  

**Input and Output**
- Peripherals for data to go in and come out of the computer such as Keyboards , Monitors  . 

**Control Unit**
- The control unit acts like the conductor of an orchestra, coordinating all parts of the computer to work together smoothly. It keeps track of where we are in the process of executing a program and each instruction.
- The control unit uses an instruction register to hold the current instruction being executed and a program counter (PC) to hold the address of the next instruction. Although "instruction pointer" might be a more descriptive name, the term "program counter" remains widely used.

___
**Instruction Processing** 
The central idea in the von Neumann model of computer processing is that the program and data are both stored as sequences of bits in the computer’s memory, and the program is executed one instruction at a time under the direction of the control unit.

- Instruction comprises OPCODE (What the operation does) and OPERANDS (Where the operation is applied to) .
- Instructions are equivalent to the word size of the computer , So for LC-3 Architecture , the instruction is 16bits long , with the OPCODE occurring within the first [15 : 12] (4bits) of the instruction . The remaining bits are used to delineate where the operands are . 
**Instruction Steps** 
### Instruction Processing Phases

#### 1. FETCH
- The FETCH phase obtains the next instruction from memory and loads it into the instruction register (IR).
- Steps:
  1. Load the MAR with the contents of the PC and simultaneously increment the PC.
  2. Interrogate memory, resulting in the instruction being placed in the MDR.
  3. Load the IR with the contents of the MDR.
- Each step is directed by the control unit and takes a specific number of clock cycles.

#### 2. DECODE
- The DECODE phase interprets the instruction to determine the required action.
- In the LC-3, a 4-to-16 decoder identifies which of the 16 opcodes is to be processed.
- The output line corresponding to the opcode is asserted, and the remaining bits identify what else is needed for processing.

#### 3. EVALUATE ADDRESS
- This phase computes the address of the memory location needed for the instruction.
- For example, the LD instruction calculates the address by sign-extending bits of the instruction and adding it to the current PC value.
- Not all instructions require this phase (e.g., ADD and AND instructions use operands from registers).

#### 4. FETCH OPERANDS
- This phase obtains the source operands needed for the instruction.
- For an LD instruction, it involves loading the MAR with the calculated address and reading memory to place the source operand in the MDR.
- For an ADD instruction, it consists of obtaining source operands from registers.

#### 5. EXECUTE
- The EXECUTE phase carries out the instruction's operation.
- In the ADD example, this phase performs the addition in the ALU.

#### 6. STORE RESULT
- The final phase writes the result to its designated destination.
- For ADD instructions, many computers, including the LC-3, perform this during the EXECUTE phase.
- Once completed, the control unit begins the next instruction cycle, starting with the FETCH phase.

**General Notes**
- The PC is updated during the FETCH phase to point to the next instruction.
- Not all instructions require all six phases; some may combine phases (e.g., the LC-3 ADD instruction does not need separate EVALUATE ADDRESS or STORE RESULT phases).
- The instruction cycle continues until interrupted or the program finishes execution.


---

Tags : #computer-architecture 