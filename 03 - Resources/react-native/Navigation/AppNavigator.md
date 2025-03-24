
```tsx
import { NavigationContainer } from "@react-navigation/native" ;
import { createNAtiveStackNavigator } from "@react-navigation/native-stack" ;

export type AppStackParamList = {
	Home: undefined 
	Login : undefined 
	Profile: undefined 
}

const Stack = createNativeStackNavigator<AppStackParamList>() ; 

export function AppNavigator() 
{
	return(
	<NavigationContainer>
		<Stack.Navigator initialRouteName="Login" screenOptions={{headerShown : false}}	
			<Stack.Screen name="name" component={HomeScreen}/> 
		</Stack.Navigator> 
	</NavigationContainer>
	)
}


```


___
Tags : #react-native #naviagation 