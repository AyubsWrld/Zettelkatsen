- This is your exotic Russian pastry within our pastry analogy ([[How the Native Modules Interact]])
- This is the source implementation for whatever code is going to be called within the `React-native` project . 
- Its exists to be received by the chef  , `Swift` and given to the clerk `Objective-C` ( They both speak the same language  , see [[Interoperability]] . ) 
-  We must expose the `Classes` and `Functions` to Clerk (`Objective-C`) through the use of [[@objc]] attribute . 

##### Core Structure 
____

_Import necessary libraries_
```swift
import Foundation 
```

_Create Functions , Classes ( Pastries ) , and expose to `Objective-C` using [[@objc]]_
```swift 

@objc(classname)
class classname : NSObject {
	private var variable = 30 ; 
	/*
		Implementation goes here
	*/
	@objc func functionName() -> returnType {	
		/*
			Implementation goes here
		*/
	}
}
```

##### Example Code
____

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

Tags : #programming #swift #react-native #native-module