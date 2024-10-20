```swift
    private func setupMonitoring() {
        let schedule = DeviceActivitySchedule(
            intervalStart: DateComponents(hour: 0, minute: 0),
            intervalEnd: DateComponents(hour: 23, minute: 59),
            repeats: true
        )
        let center = DeviceActivityCenter()
        do {
            try center.startMonitoring(.daily, during: schedule)
            print("Monitoring started successfully")
        } catch {
            print("Failed to start monitoring: \(error)")
        }
    }
```
___

Tags : #keepur #programming