These are reserved for specific CPU/internal functions.

### 🔹 Examples:

| Register                   | Role                                                                           |
| -------------------------- | ------------------------------------------------------------------------------ |
| **`rip`**                  | Instruction pointer (next instruction)                                         |
| **`rflags`**               | Status flags (zero, carry, overflow, etc.)                                     |
| **`cr0`–`cr4`**            | Control registers (e.g., enable paging, interrupts)                            |
| **`cs`, `ds`, `ss`, etc.** | Segment selectors (in segmented memory models)                                 |
| **`msr_*`**                | Model-specific registers (used for performance counters, syscall entry points) |
| **`tr`**                   | Task register (used for hardware task switching, mostly legacy)                |
| **`tss`**                  | Task state segment (holds kernel stack info on context switch)                 |


___
Tags : #computer-architecture #operating-systems #assembly