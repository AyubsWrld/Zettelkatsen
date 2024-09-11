1. **AmbientLight**:
   ```jsx
   <ambientLight intensity={0.5} />
   ```

2. **DirectionalLight**:
   ```jsx
   <directionalLight 
     position={[10, 10, 10]} 
     intensity={1} 
     castShadow 
   />
   ```

3. **PointLight**:
   ```jsx
   <pointLight 
     position={[5, 5, 5]} 
     intensity={1} 
     distance={10} 
     decay={2} 
   />
   ```

4. **SpotLight**:
   ```jsx
   <spotLight 
     position={[0, 10, 0]} 
     angle={0.5} 
     intensity={1} 
     penumbra={0.2} 
     castShadow 
   />
   ```

5. **HemisphereLight**:
   ```jsx
   <hemisphereLight 
     skyColor={"#ffffff"} 
     groundColor={"#000000"} 
     intensity={0.5} 
   />
   ```

6. **RectAreaLight**:
   ```jsx
   <rectAreaLight 
     width={5} 
     height={5} 
     color={"#ffffff"} 
     intensity={1} 
     position={[0, 5, 0]} 
     lookAt={[0, 0, 0]} 
   />
   ```

7. **LightProbe**:
   ```jsx
   <lightProbe 
     intensity={1} 
     position={[0, 0, 0]} 
   />
   ```

____

Tags : #3D #react-three-fiber  #webdesign #lighting