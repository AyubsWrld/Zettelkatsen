____
### Hello, World : 

```go
package main 

import ( 
	"fmt"
	// Other packages
)

func main(){
	fmt.Println( "Hello world " ); 
}

```

___

___
### Command-Line Arguments : 

This section utilizes command line arguments to illustrate loops and slices. 

##### Slices:
- Similar to how they are defined within python. Components of types with indices can be expressed using ` [ start : end ]` syntax. 
- os.Args returns a list of arguments as strings.

##### For Loops: 

For loops follow the convention 

```go 
for initialization; coniditon; post{ 
	// code goes here.
}
```

Ranged based for loops follow the convention 

```go 
for _,  arg := range os.Args[1:] { 
	// logic here
}
```

Range produces a pair of values, ` ( currentIdx , value ) `. We don't need this so we just simply throw it away using the `_` operator. Blank Identifier is usually used when we need the value to be defined we just wont don't use it. If a Value isn't used in go it causes compilation errors 

```go
package main 


// \n Logically seperates objects, idk if this is the case for lists like this 
import (
  "fmt"
  "os"
)

func main(){
  test := os.Args ;  // can also slice here so that we dont have to idx from 1 os.Args[1:]. 
  var output string; 
  for i := 1 ; i < len( test ) ; i++ {
    output += test[i] ; 
    output += " " ; 
  }
  fmt.Println( output ) ; 
}
```

____

### Finding Duplicate Lines :

### Animated GIFs

#### Fetching a URL

#### Fetching URLs Concurrently

#### A Web Server

#### Loose Ends
    
____
Tags : #programming #golang #language 