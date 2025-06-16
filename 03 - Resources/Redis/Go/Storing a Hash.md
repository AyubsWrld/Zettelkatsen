We can set hash map using a `[]string` type, `HSet`, and `HGet` routines.

```go
x := []string{
 "keyone", "valueone",
 "keytwo", "valuetwo",
 "keythree", "valuethree",
 "keyfour", "valuefour",
 "keyfive", "valuefive",
}

client.HSet( ctx, "test:1", x, 0).Result() // Returns # fields written ; 
client.HGet( ctx, "test:1", "keyone").Result() // Returns valueone; 

```
___
Tags: #redis 