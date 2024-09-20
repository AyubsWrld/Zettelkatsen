#### Import Dependencies 
___
```javascript
import Animated, { useSharedValue, useAnimatedStyle  , withSpring } from 'react-native-reanimated';
```
#### Create shared Value
___
`useSharedValue` allows us to keep track of all the animations. 
```javascript
const width = useSharedValue(initial value) ; 
```


#### Wrap Values in Animated.View Container
___

```html 
<Animated.View style={animatedStyle}>
    <TouchableOpacity style={[styles.button]} onPress={handlePress}>
    <Text style={styles.buttonText}></Text>
    </TouchableOpacity>
</Animated.View>
```

#### Include animated Style within the Styles
___
```javascript
const animatedStyle = useAnimatedStyle(() => {
	return {
      width: width.value,
    };
  });

```
___
Tags : #react-native #language #programming #mobile-development 
