`navigation.navigate` takes two parameters , first the page to navigate to , and secondly the props being passed to it . 

```javascript
navigation.navigate("PopulateInfo", {
  name: "John Doe",  // Pass parameters here
  age: 25
});
```

In the receiving prop we must use destructure the values 

```javascript 
function PopulateInfoScreen({ navigation, route }) {
	const { name, age } = route.params; // Destructure the props
```
____
Tags : #programming #navigation #react-native 