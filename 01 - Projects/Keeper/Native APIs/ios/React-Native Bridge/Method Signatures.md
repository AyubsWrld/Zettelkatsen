####  `RCTResponseSenderBlock` 
___
Used when making Callbacks. For instance

```swift
@objc
func getData(_ callback: @escaping RCTResponseSenderBlock) {
	let data = [ "item1", "item2" ]  
	callback([NSNull(), data]);
}
```

####  `RCTPromiseResolveBlock` & `RCTPromiseRejectBlock` 
___
Used when making Promises. For instance 

```swift
@objc
func getDataWithPromise(
_ resolve: @escaping RCTPromiseResolveBlock,
rejecter reject: @escaping RCTPromiseRejectBlock
) {
	let success = true ;
	if success {
		resolve("Success From swift") 
	}else { 
	reject("Error_code", "Something went wrong", nil)  
	}
}
```

| Concept                  | Key Notes                                               |
| ------------------------ | ------------------------------------------------------- |
| `@objc`                  | Required for all exposed methods and class              |
| `@escaping`              | Needed if using the callback asynchronously             |
| `RCTResponseSenderBlock` | Use for callback-style functions                        |
| `PromiseResolveBlock`    | For cleaner async/await in JS                           |
| `requiresMainQueueSetup` | Return `true` if your native code needs the main thread |
___

Tags : #keepur #programming