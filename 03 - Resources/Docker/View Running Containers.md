We can view running containers using the `docker ps` command. 

```bash
docker ps 
```

```bash
 CONTAINER ID   IMAGE                      COMMAND                  CREATED          STATUS          PORTS                      NAMES
 a1f7a4bb3a27   docker/welcome-to-docker   "/docker-entrypoint.â¦"   11 seconds ago   Up 11 seconds   0.0.0.0:8080->80/tcp       gracious_keldysh
```

To view stopped process we can supplement with the `-a` flag. 

```bash
docker ps -a 
```

___
Tags: #docker