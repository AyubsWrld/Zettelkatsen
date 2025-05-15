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

#### Field Tags: 


____
Tags : #programming #golang #language #go