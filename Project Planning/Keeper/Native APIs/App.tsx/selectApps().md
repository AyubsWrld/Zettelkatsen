> [!tldr] 
> [[Arrow Function]] used to create select applications to add to the family activity picker . 


#### Bit-sized explanation 
___

This function interacts with the [[selectApps.swift]] . 

```javascript
  const selectApps = () => {
    ScreenTimeBridge.selectApps(() => {
      Alert.alert('Success', 'Apps selected successfully');
    });
  };

```

___

Tags : #programming #native-module #javascript 