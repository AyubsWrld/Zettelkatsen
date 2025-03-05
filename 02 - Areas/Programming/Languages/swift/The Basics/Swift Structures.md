
Compound data type which can hold member variables of different types . the syntax is similar to how structures are created within C and C++ and the member variables are retrieved through the use of dot operators . 

### Syntax 

```swift

struct Person{  // Creating the struct
	let age  : Int    // Instanitate member variable datatpes . 
	let name : String  // Syonomous with int age , std::string name
}
```

### dot operator

used to retrieve the member variables of the struct 
```swift
let Ayub = Person(name : "ayub" , age : 32 ) ;  
print(Ayub.name) ;  // Prints ayub ; 
```

### Constructor 

Similar to python with the use of `self` to reference itself , we can use the constructor with this pointer to instantiate designated values or execute some code when the constructor is called . 

```swift
struct Macbook{  // Creating the struct	
	let Manufacturer: String   //  All macbooks are manufactured by apple
	let name : String 
	init(name : String){
	 self.name = name
	 self.Manufacturer = "Apple"
	 print("Created \(self.Manufacturer) Computer") ; // Runs when constructor is called
	}
}

```
____


Tags : #swift #language