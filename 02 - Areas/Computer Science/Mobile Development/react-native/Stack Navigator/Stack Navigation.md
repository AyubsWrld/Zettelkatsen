#### Utilization 
___
```javascript
import { NavigationContainer } from "@react-navigation/native";
import { createStackNavigator } from "@react-navigation/stack";
```

**Create a stack navigator**

```javascript
const Stack = createStackNavigator(); 
```

**Implementation**

```javascript
export default function App() {
  return (
    <NavigationContainer>
      <Stack.Navigator
        initialRouteName="Onboarding"
        screenOptions={{ headerShown: false }}>
        <Stack.Screen name="Onboarding" component={Onboarding} />
        <Stack.Screen name="Login" component={Login} />
        <Stack.Screen name="PopulateInfo" component={PopulateInfo} />
        <Stack.Screen name="Launch" component={Launch} />
        <Stack.Screen name="Signup" component={Signup} />
        <Stack.Screen name="Start" component={Start} />
        <Stack.Screen name="UsersList" component={UsersList} />
      </Stack.Navigator>
    </NavigationContainer>
  );
}
```


_____

Tags : #programming #react-native 