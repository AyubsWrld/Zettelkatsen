```typescript

class SessionManager{
	const activeSessions : Map<string, Session> ; 
	consctructor(activeSessions : Map<string, Session>){
		this.activeSessions = activeSessions ; 
	}

	endSession( session_id : string ) : void { 
		
	}
	
	beginSession( session_id : string ) : void { 	
		//Check if the session exists 
		if(!activeSessions.get(session_id)){
			throw error ; 
		}
		const session = activeSessions
	}

	cleanupInactiveSession() : void {
	
	}
}
```
___

Tags : #programming #keeper #system-design 