#### Goal 
___
- Be able to change the video on command.
#### Requirements 
___
- Have an expendable list of videos which I can iterate through and dynamically set the texture when needed.
- I should be able to select a video read off disk and set the texture @ runtime ( e.g. user presses button and it loads selects the right project )

#### Breaking down problem
___
- Array to store list of video URI's. 
- Pointer to current index of the array.
- User can scroll down/up to decrement/increment the pointer.
- Index into the array and retrieve uri. 
- Set value. 

____
### Gameplan
____
- Create array of video textures and store them into VideoTextures.jsx
- Load video textures
- Iterate through index retrieving values when needed. 
## Current code 
____
##### Loading model 
___
We load the model using [useGLTF hook](https://drei.docs.pmnd.rs/loaders/gltf-use-gltf#usegltf-hook). This loads any relevant data we need to use the actual GLTF model within our code. We save the scene, nodes and material from it for later use. 

```javascript
  const modelPath = getModelPath('Test.glb'); // Retrieve model path from base url. 
  const { scene, nodes, materials } = useGLTF(modelPath);
```

#### Setting the video value 
___
We create an HTML element which is to be used within the 

#### Solution 
___
Got it working albeit the code needs some work and cleaning up so that it's just a bit more modular. 

----
Tags : #javascript #portfolio-website