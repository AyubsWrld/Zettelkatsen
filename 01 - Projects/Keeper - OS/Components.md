
| Component                   | Description                                                    | Tools/Technologies                                      |
| --------------------------- | -------------------------------------------------------------- | ------------------------------------------------------- |
| 🧠 **Base OS Layer**        | Minimal Linux OS that boots quickly and runs entirely from RAM | [Buildroot](https://buildroot.org/)                     |
| 🔐 **Sandboxing Layer**     | Prevents access to host OS and system devices                  | Unprivileged user, AppArmor/seccomp, mount restrictions |
| 🧳 **Supervisor Interface** | Built-in tool or shell with full system visibility             | `htop`, `ps`, custom dashboard, or audit logs           |
| 🧼 **Filesystem Layout**    | Read-only base, temporary RAMFS overlay                        | `SquashFS`, `OverlayFS`, `tmpfs`                        |
| 🔌 **Boot Mechanism**       | GRUB menu entry or USB image, boots directly into Keeper       | GRUB, ISOLINUX, or EFI stub                             |
|                             |                                                                |                                                         |
| 🚫 **Access Controls**      | No networking, no package managers, no external storage mounts | iptables, no `wget`/`curl`, no auto-mount               |
| 🚀 **Distribution Format**  | USB image or ISO file, easy to flash/run                       | `.img` or `.iso` via Balena Etcher, Rufus               |
|                             |                                                                |                                                         |
____
Tags : #keeper #os