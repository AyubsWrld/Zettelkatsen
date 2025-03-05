```swift
@available(iOS 16.0, *)
@objc(ScreenTimeBridge)
class ScreenTimeBridge: NSObject {
    private let center = AuthorizationCenter.shared
    private let store = ManagedSettingsStore()

    @objc
    func requestAuthorization(_ resolve: @escaping RCTPromiseResolveBlock, reject: @escaping RCTPromiseRejectBlock) {
        Task {
            do {
                try await center.requestAuthorization(for: .individual)
                print("Authorization successful")
                setupMonitoring()
                resolve(true)
            } catch {
                print("Authorization failed: \(error.localizedDescription)")
                reject("AUTH_ERROR", "Authorization failed: \(error.localizedDescription)", error)
            }
        }
    }
```
___

Tags : #keepur #programming