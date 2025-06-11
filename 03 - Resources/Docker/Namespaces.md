**Namespaces** are a **Linux kernel feature** that provides **isolation** of system resources **per process or group of processes**. They essentially serve as scoped views of resources.

| Namespace Type | What It Isolates                                 | Docker Example                                                  |
| -------------- | ------------------------------------------------ | --------------------------------------------------------------- |
| `pid`          | Process IDs (what processes you can see)         | Each container only sees its own                                |
| `net`          | Network interfaces and IP stack                  | Container gets its own `eth0`                                   |
| `mnt`          | Mount points / filesystems                       | Container sees isolated `/` root                                |
| `uts`          | Hostname and domain name                         | Each container has its own name                                 |
| `ipc`          | Inter-process communication (e.g. shared memory) | Prevents interference via shared memory                         |
| `user`         | User and group IDs (UIDs/GIDs)                   | You can be root _in the container_ but unprivileged on the host |
| `cgroup`       | Not a namespace, but used to limit resources     | CPU, RAM, I/O limits per container                              |

___
Tags: #docker