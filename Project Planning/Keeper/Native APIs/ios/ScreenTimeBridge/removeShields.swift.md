```swift
    @objc
    func removeShields(_ resolve: @escaping RCTPromiseResolveBlock, reject: @escaping RCTPromiseRejectBlock) {
        store.shield.applications = nil
        print("All shields removed")
        resolve(true)
    }

```
___

Tags : #keepur #programming