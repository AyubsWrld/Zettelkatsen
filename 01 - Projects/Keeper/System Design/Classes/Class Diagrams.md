
```mermaid
classDiagram
    class SessionManager {
        -Map~string, Session~ activeSessions
        +createSession(guardianId, childIds)
        +endSession(sessionId)
        +getSession(sessionId)
        +cleanupInactiveSessions()
    }
    
    class Session {
        -string sessionId
        -Guardian guardian
        -List~Child~ children
        -DateTime startTime
        -DateTime lastActive
        +addChild(Child)
        +removeChild(Child)
        +isActive()
        +updateLastActive()
    }
    
    class ConnectionManager {
        -Map~string, WebSocket~ connections
        +handleConnection(userId, socket)
        +disconnectUser(userId)
        +broadcastToSession(sessionId, message)
    }
    
    class UserManager {
        -Map~string, User~ activeUsers
        +addUser(user)
        +removeUser(userId)
        +getUser(userId)
    }
    
	class Guardian{
		- static readonly USER_TYPE = 1 
		- private socket Socket
		+ beginSession(session_id)
		+ endSession(session_id)
	}
	
	class Child{
		- static readonly USER_TYPE = 0 
		- private socket Socket
	}

    SessionManager "1" --> "*" Session
    Session "*" --> "1" Guardian
    Session "*" --> "*" Child
    ConnectionManager -- SessionManager
    UserManager -- SessionManager
```

### User 
___
- `user_type` : used to delineate user type ( *1* represents guardian whereas *0* represents a child ) . 
- `user_id` : Unique User Identifier ( *UUID* ) number representing the user . 
- `first_name` : First name of user 
- `last_name` : Last name of user 
- `email` : email address of user 

### Guardian 
___
**Extends user**
- `static readonly USER_TYPE` : signifies Guardian  . 
- `private socket Socket` : Socket associated with the users 
+ `beginSession(session_id)` : send begin signal to signal manager
+ `endSession(session_id)` : sends end signal to signal manager
### Child 
___
**Extends user**
- `static readonly USER_TYPE` : signifies Guardian  . 
- `private socket Socket` : Socket associated with the users 

___

Tags : #programming #keeper #system-design 