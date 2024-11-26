```javascript
// App.tsx
import React from 'react';
import 'react-native-gesture-handler';
import { NavigationContainer } from '@react-navigation/native';
import { createStackNavigator } from '@react-navigation/stack';
import Login from './pages/Login';
import Dashboard from './pages/Dashboard';

const Stack = createStackNavigator();

export default function App() {
  return (
    <NavigationContainer>
      <Stack.Navigator initialRouteName="Login" screenOptions={{headerShown : false}}>
        <Stack.Screen name="Login" component={Login} options={{ title: 'Login' }} />
        <Stack.Screen name="Dashboard" component={Dashboard} options={{ title: 'Dashboard' }} />
      </Stack.Navigator>
    </NavigationContainer>
  );
}```


____
Tags : #programming #mobile-development #react-native #navigation 