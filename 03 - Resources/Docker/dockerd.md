the docker [[Daemon]] is the **core background service that manages everything Docker does**. The docker CLI which we issue commands to like `docker build` and `docker run` is just a client. The requests get sent to the docker daemon running in the background ( or foreground using `sudo nohup dockerd > /dev/null 2>&1 &` ) does all the heavy lifting. We must start this Daemon process prior to doing anything using the `dockerd` command. 


```mermaid
graph TD
  User["You (Docker CLI)"]
  CLI["Docker CLI<br>(e.g., docker run)"]
  Daemon["Docker Daemon<br>(dockerd)"]
  API["REST API / Unix Socket"]
  Container["Containers"]
  Image["Images"]
  Network["Networks"]
  Volume["Volumes"]

  User --> CLI
  CLI --> API
  API --> Daemon
  Daemon --> Container
  Daemon --> Image
  Daemon --> Network
  Daemon --> Volume
```


___
Tags: #docker