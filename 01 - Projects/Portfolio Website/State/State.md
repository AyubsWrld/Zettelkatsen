### Slices
___
#### `name`: Level
#### `initialState`:

```javascript
currentLevel: 'StartScreen',
binaryMap: { null }, // Load from file later. null in beginning. ? 
description: { null }, // Component Array to render the description of. ? 
model: 'path_to_model' // Path to model. 
```
#### `Reducers`: 
- `level`: 
	- `setCurrentlevel: (state, payload)`. Payload is a string for the level. 
	- `loadCurrentLevel`: ( state, payload ). Dispatched from level selection. 
	- `returnToStart`: ( state ). Return to start level and clear all the binaries. 
	- `setBinaryMap`: ( state, payload ). called when setCurrentLevel is called, loads binaries from json file. 
	- `setDescription`: Sets description for current level. 
