# Rendering-with-Three.JS

## Plan of Action
1. The Basics
2. Fiber
3. Drei
4. Spring
5. Rapier


------------

## 1. The Basics

```js
import * as THREE from "./three.module.min.js";

// 1. Scene
const scene = new THREE.Scene();

// 2. Mesh
const geometry = new THREE.BoxGeometry(1, 1, 1);
const material = new THREE.MeshBasicMaterial({ color: "red" });
const mesh = new THREE.Mesh(geometry, material);
scene.add(mesh); 

// 3. Camera
// The PerspectiveCamera constructor takes four arguments:
// 1. fov (Field of View): The vertical field of view in degrees. A value of 75 means the camera will capture a wide view.
// 2. aspect: The aspect ratio, which is the width of the viewport divided by its height. This ensures the camera's view is correctly proportioned.
// 3. near: The near clipping plane distance. Objects closer than this distance will not be rendered. A value of 0.1 means objects closer than 0.1 units will be ignored.
// 4. far: The far clipping plane distance. Objects further than this distance will not be rendered. A value of 100 means objects beyond 100 units will be ignored.
const camera = new THREE.PerspectiveCamera(75, window.innerWidth / window.innerHeight, 1, 2000);
camera.position.z = 5;
camera.position.x = 1;
camera.position.y = 1;
scene.add(camera);

// 4. Renderer
const canvas = document.querySelector(".draw");  // select the canvas element from the HTML
const renderer = new THREE.WebGLRenderer({ canvas }); // create a new WebGL renderer
renderer.setSize(window.innerWidth, window.innerHeight); // set the size of the renderer to the size of the window
renderer.render(scene, camera); // render the scene and camera
```

![image](https://github.com/user-attachments/assets/48d8572a-6920-4c1a-a6df-7ca2588e25cb)


## References
1. https://threejs.org/
2. https://3dgs-research.vercel.app/
3. https://threejs-journey.com/#summary
4. https://learnwebgl.brown37.net/
5. 
