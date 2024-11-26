___
Logical equivalent to a `Templates ` within `C++` . It is utilized to create classes  , functions , or structs which can interact with multiple different `datatypes` . 

It is essentially like a wooden shape-board which has multiple different cut outs for interacting with different shapes . Based on what shape you have , you can place it into its corresponding hole . The Shape in this example is analogous to the `datatype` and the holes are analogous to the different outputs you get depending on what you `datatype` you enter . 

```swift
func displayData<T>(data: T){
  ...
}
```

### Example Function 
___
```swift
  // create a generic function
func displayData<T>(data: T) {
  print("Generic Function:")
  print("Data Passed:", data)
}

// generic function working with String
displayData(data: "Swift")

// generic function working with Int
displayData(data: 5)
```

### Example class
___
```swift
// create a generic class
class Information<T> {

  // property of T type
  var data: T // Datatype resolution operator 

  init (data: T) {
    self.data = data
  }

  // method that return T type variable
  func getData() -> T {
    return self.data
  }
}

// initialize generic class with Int data
var intObj = Information<Int>(data: 6)
print("Generic Class returns:", intObj.getData())

// initialize generic class with String data
var strObj = Information<String>(data: "Swift")
print("Generic Class returns:", strObj.getData())
```
____


Tags : #language #swift #programming