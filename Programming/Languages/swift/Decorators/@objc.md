___
given that `Swift` and `Objective-C` support [[Interoperability]] , meaning that you can create a project which uses both `Swift` and `Objective-C` . However , `Swift Functions , Properties`   and `Classes` aren't automatically exposed to the `Objective-C` [[Runtime]] . In doing so we can 


##### Example Code
___
```swift
@objc(Counter)
class Counter: NSObject {
   // ...
   @objc func increment(_ callback: RCTResponseSenderBlock) {
       // ...
   }
   @objc func decrement(_ resolve: RCTPromiseResolveBlock, reject: RCTPromiseRejectBlock) {
       // ...
   }
   @objc static func requiresMainQueueSetup() -> Bool {
       return true
   }
   @objc func constantsToExport() -> [String: Any]! {
       return ["initialCount": count]
   }
}

```
___

Tags : #swift #swift-attribute #programming  #language 