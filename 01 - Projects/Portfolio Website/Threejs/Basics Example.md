##### Imports
___
```javascript
import { useEffect, useRef } from 'react';
import * as THREE from 'three';
```
##### Use of containerRef
___
```javascript

export default function Pixel() {
  const containerRef = useRef(null); 
```

##### Scene Setup
___
Within any three.js scene we need a camera, a renderer, and our scene to actually have anything displayed to us. 

- The Camera is our lens within the scene and exists within the scene. 
- The scene is what it actually present in our 3D  . 
- And the renderer helps us see what is actually in the scene through the cameras pov. 
- 
```javascript

    const scene = new THREE.Scene();
    const camera = new THREE.PerspectiveCamera(90, window.innerWidth / window.innerHeight, 0.1, 1000);
    const renderer = new THREE.WebGLRenderer();
    renderer.setSize(window.innerWidth, window.innerHeight);
    containerRef.current.appendChild(renderer.domElement);
```

##### Creating the geometry
___
```javascript
    const geometry = new THREE.BoxGeometry(1, 1, 1);
    const material = new THREE.MeshBasicMaterial({ color: 0x00ff00 });
    const cube = new THREE.Mesh(geometry, material);
```
##### Scene setup cont. 
___
```javascript
    scene.add(cube);
    camera.position.z = 5;
```

##### Animation 
___
```javascript
    const animate = () => {
      requestAnimationFrame(animate);
      cube.rotation.x += 0.01;
      cube.rotation.y += 0.01;
      renderer.render(scene, camera);
    };
```
##### Returning
___
```javascript
    animate();
  }, []);

  return (
    <div ref={containerRef} />
  );
}
```

----
Tags : #javascript #portfolio-website #threejs 