Since redis utilizes a client server architecture with, our application as the client, we must connect to the server which can be done through implementing the following lines of code. 

```go
import (
	"context"
	"fmt"
	"github.com/redis/go-redis/v9"
)

func main() {    
    client := redis.NewClient(&redis.Options{
        Addr:	  "localhost:6379",
        Password: "", // No password set
        DB:		  0,  // Use default DB
        Protocol: 2,  // Connection protocol
    })
}
```

- `redis.NewClient`: Takes takes in a struct which configures the connection. 
	- `Addr` : Server port. 
	- `Password`: If set we can also supplement the password. 
	- `DB` : <mark style="background: #FF5582A6;">Currently Idk what this is.</mark> 
	- `Protocol` :  <mark style="background: #FF5582A6;">The connection protocol.</mark> 


#### Connection With Connection String
___
We can also parse a connection string and get back a `redis.Options` object and use that to initialize a connection. 

```go
opt, err := redis.ParseURL("redis://<user>:<pass>@localhost:6379/<db>")
if err != nil {
	panic(err)
}

client := redis.NewClient(opt)
```
___
Tags: #redis 