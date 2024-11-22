```typescript
class ConnectionManager{
	const Connections : Map<string, Socket> ; 
	constructor(Connections : Map<string , Sockt>){
		this.Connections = Connections ; 
	}
	
	handleConnection(user_id , socket) : void {
	
	}
	
	disconnectUser(user_id) : void { 
	
	}

	broadcastToSession(user_id , socket) : void { 
	
	}
}

```
___

Tags : #programming #keeper #system-design 