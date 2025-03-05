A representation of an activity, such as an app or website, that doesn’t reveal its identity. Tokens are created using Struct [[Generics]] . 
 
```swift
struct Token<T>
```

### Overview
Managed Settings uses a `Token` to preserve user privacy and prevent anyone outside of a Family Sharing group from identifying what apps and websites the family accesses. You can use tokens to restrict and filter device use without accessing personal information.

`Managed Settings` provides the [[Application Token]] which will prove most useful within development  . The token can represent different activities ( We are most concerned with the [[Application]] activity )  through the use of [[Generics]] . 

```swift
struct Token<T> {
    // Generic struct logic here
}

struct Application {
    // Application logic here
}

typealias ApplicationToken = Token<Application>

```

___

Tags : #programming #screentime-API #swift #managed-settings