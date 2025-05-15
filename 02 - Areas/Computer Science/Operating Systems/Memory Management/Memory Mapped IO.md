Peripherals have device registers which allow for interfacing with the peripheral ( Memory storage locations on the peripheral ) . We can utilize these to write and read data from. 

Memory Mapped I/O essentially allows us to reference these peripherals through the use of addresses as opposed to utilizing special instructions. The **CPU sees these device registers as specific memory addresses** (e.g., `0xD0000000`), thanks to MMIO.

```c
*(volatile uint32_t*)0xD0000000 = 1;
```

> the last bit allows caching to be disabled for the page. This feature is important for pages that map onto device registers rather than memory. If the oper ating system is sitting in a tight loop waiting for some I/O device to respond to a command it was just given, it is essential that the hardware keep fetching the word from the device, and not use an old cached copy. With this bit, caching can be turned off. Machines that have a separate I/O space and do not use memory-map ped I/O do not need this bit.

____
Tags : #methodologies #programming 