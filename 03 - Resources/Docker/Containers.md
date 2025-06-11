A Docker Container is a running instance of a Docker Image. It is **a lightweight, isolated, and portable environment** where your application runs.

#### Each Container
___
- **Is Created from an image**:
	- A **Docker Image** contains the relevant information to actually run the container. Think of it like the resources a process needs to run ( Like the filesystem for I/O, the application code to run, dependencies, etc ), with the container being an instance of said process. 
    
- Runs in its own isolated space
	- Runs as a process sandboxed from the rest of the operating system.
    
- Shares the host’s OS kernel
    
- Has its own filesystem, processes, network, and environment

You can create, start, stop, move, or delete a container using the Docker API or CLI. You can connect a container to one or more networks, attach storage to it, or even create a new image based on its current state.

#### Example
___
The following command runs an `ubuntu` container, attaches interactively to your local command-line session, and runs `/bin/bash`.

```console
$ docker run -i -t ubuntu /bin/bash
```

When you run this command, the following happens (assuming you are using the default registry configuration):

1. If you don't have the `ubuntu` image locally, Docker pulls it from your [[Configured Registry]], as though you had run `docker pull ubuntu` manually.
    
2. Docker creates a new container, as though you had run a `docker container create` command manually.
    
3. Docker allocates a read-write filesystem to the container, as its final layer. This allows a running container to create or modify files and directories in its local filesystem.
    
4. Docker creates a network interface to connect the container to the default network, since you didn't specify any networking options. This includes assigning an IP address to the container. By default, containers can connect to external networks using the host machine's network connection.
    
5. Docker starts the container and executes `/bin/bash`. Because the container is running interactively and attached to your terminal (due to the `-i` and `-t` flags), you can provide input using your keyboard while Docker logs the output to your terminal.
    
6. When you run `exit` to terminate the `/bin/bash` command, the container stops but isn't removed. You can start it again or remove it.

___
Tags: #docker