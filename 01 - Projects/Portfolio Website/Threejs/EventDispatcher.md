Allows us to create custom event listeners to objects and listen for events and later on within our code trigger events at run time. 


For example... 

```javascript
const videoMesh = mesh['Mesh_name_XX' ] ; 
videoMesh.addEventListener( ' customEvent ', ( event ) => {
	// Execute some logic here when we fire the logic 
})
// Type is the name of the event we are firing. 
videoMesh.dispatchEvent( { type: 'customEvent' }) ;
```

----
Tags : #javascript #portfolio-website #threejs 