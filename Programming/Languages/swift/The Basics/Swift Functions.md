
### Syntax 
```swift
func functionName(arguments) -> returnType{
	codeblock  
	codeblock  
	codeblock  
}
```
#### Arguments
Functions allow you to pass in arguments which are local to that function block . when passing in the arguments its type and return type must be specified as well . 
```swift 
func testArguments(value : Int) -> Int {
	return value + 1 //Impicitly returns if return is not specified . 
}
```

#### External Arguments
Without _ we must explicitly include which argument is which . Suppose we have the function *get Sum* which returns the sum of two arguments . 

```swift
func getSum(lhs : Int , rhs : Int ) -> Int {
    return lhs + rhs 
}
```

If we ever wish to call getSum we must always explicitly delineate which argument is which when calling it . 

```swift 
getSum(lhs : 2 , rhs : 3) ;
```

If we add and underscore we can refrain from ever having to do this . 

```swift
func getSum(_ lhs : Int , _ rhs : Int ) -> Int {
    return lhs + rhs 
}
```

```swift 
getSum(lhs : 2 , rhs : 3) ;
```

# Default Values

Functions can receive default values in the cases wherein they are not passed arguments 

### Syntax
```swift
@discardableResult
func getFullName(_ fname: String = "Ayub" , _ lname : String = "Mohammed" ) -> String{
	return "\(fname) \(lname)" ; 
}

print(getFullName()) ; 
```
___

Tags : #swift #language 