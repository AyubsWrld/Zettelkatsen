You can store structs using JSON:

```go
type User struct {
    Name string
    Age  int
}

user := User{"Ayub", 24}
b, _ := json.Marshal(user)
rdb.Set(ctx, "user:ayub", b, 0)

```

to read: 

```go
val, _ := rdb.Get(ctx, "user:ayub").Result()
var u User
json.Unmarshal([]byte(val), &u)
```
___
Tags: #redis 