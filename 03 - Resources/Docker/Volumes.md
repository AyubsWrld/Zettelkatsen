At the top layer of a Docker container is a **writable layer**, which allows changes to be made at runtime. However, by default, any data written to this layer is **not persisted** once the container is removed (`docker rm`). This becomes problematic when using databases inside containers—once the container is deleted, **all data changes are lost**.

Enter **Docker Volumes**. Docker volumes provide a way to persist data **outside** the container’s lifecycle. By mounting a volume, you link a persistent storage location to a directory inside the container. This is done using the `-v` flag when running the container.

```bash
docker run --name <container_name> \
  -e POSTGRES_USER=admin \
  -e POSTGRES_PASSWORD=secret \
  -e POSTGRES_DB=mydb \
  -v pgdata:/var/lib/postgresql/data \
  -p 5432:5432 \
  -d postgres
```

✅ Notes:

- Fixed typo: `POSTGRES_UESR` → `POSTGRES_USER`
    
- Volume syntax: `pgdata:/var/lib/postgresql/data` (was missing `/` before `var`)
    
- Added `-d` flag for running the container in detached mode
    
- `-p` maps host port 5432 to the container's 5432 (Postgres default)
    
___
Tags: #docker