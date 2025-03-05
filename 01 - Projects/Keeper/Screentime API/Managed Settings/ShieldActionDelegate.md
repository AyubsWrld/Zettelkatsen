The `ShieldActionDelegate` is a protocol that your app conforms to in order to handle Screen Time interactions. This protocol includes methods that are called when the user interacts with the Screen Time shield.

### Key Components of Shield Action Delegate
- **Delegate Protocol**:
    
    - The `ShieldActionDelegate` is a protocol that your app conforms to in order to handle Screen Time interactions. This protocol includes methods that are called when the user interacts with the Screen Time shield.
    
- **Handling Requests for Time**:
    
    - One of the primary roles of this delegate is to manage requests for more time. For example, if a child requests more time to use an app that has reached its limit, your app can handle this request by either allowing or denying it, depending on the guardian's preferences or policies.
    
- **Customizing User Experience**:
    
    - You can customize the messages or actions presented to the user when they encounter a Screen Time restriction. For instance, you could provide an additional educational message or offer alternative activities.
### Common Methods in Shield Action Delegate

- **`handleTimeExtensionRequest(for app:)`**:
    
    - **Purpose**: This method is called when the user requests more time to use the app. You can customize the response by either allowing the request (possibly after verifying it with the guardian) or denying it.
    - **Implementation Tip**: You might want to integrate a notification to the guardian when such a request is made or log these requests for future review.
- **`handleIgnoreLimitRequest(for app:)`**:
    
    - **Purpose**: This method is called when the user attempts to ignore the Screen Time limit. Depending on the app's policy or settings, you can either allow this action (perhaps after a certain verification process) or deny it.
    - **Implementation Tip**: This is where you might add additional security measures, like requiring a passcode or biometric verification before allowing the limit to be ignored.
- **`shieldViewController(for app:)`**:
    
    - **Purpose**: This method allows you to customize the shield view that appears when the app is restricted. You can personalize this view to better align with your app's branding or provide additional context to the user about why the app is restricted.
    - **Implementation Tip**: Consider using this opportunity to educate users on healthy usage habits or direct them to other features of the app that aren’t restricted.

### Example 
Certainly! Below is a brief example of how you might implement and use the `ShieldActionDelegate` in a Screen Time-controlled app.

### Example Scenario:
Imagine you are developing a game app for kids, and you want to handle what happens when a Screen Time limit is reached. You want to allow the child to request more time, but that request should be sent to a parent for approval.

### Step 1: Conform to `ShieldActionDelegate`

First, ensure your view controller conforms to the `ShieldActionDelegate` protocol.

```swift
import UIKit
import DeviceActivity

class GameViewController: UIViewController, ShieldActionDelegate {

    override func viewDidLoad() {
        super.viewDidLoad()
        // Additional setup
    }

    // Handle requests for more time
    func handleTimeExtensionRequest(for app: ApplicationIdentifier) {
        // Show an alert to the child that the request has been sent
        let alert = UIAlertController(title: "Time Extension Requested",
                                      message: "Your request for more time has been sent to your parent for approval.",
                                      preferredStyle: .alert)
        alert.addAction(UIAlertAction(title: "OK", style: .default))
        present(alert, animated: true, completion: nil)
        
        // Simulate sending a notification to the parent for approval
        notifyParentForApproval(for: app)
    }

    // Handle requests to ignore limit
    func handleIgnoreLimitRequest(for app: ApplicationIdentifier) {
        // Deny the request with an appropriate message
        let alert = UIAlertController(title: "Access Denied",
                                      message: "You cannot ignore the screen time limit.",
                                      preferredStyle: .alert)
        alert.addAction(UIAlertAction(title: "OK", style: .default))
        present(alert, animated: true, completion: nil)
    }

    // Optional: Customize the shield view
    func shieldViewController(for app: ApplicationIdentifier) -> UIViewController? {
        // Provide a custom view controller that explains why the app is restricted
        let customShieldVC = CustomShieldViewController()
        customShieldVC.message = "Screen time limit reached. Take a break and try again later!"
        return customShieldVC
    }
    
    // Helper function to simulate notifying a parent
    func notifyParentForApproval(for app: ApplicationIdentifier) {
        // In a real app, you might send a push notification or update a server
        print("Notifying parent for approval...")
    }
}
```

### Step 2: Set the Delegate

When you set up your app, you need to assign your `GameViewController` as the delegate that handles shield actions:

```swift
override func viewDidLoad() {
    super.viewDidLoad()

    // Assume `screenTimeController` is an instance managing Screen Time
    screenTimeController.shieldDelegate = self
}
```

### Step 3: Customize the Shield View (Optional)

If you want to provide a custom experience when the Screen Time shield appears, implement the `shieldViewController(for:)` method as shown in the example. You can create a custom `UIViewController` that explains the restriction and provides additional options or information.

### Summary

In this example, when a child hits the Screen Time limit while playing the game, they can request more time. This request triggers a notification to the parent, and the app displays an appropriate message. The app also denies any requests to ignore the limit and can present a custom shield view to explain the restriction.

This setup helps you manage Screen Time limits while providing a controlled experience for young users and their guardians.

___

Tags : #swift #screentime-API 