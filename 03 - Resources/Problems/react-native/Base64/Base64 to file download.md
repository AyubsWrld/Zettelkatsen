#### Description
___
We have Base64 encoded string we want to allow the user to be able to download it without having to view it within the application.

- [ ] Find filepath to save to files 

```typescript

const results = await DocumentPicker.pickSIngle({
	type: [[DocumnetPicker.types.allFiles]],
	copyto: [[ 'documentDirectory' ]]
});

```

``



	- [ ] use [[writeFile]] to save the file  
	- [ ] Use RNFS to interact with everything 


___
Tags : #react-native #graphite #encoding 