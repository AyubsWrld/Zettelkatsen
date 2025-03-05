
> [!tldr] 
> [[Async Function]] which interacts with [[applyShields.swift]] member function of [[ScreenTimeBridge]] . It is utilized to set sheilds on the selected applications . 

#### Bit-sized explanation 
___

```javascript
  const applyShields = async () => {
    try {
      await ScreenTimeBridge.applyShields();
      setIsShielded(true);
      Alert.alert('Success', 'Shields applied to selected apps');
    } catch (error) {
      Alert.alert('Error', 'Failed to apply shields: ' + error.message);
    }
  };
```  

___

Tags : #programming #native-module #javascript 