```swift
// MARK: - SwiftUI View for FamilyActivityPicker
@available(iOS 16.0, *)
struct AppPickerView: View {
    @State private var selection = FamilyActivitySelection() // Use @State to track changes
    @Environment(\.presentationMode) var presentationMode // For dismissing the view
    var applyShields: ([Any]) -> Void // Closure to apply shields

    var body: some View {
        NavigationView {
            FamilyActivityPicker(selection: $selection) // Bind the selection state
                .navigationTitle("Select Apps")
                .navigationBarTitleDisplayMode(.inline)
                .toolbar {
                    ToolbarItem(placement: .navigationBarTrailing) {
                        Button("Confirm") {
                            let selectedTokens = Array(selection.applicationTokens) // Convert to Array
                            print("Selected apps: \(selectedTokens)")
                            applyShields(selectedTokens) // Apply shields to selected apps
                            // Dismiss the view after confirming the selection
                            presentationMode.wrappedValue.dismiss()
                        }
                    }
                }
        }
    }
}
```

___

Tags : #keepur #programming