```swift
    @objc
    func selectApps(_ callback: @escaping RCTResponseSenderBlock) {
        DispatchQueue.main.async {
            let pickerView = AppPickerView(applyShields: self.applyShields) // Pass the shielding function
            let hostingController = UIHostingController(rootView: pickerView)

            hostingController.modalPresentationStyle = .formSheet
            hostingController.isModalInPresentation = true

            if let topController = UIApplication.shared.windows.first?.rootViewController {
                topController.present(hostingController, animated: true) {
                    callback([])
                }
            } else {
                print("Unable to present Family Activity Picker")
                callback([])
            }
        }
    }
```
___

Tags : #keepur #programming