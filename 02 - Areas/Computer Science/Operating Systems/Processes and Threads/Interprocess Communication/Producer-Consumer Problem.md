- **Consumer**: takes object out of buffer. 
- **Producer**: Places object within buffer. 

A sort of codependence arises within this system. However a problem arises when either attempts to perform their desired task when the other has not placed/removed anything out of the buffer. For example the **Producer** attempts to place more data into the buffer even though there exists some data the consumer has not yet consumed ( Same goes for the inverse of this with the consumer trying to take data out of the buffer even though there is no data within it ). 

Either can sleep whenever one of these conditions is true to wait for them to perform their task when the buffer is ready. Subject to race conditions however. 

___
Tags : #computer-architecture #operating-systems #processes