#### Example Code 
```javascript
import React, { useState } from "react";
import { Text, View, StyleSheet, Alert } from "react-native";
import { createClient } from '@supabase/supabase-js';
import Button from "../components/Button";
import Input from "../components/Input";

// Supabase client configuration
const supabaseUrl = 'https://tqtqpftsctrshouqpcej.supabase.co';
const supabaseAnonKey = 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6InRxdHFwZnRzY3Ryc2hvdXFwY2VqIiwicm9sZSI6InNlcnZpY2Vfcm9sZSIsImlhdCI6MTcyODg5MTU0MywiZXhwIjoyMDQ0NDY3NTQzfQ.2h9rCohCCLwl1AGT8Kg8CXjp7fw87jYSV3zz6qRtKxs';
const supabase = createClient(supabaseUrl, supabaseAnonKey);

export default function Login({ navigation }) {
  const [email, setEmail] = useState("");
  const [password, setPassword] = useState("");
  const [loading, setLoading] = useState(false);

  async function validateCredentials() {
    if (!email || !password) {
      Alert.alert("Error", "Please enter both email and password.");
      return;
    }

    setLoading(true);

    try {
      const { data, error } = await supabase
        .from('users')
        .select('role_id')
        .eq('email', email)
        .eq('password', password)
        .single();

      if (error) {
        console.error("Error fetching data:", error);
        Alert.alert("Error", "An error occurred while verifying credentials.");
        return;
      }

      if (data) {
        console.log("Login successful:", data);
        navigation.navigate("PopulateInfo");
      } else {
        Alert.alert("Error", "Invalid email or password.");
      }
    } catch (error) {
      console.error("Error caught in catch block:", error);
      Alert.alert("Error", "An unexpected error occurred.");
    } finally {
      setLoading(false);
    }
  }

  return (
    <View style={styles.container}>
      <View style={styles.imageContainer}></View>
      <Text style={styles.loginHeader}>Login</Text>
      <View style={styles.rowOne}>
        <Input placeholder="Email" callback={setEmail} value={email} />
        <Input placeholder="Password" callback={setPassword} value={password} secureTextEntry />
        <Button type="small" text={loading ? "Loading..." : "Continue"} callback={validateCredentials} disabled={loading} />
      </View>
      <View style={styles.rowTwo}>
        <View style={styles.divider}></View>
        <Text style={styles.dividerText}>or</Text>
        <View style={styles.divider}></View>
      </View>
      <View style={styles.rowThree}>
        <Button
          type="medium"
          text="Sign in with Google"
          trailing="rightarrow"
          leading="google"
        />
        <Button
          type="medium"
          text="Sign in with LinkedIn"
          trailing="rightarrow"
          leading="linkedin"
        />
      </View>
    </View>
  );
}

```
Certainly! I'll provide you with flashcards summarizing the key changes, followed by explanations and references to the Supabase documentation.





# Flashcards: Key Changes to Login Component

1. **Removed useEffect hook**
   - Before: Fetched all first names on component mount
   - After: Credentials checked only when "Continue" is pressed

2. **Async validateCredentials function**
   - Before: Simple navigation based on email/password presence
   - After: Queries Supabase to verify credentials

3. **Supabase query**
   - Before: No direct database query
   - After: Uses `supabase.from('users').select().eq().eq()`

4. **Error handling**
   - Before: Basic error logging
   - After: Comprehensive error handling with user feedback

5. **Loading state**
   - Before: No loading state
   - After: Disables button and shows loading message during authentication

6. **Password input**
   - Before: Plain text input
   - After: Uses `secureTextEntry` for password masking



Now, let's go through each change in detail and reference the relevant Supabase documentation:

1. **Removed useEffect hook**
   - Explanation: Instead of fetching all user data on component mount, we now query the database only when the user attempts to log in. This improves performance and security.
   - Supabase docs: This change doesn't directly relate to Supabase, but aligns with best practices for on-demand data fetching.

2. **Async validateCredentials function**
   - Explanation: We transformed the function into an async operation to handle the Supabase query.
   - Supabase docs: [Using async/await with Supabase client](https://supabase.com/docs/reference/javascript/installing)

3. **Supabase query**
   - Explanation: We use Supabase's query builder to check for a user with matching email and password.
   - Supabase docs: [Querying data](https://supabase.com/docs/reference/javascript/select)
   - Specific method: `.from('users').select('role_id').eq('email', email).eq('password', password).single()`

4. **Error handling**
   - Explanation: We added comprehensive error handling to catch and display various error scenarios.
   - Supabase docs: [Error handling](https://supabase.com/docs/reference/javascript/select#error-handling)

5. **Loading state**
   - Explanation: We introduced a loading state to provide visual feedback during the authentication process.
   - Supabase docs: This is a React-specific implementation, not directly related to Supabase.

6. **Password input**
   - Explanation: We added the `secureTextEntry` prop to the password Input component for better security.
   - Supabase docs: This is a React Native-specific implementation, not directly related to Supabase.

It's important to note that while these changes improve the functionality of the login component, there are still security considerations to address:

- The current implementation compares passwords directly in the database, which is not secure. In a production environment, you should use Supabase's built-in authentication methods.
- Supabase docs: [Authentication](https://supabase.com/docs/guides/auth)
- Recommended method: `supabase.auth.signInWithPassword({ email, password })`

This method handles password hashing and security properly, and is the recommended way to implement user authentication with Supabase.

For further improvements and best practices, I recommend reviewing the following Supabase documentation:

1. [Supabase Auth Helpers](https://supabase.com/docs/guides/auth/auth-helpers)
2. [Supabase Auth API](https://supabase.com/docs/reference/javascript/auth-signin)
3. [Row Level Security](https://supabase.com/docs/guides/auth/row-level-security)

These resources will help you implement a more secure and robust authentication system using Supabase.
____
Tags : #programming #supabase