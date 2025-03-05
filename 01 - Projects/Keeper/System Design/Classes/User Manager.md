```typescript
class UserManager{
	const ActiveUsers : Map<string , User>  ; 

	constructor( ActiveUsers : Map<string , User> ){
		this.ActiveUsers = ActiveUsers ; 	
	}

	addUser(User) : void {
		this.ActiveUsers.set(User.user_id , User) ; 		
	}
	
	removeUser(User) : void {
		this.ActiveUsers.delete(User.user_id , User) ; 		
	}

	getUser(user_id) : string {
		if(!this.ActiveUsers.get(user_id)){
			throw error 	
			return 
		}
		return this.ActiveUsers.get(user_id) ; 
	}
}

```
___

Tags : #programming #keeper #system-design 