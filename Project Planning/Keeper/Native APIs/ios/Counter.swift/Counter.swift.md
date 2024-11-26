This code defines a class `Counter` in Swift that interacts with React Native, making use of Objective-C interoperability (`@objc`) to expose methods to the JavaScript side of a React Native app. Here's a breakdown of the code:

### Imports and Class Declaration

```swift
import Foundation
```
- **`Foundation`** is a core framework in Swift, providing essential data types, collections, and other basic functionalities.

```swift
@objc(Counter)
class Counter: NSObject {
```
- **`@objc(Counter)`**: This exposes the class `Counter` to Objective-C, which is necessary for React Native modules since the React Native bridge is built on Objective-C. 
- **`NSObject`**: This is the base class for most Objective-C classes. Subclassing `NSObject` is needed to interact with Objective-C and React Native.

### Properties

```swift
private var count = 0
```
- **`count`**: A private integer property initialized to `0`, representing the counter value. It's not directly accessible outside the class.

### `increment` Method

```swift
@objc
func increment(_ callback: RCTResponseSenderBlock) {
  count += 1
  print(count)
  callback([count])
}
```
- **`@objc`**: Marks the function as accessible from Objective-C (and therefore from React Native's JavaScript code).
- **`increment(_ callback: RCTResponseSenderBlock)`**: Increases the `count` by 1, prints the updated value, and calls the provided callback function from JavaScript, returning the new count as an array (since React Native requires arrays for callback arguments).

### `requiresMainQueueSetup` Static Method

```swift
@objc
static func requiresMainQueueSetup() -> Bool {
  return true
}
```
- **`requiresMainQueueSetup`**: A static method that React Native looks for to determine if this module needs to be initialized on the main thread. Returning `true` here means that this module must be set up on the main thread (often used when the module interacts with UI components or other main-thread-bound features).

### `constantsToExport` Method

```swift
@objc
func constantsToExport() -> [String: Any]! {
  return ["initialCount": count]
}
```
- **`constantsToExport`**: This method provides constant values to be exported to JavaScript when the module is initialized. Here, it exports the `initialCount` (the current value of `count`) to JavaScript. This method is commonly used to define static constants available in JavaScript without calling a method.

### `decrement` Method with Promises

```swift
@objc
func decrement(_ resolve: RCTPromiseResolveBlock, reject: RCTPromiseRejectBlock) {
  if (count == 0) {
    let error = NSError(domain: "", code: 200, userInfo: nil)
    reject("ERROR_COUNT", "Count cannot be negative", error)
  } else {
    count -= 1
    resolve(count)
  }
}
```
- **`decrement(_ resolve: RCTPromiseResolveBlock, reject: RCTPromiseRejectBlock)`**: This method decrements the `count` by 1, but only if `count` is greater than 0. It uses JavaScript Promises (via `resolve` and `reject` blocks) to return the result:
  - If `count` is 0, it rejects the promise, passing an error message (`"Count cannot be negative"`) to JavaScript.
  - Otherwise, it decrements the `count` and resolves the promise with the new value of `count`.

### Summary:
- This `Counter` class defines a counter that can be incremented and decremented from the JavaScript side of a React Native app.
- The class supports both callback-style methods (`increment`) and promise-style methods (`decrement`).
- It also exports a constant `initialCount` to the JavaScript side when the module is initialized.
```swift
import Foundation

@objc(Counter)
class Counter: NSObject {
  private var count = 0

  @objc
  func increment(_ callback: RCTResponseSenderBlock) {
    count += 1
    print(count)
    callback([count])
  }

  @objc
  static func requiresMainQueueSetup() -> Bool {
    return true
  }

  @objc
  func constantsToExport() -> [String: Any]! {
    return ["initialCount": count]
  }

  @objc
  func decrement(_ resolve: RCTPromiseResolveBlock, reject: RCTPromiseRejectBlock) {
    if (count == 0) {
      let error = NSError(domain: "", code: 200, userInfo: nil)
      reject("ERROR_COUNT", "Count cannot be negative", error)
    } else {
      count -= 1
      resolve(count)
    }
  }
}
```
___

Tags : #keepur #programming