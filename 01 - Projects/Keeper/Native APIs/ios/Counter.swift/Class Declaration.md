```swift
@objc(Counter)
class Counter: NSObject {
```

- **`@objc(Counter)`**: This exposes the class `Counter` to Objective-C, which is necessary for React Native modules since the React Native bridge is built on Objective-C.
- **`NSObject`**: This is the base class for most Objective-C classes. Subclassing `NSObject` is needed to interact with Objective-C and React Native.

___

Tags : #keepur #programming