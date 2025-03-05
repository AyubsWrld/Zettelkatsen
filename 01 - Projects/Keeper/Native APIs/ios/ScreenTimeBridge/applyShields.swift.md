```swift
    @objc
    func applyShields(_ selectedApps: [Any]) {
        // Attempt to cast each element to ApplicationToken
        let appTokens = selectedApps.compactMap { $0 as? ApplicationToken }
        let tokenSet = Set(appTokens) // Convert the array to a Set

        if tokenSet.isEmpty {
            store.shield.applications = nil
            print("Shields removed from all apps")
        } else {
            store.shield.applications = tokenSet
            print("Shields applied to apps: \(Array(tokenSet))") // Convert Set to Array for printing
        }
    }

```
___

Tags : #keepur #programming