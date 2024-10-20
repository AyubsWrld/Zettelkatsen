
> [!tldr] 
> [[Async Function]] which interacts with [[removeShields.swift]] member function of [[ScreenTimeBridge]] . It is utilized to set sheilds on the selected applications . 

#### Bit-sized explanation 
___
```javascript
  const removeShields = async () => {
    try {
      await ScreenTimeBridge.removeShields();
      setIsShielded(false);
      Alert.alert('Success', 'Shields removed from all apps');
    } catch (error) {
      Alert.alert('Error', 'Failed to remove shields: ' + error.message);
    }
  };

```

___

Tags : #programming #native-module #javascript 