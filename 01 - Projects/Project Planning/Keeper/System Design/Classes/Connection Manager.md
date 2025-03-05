```typescript
class ConnectionManager{
	const Connections : Map<string, string> ;  // Maps user_id to socket_id 
	constructor(Connections : Map<string , Socket>){ // Maps user ID to socket
		this.Connections = Connections ; 
	}
	
	handleConnection(user_id : string , socket_id : string) : void {
		if(Connections.get( socket_id )){
			console.log('Why would this ever occur ? ')	 ; 
			throw error ; 
		}
		Connections.set( user_id , socket_id )	 ; 
	}
	
	disconnectUser(user_id) : void { 
		Users.get(user_id).socket = null ; 	 // Remove socket from user class 
	}

	broadcastToSession(user_id , socket) : void {  // Pass in guardian ID
	
	}
}

```
___

Tags : #programming #keeper #system-design 