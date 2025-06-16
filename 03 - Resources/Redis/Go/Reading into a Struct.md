We can use tagged struct fields to store structs.

```go
x := []string{
	"email" , "iwantwraiths@gmaail.com"
	"password" , "idkthisisntarealpassword"
	"username" , "compilerclansman"
}

client.HSet(ctx, "user:1", x, 0) ;

type User struct{
	email    string   `redis:"email"`
	password string   `redis:"password"`
	username string   `redis:"username"`
}

y := &User{} ; 

client.HGetAll(ctx, "user:1").Scan(y) ; 

fmt.Println( y.email ) ; 
```

___
Tags: #redis 