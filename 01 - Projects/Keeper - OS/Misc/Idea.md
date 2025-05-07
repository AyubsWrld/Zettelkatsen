A secure, bootable sandbox OS for safe, verifiable testing environments.
#### Requirements :
____
- Supports common x86_64 and ARM64 architectures
	- Build for **x86_64 first**, then target ARM later
- No persistent storage. Bootable via ISO, USB, or dedicated partition. Removable without residue.
	- Reboot → Done → Wipe → Nothing remains
- Should provide minimal strain to actually get it up and running. 
	- No BIOS/UEFI tinkering if avoidable
	- Should be easily bootable and once done, easily removeable. 
	- Suggest pairing with clear onboarding materials or automated scripts 
	- Could even use Ventoy or UEFI boot menu for plug-and-run testing
- Supervisor should be given complete access to ALL the processes running on the machine. Given that it is sandboxed this should no be a problem. 
	- Root-level access for supervisor only
	- Full logging of system calls, process trees, memory usage, etc.
- Everything should be sandboxed so that it is not invasive for the user. 
	- Read-only root filesystem (`SquashFS`, OverlayFS)
	- No package managers or `curl`, `wget`
	- DNS/NIC blocking or firewall rules to block all outbound access
- The memory should be immutable, no access to downloading software. 
- Should be able to run on user partitions as opposed to needing a physical device. 


____
Tags : #keeper #os