##### Requesting Access 
___
Firstly we must request access to the child's applications . So we must import the [[Family Controls ]]framework to begin with . 

```swift
import FamilyControls
```

Next we must actually request authorization 

```swift
AuthorizationCenter.shared.requestAuthorization { result in 
	switch result {
	case .success(): 
	 /* 
		 Implement sucessful authorization code here
	 */ 
	}
	case .failure(let error): 
	 /* 
		 Implement unsuccessful authorization code here
		 Returns unsuccessful if signed in iCloud is not a child using Family Sharing
	 */ 
	}												 
}
```


##### Executing the code without the application running  
___
Because it would be rare for a child to ever run the parental control application , [[Device Activity]] serves to solve this problem through asynchronous code execution based on one of two parameters... 
1) Between two time intervals . For example locking the application between the hours of 5PM and 9:00PM  . 
2) Limiting the amount of time which an application can be utilized . 

_Implementation..._ 

Firstly we must import the [[Device Activity]] framework so that we can actually set up these boundaries . 

```swift 
import DeviceActivity
```

Next we create the `Start` and `End` intervals which will take the intervals an execute code accordingly . 

```swift
// EXTENSION: Create a DeviceActivityMonitor
import DeviceActivity

class MyMonitor: DeviceActivityMonitor{
	override func intervalDidStart(for activity: DeviceActivityNAme){
		super.intervalDidStart(for: activity) ; 
	}
	
	override func intervalDidEnd(for activity: DeviceActivityNAme){	
		super.intervalDidEnd(for: activity) ; 
	}
}
```

Next we create a `Device Activity Name` and a `Device Activity Schedule` 
```swift
//APP : Monitor a DeviceActivitySchedule 

import DeviceActivity 

extension DeviceActivityName{ //How activity is referenced within the extension 
	static let daily = Self("daily") ; //Set device activity name to daily 
}

let schedule = DeviceActivitySchedule( // Represents time bounds app monitors for activity

	intervalStart : DateComponents(hour: 0 , minute: 0),  // Starts and ends at midnight
	intervalEnd: DateComponents(hour: 23 , minute: 59), 
	repeats: true // Activity also repeats . 
) ;

let center = DeviceActivityCenter(); // Create a DeviceActivityCenter
try center.startMonitoring(.daily, during: schedule) // Call startMonitoring with activity name and sschdule 

```

_Selecting applications to shield_ 
___
We utilize [[Family Controls]]  in conjunction with `SwiftUI` to  achieve this . 
```swift
import FamilyControls 
import SwiftUI

@StateObject var model = MyModel() ;
@State var isPresented = false ; 

var body: some View{
	Button("Select Apps to Discourage"){
		isPresented = true ; 
	}
	.familyActivityPicker(isPresented: $isPresented,
		selection: $model.selectionToDiscourage) ; 
}
```

The application then returns opaque tokens and sets restrictions on the applications each token represents . 

```swift
// EXTENSION: Create a DeviceActivityMonitor
import DeviceActivity
import ManagedSettings

class MyMonitor: DeviceActivityMonitor{
	let store = ManagedSettingsStore()
	override func intervalDidStart(for activity: DeviceActivityNAme){
		super.intervalDidStart(for: activity) ; 

		let model = MyModel() ; 
		let applications = model.selectionToDiscourage.applications ; 
		store.shield.applications = application.isEmpty ? nil : applications ;
	}
	
	override func intervalDidEnd(for activity: DeviceActivityNAme){	
		super.intervalDidEnd(for: activity) ; 
		store.shield.applications = nil  ; 
	}
}
```
____

Tags : #screentime-API