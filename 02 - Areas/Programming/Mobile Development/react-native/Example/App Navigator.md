#### Imports  
___
```typescript
import {
  NavigationContainer,
  NavigatorScreenParams, // @demo remove-current-line
} from "@react-navigation/native"
```

- `NavigationContainer`: The main container component for React Navigation. It manages the navigation state and linking.
- `NavigatorScreenParams`: Defines types for nested navigators, ensuring proper type checking when passing parameters.

```typescript
import { createNativeStackNavigator, NativeStackScreenProps } from "@react-navigation/native-stack"
```

- `createNativeStackNavigator`: Creates a stack navigator using the native stack implementation, which offers better performance on mobile.
- `NativeStackScreenProps`: A utility type that helps define the props for a screen inside a native stack navigator.

```typescript
import { observer } from "mobx-react-lite" // @mst remove-current-line
```

- `observer`: A higher-order component from MobX that makes React components reactive, re-rendering them when observed state changes.

```typescript
import * as Screens from "@/screens"
```

- Imports all screens from the `@/screens` directory, allowing dynamic access to screens in the navigator.

```typescript
import Config from "../config"
```

- Imports configuration settings from the `config` file, which might include environment variables, API keys, or navigation settings.

```typescript
import { useStores } from "../models" // @demo remove-current-line
```

- `useStores`: A custom hook to access MobX stores, providing state management for authentication, themes, and more.

```typescript
import { DemoNavigator, DemoTabParamList } from "./DemoNavigator" // @demo remove-current-line
```

- `DemoNavigator`: A separate navigator component, likely handling tab-based navigation within a demo section.
- `DemoTabParamList`: A TypeScript type defining available screens and parameters within the demo navigator.

```typescript
import { navigationRef, useBackButtonHandler } from "./navigationUtilities"
```

- `navigationRef`: A reference to the navigation container, allowing programmatic navigation outside of components.
- `useBackButtonHandler`: A custom hook to handle the Android back button, ensuring correct behavior for navigation exits.

```typescript
import { useAppTheme, useThemeProvider } from "@/utils/useAppTheme"
```

- `useAppTheme`: A custom hook for accessing the current theme (e.g., colors, dark/light mode).
- `useThemeProvider`: A utility that provides theme-related context and state management.

```typescript
import { ComponentProps } from "react"
```

- `ComponentProps`: A TypeScript utility that extracts the props type of a React component, allowing flexible prop definitions.
