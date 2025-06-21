Adapters around [[IO Readers and Writers]] to allow us to serialize any [[Interface]] and convert it into buffer friendly format we can write to buffers.

```go

// Create a buffer

var buffer bytes.Buffer ; 

encodeAdapter := gob.NewEncoder( buffer ) ; 
encodeAdapter.encode( /* Some interface{} goes here */ ) ; 

var dest Person ; 

//Create a new io.reader. 
decodeAdapter.NewDecoder( bytes.NewReader( buffer.Bytes()) ; 

// Take whatever is in that buffer and read into this.
decodeAdapter.Decode( &dest ) 
```
____
Tags: #programming #golang #language 