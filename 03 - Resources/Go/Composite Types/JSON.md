Basic types include the following 
```json 
boolean     true
number      -273.15
string      "She said \"hello\""
array       [ "gold", "silver", "bronze" ]
object      { 
				"year": 1980, 
				"event": "cherry", 
				"medals": ["gold", "silver", "bronze"] , 
			}
```

its quite easy to convert to and from this format. Converting a go data structure to JSON is called *marshalling*. Marshalling is done by `json.Marshall`. Can also use `json.MarshalIndent` to get it formatted nicely. 
![[Pasted image 20250514163854.png]]

The code above prints out: 
![[Pasted image 20250514164205.png]]

____
#### Field Tags
____
- A field tag is a string of metadata associated at compile time with the field of a struct.

```go
Year      int        `json:"released"` ; 
color     bool       `json:"released"` ; 
```

- They are conventionally interpreted as a space-separated list of key:"value" pairs. ( key = `json` , value = `:"value"` ). 

```go
{
	"Title": "Casablanca",
	"released": 1942,
	"Actors": [ "Humphrey Bogart", "Ingrid Bergman"
	]
}, 
```

*Casablanca above has omitempty on color and thus no json field is generated*. 

##### Omit empty
- Specifies that no json output should be generated in the case the field has the zero value for its type ( False here ). 

#### Marshalling vs. Unmarshalling. 
___
- **Marshalling**: Going from Go structs to JSON. Done utilizing json.Marshall. 
- **Unmarshalling**: Going from JSON to go Structs. Done utilizing json.Unmarshall. 

#### Unmarshalling Example 
___
The following is an example of converting some json into a go slice containing a struct with a single member, `Title`. 

```go
var titles []struct { Title   string }; 
if err := json.Unmarshal( data, &title ) ; err != nil {
	log.Fatalf( /* Do some error handling here */ ) ; 
}

fmt.Println( titles ) 
```
____
Tags : #programming #golang #language #go