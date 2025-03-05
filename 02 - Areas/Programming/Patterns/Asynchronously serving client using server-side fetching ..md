> [!abstract] 
> This pattern revolves an async-await request from the client being sent to the server and the server responding with data queried from the database . 

### Psuedo Code 
___
> [!warning] 
> Make sure that the function being initiate the correspondence is even called . This can be done even based or on render . 

 - **Client**  
	 - `Client sends primary key to the socket for the server to make query to the database`
	 - `Client Asynchronously awaits the response from the server`
	 - `Client listens to response`
	 - `When the server responds the client does what they want with the data`
- **Server**
	- `Server recieves value from socket`
	- `Server begins query`
	- `After the data is recieved the server responds to the socket with the query data`
____
> [!tip] 
> A really good rule of thumb when communication occurs between the client and the server is to ALWAYS know the structure of the data which the client is sending , how the server is manipulating it , and the structure of the data being sent back to the client 




___

Tags: #programming #patterns #server-side