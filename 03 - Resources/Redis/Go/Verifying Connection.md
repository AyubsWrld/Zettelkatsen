We can verify a connection through setting a simple value and retrieving it. 

```go
ctx := context.Background()

err := client.Set(ctx, "foo", "bar", 0).Err()
if err != nil {
    panic(err)
}

val, err := client.Get(ctx, "foo").Result()
if err != nil {
    panic(err)
}
fmt.Println("foo", val)
```

- `Set`: Takes in a context and sets the value 
___
Tags: #redis 