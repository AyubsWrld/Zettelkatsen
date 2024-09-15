### 1. **Importing Foundation**
   ```swift
   import Foundation
   ```
   - This imports the Foundation framework, which provides essential data types, collections, and operating system services for Swift apps.

### 2. **Defining the Counter Class**
   ```swift
   @objc(Counter)
   class Counter: NSObject {
   ```
   - The `@objc(Counter)` attribute makes the `Counter` class accessible to Objective-C, which is necessary for it to be used with React Native.
   - The class inherits from `NSObject`, which is the base class of most Objective-C classes and provides basic object behavior.

### 3. **Private Property: `count`**
   ```swift
   private var count = 0
   ```
   - `count` is a private integer property that tracks the current count. It’s private, meaning it can only be accessed within the `Counter` class.

### 4. **Method: `increment`**
   ```swift
   @objc
   func increment(_ callback: RCTResponseSenderBlock) {
       count += 1
       print(count)
       callback([count])
   }
   ```
   - This method increments the `count` by 1.
   - The `@objc` attribute makes it accessible from JavaScript.
   - The `callback` parameter is of type `RCTResponseSenderBlock`, which is a block that React Native uses to send data back to JavaScript.
   - After incrementing the count, it prints the new value and passes it back to JavaScript via the `callback`.

### 5. **Static Method: `requiresMainQueueSetup`**
   ```swift
   @objc
   static func requiresMainQueueSetup() -> Bool {
       return true
   }
   ```
   - This method indicates whether the module should be initialized on the main thread. Returning `true` means the module must be initialized on the main thread, which is important for UI updates or tasks that must be executed on the main thread.

### 6. **Method: `constantsToExport`**
   ```swift
   @objc
   func constantsToExport() -> [String: Any]! {
       return ["initialCount": count]
   }
   ```
   - This method exports constants that can be accessed from JavaScript when the module is initialized. In this case, it exports the initial value of `count` under the key `"initialCount"`.

### 7. **Method: `decrement`**
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
   - This method decreases the `count` by 1.
   - It uses a promise pattern, which is common in JavaScript. The `resolve` block is called with the new count if the operation succeeds, and the `reject` block is called if the operation fails.
   - If `count` is already 0, it creates an error and calls `reject` with an error code and message. Otherwise, it decrements `count` and calls `resolve` with the new count.
____

Tags : #swift #react-native #expo 