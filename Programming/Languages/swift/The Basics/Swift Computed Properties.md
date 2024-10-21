
Suppose we have  [[Swift Structures]]  wherein we wish to have a persons first name and their last name as well as their full name . This logic would not work . 

```swift
struct Person{
	let firstName :  String ; 
	let lastName  :  String ; 
	let fullName = "\(firstName) \(lastName)" ; 
}
```
this is due to the fact that  `firstName` and `lastName` are not known at the time of creating `fullName` . So instead we must utilize the constructor or we must utilize a Swift Computed Property . 

```swift
struct Person{
	let firstName :  String ; 
	let lastName  :  String ; 
	var fullName {	
		"\(firstName) \(lastName)" ; 
	}
	
}

```

____


Tags : #swift #language