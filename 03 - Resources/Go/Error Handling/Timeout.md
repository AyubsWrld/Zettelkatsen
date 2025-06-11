```go
func WaitForServer() error {
	const timeout  = 1 * time.Minute ; 
	deadline = 1 * time.Now().Add(timeout); 
	for tries := 0 ; time.Now().Before(deadline); tries++ {
		_ , err := http.Head(url) ;
		if err == nil {
			return nil  ; 
		}
		log.Printf("Server not responding"); 
		time.Sleep(time.Second << uint(tries)) // exponential back-off
	}
	return fmt.Errorf("Some error message") ; 
}
```
____
Tags : #programming #golang #language #go