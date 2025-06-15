A connection to a Postgres database can be initiated through the use of the `Connect` routine which takes a [[Context]] and Database URL as an argument. 

`conn , err := pgx.Connection( ctx.Background(), os.Getenv("DATABASE_URL")`

The database connection string can be in URL or key/value format. Both PostgreSQL settings and pgx settings can be specified here. In addition, a config struct can be created by [ParseConfig](https://pkg.go.dev/github.com/jackc/pgx/v5#ParseConfig) and modified before establishing the connection with [ConnectConfig](https://pkg.go.dev/github.com/jackc/pgx/v5#ConnectConfig) to configure settings such as tracing that cannot be configured with a connection string.

___
Tags : #golang #modules