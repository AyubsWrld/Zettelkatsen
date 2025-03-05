This code defines the **main navigation structure** for the **React Native app** using **React Navigation**. It sets up the **navigation stack**, defines the available screens, and applies **authentication-based navigation logic**.
### **How This Fits into `WelcomeScreenProps`**
Earlier, we analyzed:
```tsx
interface WelcomeScreenProps extends AppStackScreenProps<"Welcome"> {}
```
- `AppStackScreenProps<"Welcome">` ensures `WelcomeScreenProps` has the correct **navigation props**.
- This type comes from:
  ```tsx
  export type AppStackScreenProps<T extends keyof AppStackParamList> = NativeStackScreenProps<
    AppStackParamList,
    T
  >
  ```
  - **`AppStackScreenProps` extracts navigation props** for a given screen (e.g., `"Welcome"`).
  - **`AppStackParamList` defines all possible screens**, meaning `WelcomeScreenProps` gets type safety.

---
### **Breaking Down the Navigation Code**
---

### **1. Importing Dependencies**
```tsx
import {
  NavigationContainer,
  NavigatorScreenParams,
} from "@react-navigation/native"
import { createNativeStackNavigator, NativeStackScreenProps } from "@react-navigation/native-stack"
import { observer } from "mobx-react-lite"
import * as Screens from "@/screens"
import Config from "../config"
import { useStores } from "../models"
import { DemoNavigator, DemoTabParamList } from "./DemoNavigator"
import { navigationRef, useBackButtonHandler } from "./navigationUtilities"
import { useAppTheme, useThemeProvider } from "@/utils/useAppTheme"
import { ComponentProps } from "react"
```
- **React Navigation Imports**
  - `NavigationContainer`: Wraps the entire navigation system.
  - `createNativeStackNavigator`: Creates a stack-based navigation flow.
  - `NativeStackScreenProps`: Defines **props for stack screens** (used in `AppStackScreenProps`).
  - `NavigatorScreenParams`: Allows **nested navigators** (used for tab-based navigation).

- **MobX (`observer`)**: Ensures navigation updates reactively when authentication state changes.
- **Screens (`* as Screens`)**: Imports all screens dynamically.
- **Authentication (`useStores()`)**: Retrieves **authentication state** from MobX.
- **Theming (`useAppTheme`)**: Provides **dark/light mode support**.
- **Navigation Utilities (`useBackButtonHandler`)**: Handles Android back button behavior.

---

### **2. Defining Navigation Type (`AppStackParamList`)**
```tsx
export type AppStackParamList = {
  Welcome: undefined
  Login: undefined
  // Demo: NavigatorScreenParams<DemoTabParamList> // Removed for demo
}
```
- This **defines the app’s navigation structure**.
- Each **screen name** (e.g., `"Welcome"`, `"Login"`) is mapped to its **expected parameters**:
  - **`Welcome: undefined`** → No parameters required.
  - **`Login: undefined`** → No parameters required.
  - **Commented-out `Demo`** → Used for a tab navigator (`DemoTabParamList`).

> 🔥 `AppStackParamList` is crucial for **type safety in navigation**.

---

### **3. Creating `AppStackScreenProps`**
```tsx
export type AppStackScreenProps<T extends keyof AppStackParamList> = NativeStackScreenProps<
  AppStackParamList,
  T
>
```
- **Extracts navigation props** for a given screen.
- Used in `WelcomeScreenProps`:
  ```tsx
  interface WelcomeScreenProps extends AppStackScreenProps<"Welcome"> {}
  ```
- Ensures `navigation` and `route` props match **React Navigation’s type system**.

---

### **4. Creating the Navigation Stack**
```tsx
const Stack = createNativeStackNavigator<AppStackParamList>()
```
- **Creates a navigation stack** based on `AppStackParamList`.
- `Stack` manages **screen transitions** within the app.

---

### **5. Building `AppStack` (Main Stack Navigator)**
```tsx
const AppStack = observer(function AppStack() {
  const {
    authenticationStore: { isAuthenticated },
  } = useStores()

  const {
    theme: { colors },
  } = useAppTheme()

  return (
    <Stack.Navigator
      screenOptions={{
        headerShown: false,
        navigationBarColor: colors.background,
        contentStyle: {
          backgroundColor: colors.background,
        },
      }}
      initialRouteName={isAuthenticated ? "Welcome" : "Login"}
    >
      {isAuthenticated ? (
        <>
          <Stack.Screen name="Welcome" component={Screens.WelcomeScreen} />
          <Stack.Screen name="Demo" component={DemoNavigator} />
        </>
      ) : (
        <>
          <Stack.Screen name="Login" component={Screens.LoginScreen} />
        </>
      )}
    </Stack.Navigator>
  )
})
```
### **How It Works**
- **Checks `isAuthenticated` (MobX state)**:
  - If `true`: User **sees** `"Welcome"` and `"Demo"`.
  - If `false`: User **sees only `"Login"`**.
- **Disables headers** (`headerShown: false`).
- **Applies theming** (`navigationBarColor: colors.background`).
- **Uses `initialRouteName` to determine the first screen**.

---

### **6. `AppNavigator` (Top-Level Navigator)**
```tsx
export const AppNavigator = observer(function AppNavigator(props: NavigationProps) {
  const { themeScheme, navigationTheme, setThemeContextOverride, ThemeProvider } =
    useThemeProvider()

  useBackButtonHandler((routeName) => exitRoutes.includes(routeName))

  return (
    <ThemeProvider value={{ themeScheme, setThemeContextOverride }}>
      <NavigationContainer ref={navigationRef} theme={navigationTheme} {...props}>
        <AppStack />
      </NavigationContainer>
    </ThemeProvider>
  )
})
```
### **How It Works**
- **Wraps the entire app in a `NavigationContainer`**.
- **Handles Android back button behavior** via `useBackButtonHandler()`.
- **Applies theming (`useThemeProvider()`)** to support **dark/light modes**.
- **Uses `navigationRef`** for manually controlling navigation.

---

## **How Everything Fits Together**
| Component | Purpose |
|-----------|---------|
| **`AppStackParamList`** | Defines all screens and their expected parameters. |
| **`AppStackScreenProps<T>`** | Provides type safety for navigation props in each screen. |
| **`createNativeStackNavigator<AppStackParamList>()`** | Creates the stack navigator. |
| **`AppStack`** | Defines navigation behavior based on authentication state. |
| **`AppNavigator`** | Wraps everything in `NavigationContainer` and applies theming. |
| **`WelcomeScreenProps`** | Extends `AppStackScreenProps<"Welcome">` to enforce navigation types. |

### **Example Flow**
1. **User opens the app**:
   - `AppNavigator` initializes `AppStack`.
   - Checks if user is authenticated.
   - If `true`: Shows `"Welcome"` & `"Demo"`.
   - If `false`: Shows `"Login"`.

2. **User navigates**:
   - `navigation.navigate("Welcome")` works because `"Welcome"` is **defined in `AppStackParamList`**.
   - TypeScript ensures the correct **props are passed**.

---

## **Conclusion**
This navigation setup:
✅ **Enforces type safety** with `AppStackScreenProps`.  
✅ **Uses MobX** to reactively update the navigation stack.  
✅ **Supports dark/light theming** via `useThemeProvider()`.  
✅ **Handles Android back button behavior**.  

This structure is **scalable**, ensuring:
- **Future screens** can be easily added.
- **Navigation logic** remains **maintainable & type-safe**.

Would you like more clarification on any part? 🚀
