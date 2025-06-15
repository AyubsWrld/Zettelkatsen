#### Running the container
___
```bash
docker run --name <name> \
	-e POSTGRES_PASSWORD=<password> \
	-e POSTGRES_USER=<user_name>
	-e POSTGRES_DB=<dbname>
	-p <POSTGRESPORT|HOSTPORT> 
	-d postgres # For detached mode.
```

| Flag                   | Purpose                                                 |
| ---------------------- | ------------------------------------------------------- |
| `--name my-postgres`   | Names the container `my-postgres`                       |
| `-e POSTGRES_USER`     | Sets the default Postgres user                          |
| `-e POSTGRES_PASSWORD` | Sets the user’s password (required)                     |
| `-e POSTGRES_DB`       | Creates a default database                              |
| `-p 5432:5432`         | Maps local port 5432 → container port 5432              |
| `-d`                   | Runs the container in detached mode (in the background) |
| `postgres`             | Specifies the image to use (latest tag by default)      |
#### Connecting to the db through docker
___
`docker exec -it my-postgres psql -U admin -d mydb`

___
Tags: #docker