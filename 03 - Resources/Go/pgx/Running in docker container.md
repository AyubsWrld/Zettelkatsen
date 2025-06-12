```bash
docker run --name <container name> \
	-e POSTGRES_USER=admin \
	-e POSTGRES_PASSWORD=<password> \
	-e POSTGRES_DB=<db-name> \
	-p <HOSTPORT:POSTGRESPORT> 
	-d postgres # Starts in detached mode 
```


#### Interacting with the container via psql cli
___

___
Tags : #golang #modules