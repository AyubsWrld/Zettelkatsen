____
#### Processing Unit:

- **Processors** : Brain of the computer, Fetches instructions from memory and executes them. 
- **[[Registers]]**: Memory locations built into the CPU that ensure quick access and temporary storage. Registers are split into two different categories. General purpose registers and Special Registers. 
	- **[[Program Counter]]**: Contains a pointer to the location of the next instruction in memory to be fetched. 
	- **[[Stack Pointer]]**: Points to the top of the current stack in memory. 
	- **[[Program Status Word]]**: Program Status Word. This register contains the **Condition Code Bits**, which are set by comparison instructions, the CPU priority, the mode (user or kernel), and various other control bits. User programs may normally read the entire PSW but typically may write only some of its fields. The PSW plays an important role in system calls and I/O. A singular bit within the **PSW** delineates the mode which can either be in [[User Mode]] or [[Kernel Mode]]. 
- To obtain services from the operating system, a user program makes a [[System Call]], which traps into the kernel and invokes the operating system. The Trap instruction switches ( [[Context Switching ]] ) from user mode to kernel mode and starts the operating system. When the work has been completed, control is returned to the user program at the instruction following the system call.
- It is worth noting that computers have traps other than the instruction for executing a system call. Most of the other traps are caused by the hardware to warn of an exceptional situation such as an attempt to divide by 0 or a floating-point underflow. In all cases the operating system gets control and must decide what to do. Sometimes the program must be terminated with an error. Other times the error can be ignored (an underflowed number can be set to 0). Finally, when the program has announced in advance that it wants to handle certain kinds of conditions, control can be passed back to the program to let it deal with the problem

____
#### Memory: 

Modern computers use a **memory hierarchy** to balance speed, size, and cost. No single memory type is fast, large, and cheap all at once, so systems combine different types of memory across several layers:

 **1. Registers**
- **Speed:** Fastest (1 ns access time)
- **Capacity:** Smallest (<1 KB)
- **Location:** Inside the CPU
- **Managed by:** Software/programs
- **Use:** Immediate data processing
    
 **2. Cache**
- **Speed:** Very fast (1–10 ns access time)
- **Capacity:** Small (e.g., L1: 16 KB, L2: several MB)
- **Levels:** L1 (split into instruction/data), L2 (shared or per core)
- **Managed by:** Hardware
- **Use:** Temporarily holds frequently accessed data from main memory
- **Mechanism:** Uses cache lines (e.g., 64 bytes); cache hits are fast, misses go to RAM
- **Design Choices:** Replacement strategies, mapping of memory addresses, eviction rules
    
 **3. Main Memory (RAM)**
- **Speed:** Slower than cache (≈100 ns)
- **Capacity:** Large (1–8 GB typically)
- **Use:** General-purpose memory used by programs and OS
- **Volatile:** Loses content when powered off
    
 **4. Non-Volatile Memory**
- **ROM:** Factory-programmed; used for bootloaders or device control
- **EEPROM/Flash:** Can be rewritten; used in firmware updates, digital devices
- **CMOS:** Stores system time and configuration; battery-backed
    
 **5. Magnetic Disk (Hard Drive)**
- **Speed:** Much slower (≈10 ms average access time)
- **Capacity:** Very large (1–4 TB)
- **Mechanism:** Rotating platters, read/write heads on movable arms
- **Use:** Persistent storage for files and programs
- **Structure:** Data stored in sectors on tracks; tracks make up cylinders
  
 **6. Solid State Drives (SSD)**
- **Speed:** Faster than HDDs, slower than RAM
- **No moving parts:** Uses flash memory
- **Durability:** Can wear out with too many writes
 
**7. Virtual Memory**
- **Concept:** Allows programs to exceed RAM size by using disk storage as an extension
- **Managed by:** MMU (Memory Management Unit) inside the CPU
- **Operation:** Translates virtual addresses to physical ones in RAM
- **Context Switch Impact:** Requires flushing caches and remapping memory, which is costly

Caching and memory management significantly affect system performance. Efficient memory hierarchies help bridge the gap between the CPU's speed and slower storage types, but tradeoffs in cost and complexity require careful architectural design.


_____

#### I/O Devices: 
- Comprised of two distinct parts: a controller and the device itself. Controller provides an abstract interface to the operating system. The operating system is only concerned with interacting with the controller itself. The code required to facilitate this interaction differs from controller to controller and is referred to as the [[Device Driver]]. 
- Drivers must be put into the operating system so that they can run in [[Kernel Mode]]. Drivers can sometimes be ran outside of the operating system. There are three ways to add the driver into the kernel. 
	- Relink the kernel with the new driver then reboot the system. 
	- Make an entry in an operating system file telling it that it needs the driver and then reboot the system. At boot time, the operating system goes and finds the drivers it needs and loads them. 
	- the operating system can accept new drivers while running and install them on the fly without the need to reboot. ( [[Hot Pluggable Devices ]] ).
- Input and output can be done in three different ways.
	- **Busy Waiting**: The simplest way, a user program generates a [[System-Call]] which the User program then converts into a [[Procedure-Call]] to the appropriate driver. The driver then starts the I/O and sits in a tight loop continuously polling the device to see if it is done ( usually there is some bit that communicates whether the process is done or not ). When the I/O has completed, the driver puts the data (if any) where they are needed and returns. The operating system then re turns control to the caller. Although this ties up the CPU until the device has returned some data.   
	- The second method is for the driver to start the device and ask it to give an [[Interrupt]] when it is finished. At that point the driver returns. The operating system then blocks the caller if need be and looks for other work to do. When the con troller detects the end of the transfer, it generates an interrupt to signal completion.

_____
#### Buses: 
- See [[PCIe]] for potentially listing peripherals. 
  
___
#### Booting the Computer: 

- **[[Basic Input Output System]] ( BIOS )** is a small program stored on the motherboard which is the first thing that boots up when you switch your computer on. The BIOS contains low level I/O software to take input from peripherals like your mouse and keyboard as well as draw to your screen. 
	- The BIOS begins by scanning the PCIe and PCI busses to determine whether there exists any devices which have not been configured since the last time the BIOS ran. Any novel devices are then configured. 
	- The BIOS then determines the boot device by trying a list of devices stored in the [[CMOS memory]].
	- The [[Boot Order]] is usually configured by the user and stored within the CMOS. 
	- The first sector from the boot device is read into memory and executed. This sector contains a program that normally examines the partition table at the end of the boot sector to determine which partition is active. Then a secondary boot loader is read in from that partition. This loader reads in the operating system from the active partition and starts it.
	- The operating system then queries the [[BIOS]] to get the configuration information. For each device, it checks to see if it has the device driver. If it doesn't the user is prompted to install it themselves. After the operating system has all the required drivers it loads them into the [[Kernel]] and then the computer can display some GUI and prompt the user to Login. Then it initializes its tables, creates whatever background processes are needed, and starts up a login program or GUI.
___

#### Booting the computer:

___
Tags : #computer-architecture #operating-systems