#### Simple script to create a database connection 
___
```go
package main

import (
	"context"
	"fmt"
	"log"
	"github.com/jackc/pgx/v5"
)

func main() {
	ctx := context.Background()

	conn, err := pgx.Connect(ctx, "postgres://admin:secret@localhost:5432/mydb")
	if err != nil {
		log.Fatalf("Unable to connect to database: %v\n", err)
	}
	defer conn.Close(ctx)

	var greeting string
	err = conn.QueryRow(ctx, "SELECT 'Hello from Postgres!'").Scan(&greeting)
	if err != nil {
		log.Fatal(err)
	}

	fmt.Println(greeting)
}

```
___
Tags : #golang #modules