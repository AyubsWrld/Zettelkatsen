#### Running the Postgres Container
___
```bash
docker run --name my-postgres -e POSTGRES_PASSWORD=mysecretpassword -d postgres
```

#### Connecting to the postgres container
___
```bash
docker exec -it my-postgres psql -U postgres
```

___
Tags: #docker