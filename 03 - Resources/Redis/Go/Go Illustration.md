```go
package main

import (
    "context"
    "fmt"
    "github.com/redis/go-redis/v9"
)

var ctx = context.Background()

func main() {
    rdb := redis.NewClient(&redis.Options{
        Addr:     "localhost:6379",
        Password: "", // no password set
        DB:       0,  // use default DB
    })

    // SET key value
    err := rdb.Set(ctx, "mykey", "hello", 0).Err()
    if err != nil {
        panic(err)
    }

    // GET key
    val, err := rdb.Get(ctx, "mykey").Result()
    if err != nil {
        panic(err)
    }
    fmt.Println("mykey:", val)

    // GET non-existent key
    val2, err := rdb.Get(ctx, "missingkey").Result()
    if err == redis.Nil {
        fmt.Println("missingkey does not exist")
    } else if err != nil {
        panic(err)
    } else {
        fmt.Println("missingkey:", val2)
    }
}
```

___
Tags: #redis 