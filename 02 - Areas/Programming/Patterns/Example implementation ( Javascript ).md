
> [!summary] Language Concepts Used
>  [[Promise]]
>  [[Async Function]]
## Client
___
In this example the client calls the asynchronous function using [[useEffect]] , so the fetching occurs on render. 

```javascript
  useEffect(() => {
    fetchSession();
  }, []);
```

#####  **Client sends primary key to the socket for the server to make query to the database**
___
```javascript
  async function fetchSession() {
    console.log('Fetching credentials');
    try {
      const message = {
        type: 'fetchSession',
        user_id: user_id, // Primary Key being sent to the server to be used in query
      };
```

#### **Client waits for response from the server**
___
```javascript
      const result = await new Promise((resolve, reject) => {
        const handleSessionParameters = (message) => {
          console.log('Received session_parameters:', message);
          resolve(message); // Resolve the promise with the received data
          socket.off('session_parameters', handleSessionParameters); // Remove the listener after receiving the message
        };
```

___

___

## Server 
___
#####  **Server Receives primary key from the client**
___

```javascript
socket.on('fetchSession', (message) => {
  if (message.type === 'fetchSession') {
    fetchSession(message.user_id)
      .then((sessionData) => {
        if (sessionData) {
          const response = {
            type: 'session_parameters',
            session_parameters: sessionData,
          };

          socket.emit('session_parameters', response); // Correctly emit the response
        } else {
          console.log('No session data found.');
        }
      })
      .catch((error) => {
        console.error('Error fetching session data:', error);
      });
  }
});
```



```javascript
async function fetchSession(user_id) {
  console.log('Fetching credentials using:', user_id);
  try {
    const { data, error } = await supabase
      .from('sessions')
      .select('session_id, restriction_id, start_time, end_time, days_of_week, children_id')
      .or(`guardian_id.eq.${user_id},children_id.cs.{${user_id}}`);

    if (error) {
      console.log('Error occurred while fetching data:', error.message);
      return null; // Return null if there's an error
    }

    if (data) {
      return data; // Return the data if found
    } else {
      console.log('No data found for the provided session_id');
      return null; // Explicitly return null if no data
    }
  } catch (error) {
    console.log('Error occurred while fetching data:', error);
    return null; // Return null on any unexpected error
  }
}
```
___

Tags: #programming #patterns #server-side