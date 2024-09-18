class Screentime_SandboxMonitor: DeviceActivityMonitor { // Extends DeviceActivityMonitor
    let database = BarkDatabase()
    
    override func intervalDidStart(for activity: DeviceActivityName) {
        super.intervalDidStart(for: activity)
        let socialStore = ManagedSettingsStore(named: .social)
        socialStore.clearAllSettings() // Clear settings when the interval starts
        print(Interval started, social settings cleared.)
    }
    
    override func intervalDidEnd(for activity: DeviceActivityName) {
        super.intervalDidEnd(for: activity)
        let socialStore = ManagedSettingsStore(named: .social)
        let socialCategory = database.socialCategoryToken // Retrieve the category from the database
        socialStore.shield.applicationCategories = .specific([socialCategory])
        socialStore.shield.webDomainCategories = .specific([socialCategory])
        print(Interval ended, social settings restored.)
    }
    
    // Function to start monitoring
    func startMonitoring() {
        let schedule = DeviceActivitySchedule(
            intervalStart: Date(), // Define your interval start
            intervalEnd: Date().addingTimeInterval(3600) // End after 1 hour, for example
        )
        let activity = DeviceActivityName(SocialMediaMonitoring)
        try? DeviceActivityCenter.shared.startMonitoring(activity, during: schedule)
        print(Started monitoring device activity.)
    }
    
    // Function to stop monitoring
    func stopMonitoring() {
        let activity = DeviceActivityName(SocialMediaMonitoring)
        DeviceActivityCenter.shared.stopMonitoring(activity)
        print(Stopped monitoring device activity.)
    }
}

_____
extension ManagedSettingsStore.Name {

    static let gaming = Self("gaming")

    static let social = Self("social")

}

  

func worklogSetup() {

    let gamingCategory = ActivityCategoryToken(...)

    let gamingStore = ManagedSettingsStore(named: .gaming)

    gamingStore.shield.webDomainCategories = .specific([gamingCategory])

  

    let socialCategory = ActivityCategoryToken(...)

    let socialStore = ManagedSettingsStore(named: .social)

    socialStore.shield.applicationCategories = .specific([socialCategory])

    socialStore.shield.webDomainCategories = .specific([socialCategory])

} 

  

  

//typealias ApplicationToken = Token<Application>

//

let app1 = Application(bundleIdentifier: "com.google.chrome.ios")