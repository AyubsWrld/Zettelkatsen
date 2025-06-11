First, and most common, is to propagate the error ,so that a failure in a subroutine becomes a failure of the calling routine.

Second, for errors that represent transient or unpredictable errors, it makes sense to wait a little bit and then retry the operation again. For example: 

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

Third, if progress is impossible, the caller can print the error and stop the program gracefully, although this course of action should be reserved for the main package of a program. 

Fourth, in some cases, it’s sufficient just to log the error and then continue, perhaps with reduced functionality. Use `log.Fatalf` to get the time and date of the error as well. 


Error handling in Go has a particular rhythm. After checking an error,failure is usually dealt with before success. If failure causes the function to return, the logic for success is not indented within an else block but follows at the outer level.
____
Tags : #programming #golang #language #go