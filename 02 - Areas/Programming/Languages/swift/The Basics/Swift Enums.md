
Similar to enums present within other languages . Enums are used to link associated data with one another . for example , we can have an Animals Enum or an error Enum to link different animals or error codes together. 

```swift
enum Animal{
	case Bird ;
	case Dog ;
	case Cat ;
}

let Beerus = Animal.Dog  ; 

if Beerus == Animal.Cat{
    print("Beerus is a cat")
}
else{
    print("Beerus is not a cat")
}
```


### Associated Values
We can also have associated values with the actual enums . For example we know that `Beerus` is a cat , but what kind of cat is `Beerus` ? 

____


Tags : #swift #language