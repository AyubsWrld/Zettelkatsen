
Great question. **Procedure Linking Information** is tightly related to how **function calls (`call`) are resolved** — especially for functions in **other translation units** or **shared libraries**.

Let’s unpack it in the context of **x86-64 assembly** and the **linker/loader process**.

---

### ✅ What is **Procedure Linking Information**?

It refers to metadata and mechanisms used by the **linker and loader** to resolve **external function calls**, especially:

- Functions defined in **other `.o` files**
    
- Functions defined in **dynamic/shared libraries (.so/.dll)**
    

---

### 🧠 Context: The `call` Instruction

In x86-64 assembly, `call` can work in **two main ways**:

#### 1. **Direct call to a known address**

```asm
call my_function      ; resolved at compile/link time
```

#### 2. **Indirect call (via a pointer)**

```asm
call QWORD PTR [rip + offset]  ; used for dynamically linked functions
```

When the callee is **not known at compile time** (e.g. in another library), the compiler generates **Procedure Linking Information** so that:

- The **linker** knows what symbols need to be resolved
    
- The **dynamic linker/loader** can patch the call at runtime (for dynamic linking)
    

---

### ⚙️ Mechanisms used for this:

#### 🧩 1. **PLT (Procedure Linkage Table)**

- A table of **jump stubs**
    
- Used to call functions in shared libraries
    
- `call` instructions for external functions actually call **entries in the PLT**
    

#### 🧩 2. **GOT (Global Offset Table)**

- A table of **addresses**, one for each external symbol
    
- PLT entries use GOT to look up the _actual_ runtime address
    

#### 🧩 3. **Relocation Entries**

- Metadata saying: “The linker must resolve the address of `printf` here”
    
- Stored in ELF sections like `.rela.plt` or `.rela.dyn`
    

---

### 📌 Example: Calling `printf`

Your C++ code:

```cpp
printf("Hello\n");
```

May result in assembly like:

```asm
call printf@PLT  ; indirect call using the PLT entry for printf
```

Which jumps to a PLT stub:

```asm
jmp QWORD PTR [rip + offset_to_printf@GOT]
```

Initially, the GOT entry for `printf` points back into the PLT’s **resolver stub**, which then asks the **dynamic linker** to find the real `printf` and patches the GOT.

After the first call, future calls go straight to the correct address.

---

### 🔍 Why is this useful?

- You can link against shared libraries **without knowing their addresses** at compile time.
    
- You can dynamically load functions and libraries at runtime.
    
- It's part of **Position-Independent Code (PIC)** for shared object (.so) files.
    

---

### ✅ Summary

> **Procedure Linking Information** refers to the data and mechanisms (like PLT, GOT, and relocation tables) that enable the `call` instruction in x86-64 to resolve function addresses **across translation units and dynamic libraries**.

It’s critical for dynamic linking, lazy binding, and position-independent code.

Let me know if you’d like to trace through how a `call printf` is resolved in a live binary using tools like `objdump`, `readelf`, or `gdb`.
___
Tags : #x86_64_asm