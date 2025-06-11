#### How Layering Works
____


[[Images]] consist of immutable file system that are made in layers. An example of adding layers to an image could include: 

1. The first layer adds basic commands and a package manager, such as apt.
2. The second layer installs a Python runtime and pip for dependency management.
3. The third layer copies in an application’s specific requirements.txt file.
4. The fourth layer installs that application’s specific dependencies.
5. The fifth layer copies in the actual source code of the application.
![[Pasted image 20250610161233.png]]

There is a sequential aspect to this, so it's best not to put the cart in front of the horse for this.

This gives us the opportunity to reuse layers which applications share. For example two applications may require a Debian base and python and pip whereas they may differ in application code. 
___
Tags: #docker