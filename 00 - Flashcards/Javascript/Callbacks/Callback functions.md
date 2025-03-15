Functions passed in as arguments. 

```javascript
function useCallback(firstname : string , lastname : string , callback ) : void {
  callback( firstname + lastname ) ;
}

function callMe ( Name : string ) : void {
  console.log(`Calling ${Name}`);
}

useCallback( "Ayub" , "Mohamed" , callMe ) ;

```


___
Tags : #programming #javascript 