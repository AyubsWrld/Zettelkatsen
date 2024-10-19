```javascript
import React, { useState, useEffect } from 'react';
import { View, StyleSheet, Text, Button, NativeModules, Alert } from 'react-native';

const { ScreenTimeBridge } = NativeModules;

export default function App() {
  const [count, setCount] = useState(0);
  const [isAuthorized, setIsAuthorized] = useState(false);
  const [isShielded, setIsShielded] = useState(false);

  useEffect(() => {
    // Initialize count from the native module (if still needed)
    if (ScreenTimeBridge.constantsToExport) {
      const initialCount = ScreenTimeBridge.constantsToExport().initialCount || 0;
      setCount(initialCount);
    }
  }, []);

  const requestAuthorization = async () => {
      try {
        await ScreenTimeBridge.requestAuthorization();
        setIsAuthorized(true);
        Alert.alert('Success', 'Authorization granted for Screen Time');
      } catch (error) {
        let message = 'Failed to get authorization';
        switch (error.code) {
          case 'AUTH_DENIED':
            message = 'Authorization was denied. Please enable Screen Time in Settings.';
            break;
          case 'AUTH_CANCELED':
            message = 'Authorization was canceled. Please try again.';
            break;
          case 'AUTH_FAILED_TO_RETRIEVE':
            message = 'Failed to retrieve authorization status. Please check your device settings.';
            break;
          case 'AUTH_UNKNOWN':
            message = 'An unknown error occurred during authorization.';
            break;
        }
        Alert.alert('Error', message);
      }
    };

  const selectApps = () => {
    ScreenTimeBridge.selectApps(() => {
      Alert.alert('Success', 'Apps selected successfully');
    });
  };

  const applyShields = async () => {
    try {
      await ScreenTimeBridge.applyShields();
      setIsShielded(true);
      Alert.alert('Success', 'Shields applied to selected apps');
    } catch (error) {
      Alert.alert('Error', 'Failed to apply shields: ' + error.message);
    }
  };

  const removeShields = async () => {
    try {
      await ScreenTimeBridge.removeShields();
      setIsShielded(false);
      Alert.alert('Success', 'Shields removed from all apps');
    } catch (error) {
      Alert.alert('Error', 'Failed to remove shields: ' + error.message);
    }
  };

  // Keeping the original counter functionality
  const increment = () => {
    if (ScreenTimeBridge.increment) {
      ScreenTimeBridge.increment(value => {
        setCount(value[0]);
      });
    }
  };

  const decrement = () => {
    if (ScreenTimeBridge.decrement) {
      ScreenTimeBridge.decrement()
        .then(result => {
          setCount(result);
        })
        .catch(error => {
          console.log(error.message);
        });
    }
  };

  return (
    <View style={styles.container}>
      <Text style={styles.text}>Count: {count}</Text>
      <Button title="Increase Count" onPress={increment} />
      <Button title="Decrease Count" onPress={decrement} />

      <View style={styles.separator} />

      <Button
        title="Request Authorization"
        onPress={requestAuthorization}
        disabled={isAuthorized}
      />
      <Button
        title="Select Apps to Shield"
        onPress={selectApps}
        disabled={!isAuthorized}
      />
      <Button
        title="Apply Shields"
        onPress={applyShields}
        disabled={!isAuthorized || isShielded}
      />
      <Button
        title="Remove Shields"
        onPress={removeShields}
        disabled={!isAuthorized || !isShielded}
      />
    </View>
  );
}
```

___

Tags : #keepur #programming