> [!tip] **Description**
>  Compound value which groups multiple different data types together. Can be used to return multiple arguments from a function . 


```swift
//Type ( String , String , Int )

let values = ("One" , "Orange" , 3)

// Decomposing the tuple ..
let ( Amount , Fruit , Cost ) = values 
print("\(Amount) \(Fruit) Costs \(Cost) Dollars")

```

### Assigning Values 
___
We can assign values to a tuple utilizing the following ...

```swift 

let tupled = (ErrorCode : 200 , description : "Status Code" )

print(Tupled.ErrorCode) // Prints 200

```
### Accessing
___
We can utilize indexing in tandem with the `.` operator to retrieve data from a tuple . 

```swift
//Type ( String , String , Int )

let values = ("One" , "Orange" , 3)

// Decomposing the tuple ..
print(values.0) // Prints One

```



> [!tip] 
> If we only need a couple of the values within the tuple we can utilize ( _ ) where needed

```swift
let values = ("One" , "Orange" , 3)

// Decomposing the tuple ..
let (_ ,  Fruit , _ ) = values // Retrieves only fruit
print(Fruit)
```


____

Tags : #language #swift #programming