Entry point to the application . Essentially whenever anything occurs on the IOS , the AppDelegate takes that input and delegates a task to the backend , such as calling a function or reading/writing data .   

### Example AppDelegate

##### Dependencies Inclusion 

```cpp
#import "AppDelegate.h" // Header file for 
#import <React/RCTBundleURLProvider.h>
#import <React/RCTLinkingManager.h>
```

___

Tags : #keepur #objective-c #entry-point