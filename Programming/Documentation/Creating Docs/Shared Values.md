A [shared value](https://docs.swmansion.com/react-native-reanimated/docs/fundamentals/glossary#shared-value) is a driving factor of all your animations. You can think of it as a React state which is automagically kept in sync between the “JavaScript” and the “native” side of your app (hence the name). You create shared values using a `useSharedValue` hook:
```javascript
import { useSharedValue } from 'react-native-reanimated';
```
#### Manipulating Values
___
```javascript
import { Button, View } from 'react-native';
import Animated, { useSharedValue } from 'react-native-reanimated';

export default function App() {
  const width = useSharedValue(100);

  const handlePress = () => {
    width.value = width.value + 50;
  };

  return (
    <View style={{ flex: 1, alignItems: 'center' }}>
      <Animated.View
        style={{
          width,
          height: 100,
          backgroundColor: 'violet',
        }}
      />
      <Button onPress={handlePress} title="Click me" />
    </View>
  );
}
```