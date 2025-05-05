## ✅ **Top Prerequisites to Know Before Using Buildroot**

### 1. **Basic Linux Command Line**

You should be comfortable with:

- Navigating with `cd`, `ls`, `pwd`, `cp`, `mv`, `rm`
    
- Editing files (`nano`, `vim`, or `neovim`)
    
- Running shell scripts
    
- Installing packages via `apt`, `pacman`, or `dnf`
    

> If you’ve used Linux for development or coursework, you're probably good here.

---

### 2. **Linux Filesystem Layout**

Understand the purpose of:

- `/bin`, `/sbin`, `/lib`, `/usr`, `/etc`, `/tmp`, `/dev`, `/proc`
    
- The concept of **root filesystem (rootfs)** — the full OS environment Buildroot builds for you
    

---

### 3. **Cross Compilation Basics**

Buildroot compiles your OS **for a target architecture** (e.g., ARM, x86_64) on your dev machine (host).

You should know:

- What **cross-compiling** means
    
- That you need different toolchains for different targets (e.g., Raspberry Pi vs PC)
    
- That `gcc` for x86 is not the same as `arm-linux-gnueabi-gcc`
    

> You don’t have to write toolchains yourself — Buildroot does it for you — but understanding the concept is crucial.

---

### 4. **Kernel and Boot Basics**

You don’t need to be a kernel hacker, but you should know:

- What the **Linux kernel** is
    
- That **GRUB**, **Syslinux**, or **U-Boot** are bootloaders
    
- That `init` (or `systemd`, `busybox init`) starts your userland
    
- That you pass the `root=` parameter to the kernel to tell it where the OS is
    

---

### 5. **Make and Menuconfig Usage**

Buildroot is driven by `make` and its own `menuconfig` UI (same as Linux kernel config).

You’ll use:

```bash
make menuconfig      # to configure
make                 # to build
make clean           # to rebuild
```

### 6. **Disk Images and Mounting**

Know how to:

- Mount `.img` or `.iso` files using `mount` or loop devices
    
- Flash disk images using `dd` or tools like **Balena Etcher**
    
- Boot from USB or run an `.iso` in QEMU or VirtualBox
    

---

## ⚙️ Optional (But Helpful)

- Basic understanding of **init systems** (e.g., BusyBox vs Systemd)
    
- Familiarity with **QEMU** for testing OS images without real hardware
    
- Some **C or shell scripting** experience for adding startup scripts or modifying boot behavior
    

---

## ❌ You **Don't** Need:

- In-depth kernel hacking
    
- Manual package builds
    
- Full distro knowledge (like LFS requires)
    

---

### TL;DR Prerequisite Checklist

| Concept                         | Required?   |
| ------------------------------- | ----------- |
| Linux CLI                       | ✅ Yes       |
| Filesystem layout               | ✅ Yes       |
| Cross-compilation basics        | ✅ Yes       |
| Kernel/bootloader understanding | ✅ Yes       |
| `make` and `menuconfig` usage   | ✅ Yes       |
| Disk image mounting/flashing    | ✅ Yes       |
| Systemd/init knowledge          | ⚠️ Optional |
| C/bash scripting                | ⚠️ Optional |
| QEMU or VM familiarity          | ⚠️ Helpful  |

---

Would you like a learning roadmap or curated resources to get up to speed with these areas quickly?
____
Tags : #keeper #os