> [!error] **Keep In Mind**
> Most arithmetic operations within swift must conform to having both operands be of the same type , otherwise the addition will not occur . 

```swift

let myDouble : Double = 0.3182 // Type double
let myInteger : Int = 3 // Assigned type int

let sum = myDouble + myInteger // Incorrect 
let sum = myDouble + Double(myInteger) // Correct
```


___

Tags : #swift #language 
