# Rendering with Three.JS - Part I

## Plan of Action
1. [Hello, Cube!](#hc)
2. [Transformations](#t)
3. [Animations](#a)
4. [Cameras](#c)
5. [Geometries](#g)
6. [Textures](#tx)
7. [Materials](#m)


------------
<a name="hc"></a>
## 1. Hello, Cube!
In this "Hello, World!" example, we will show how to render a cube with Three.JS. For thatwe need four elements: **a scene, an object, a camera and a renderer**. And voila!

### 1.1 The Scene
The Scene is this **container** where we want to add all our objects, cameras, models etc for Three.JS to render. 

```js
// Scene
const scene = new THREE.Scene() // A scene is a container for all objects
```

### 1.2 The Object
We want to render an Object in our Scene. What is this object? It can be a mesh or particles or lights etc,.. In our case, we want our object to have the geometry of a cube and a material of color "yellow". We will then build a Mesh from the geometry and material. Finally, we would want to add that objct to our scene in order to be rendered.

```js
const geometry = new THREE.BoxGeometry(1, 1, 1) // 1 meter wide, 1 meter high, 1 meter deep
const material = new THREE.MeshBasicMaterial({ color: 'yellow' }) // material of color yellow
const mesh = new THREE.Mesh(geometry, material) // A mesh is a combination of a geometry and a material
scene.add(mesh) // Add the mesh to the scene
```

### 1.3 The Camera
The camera is the ```point of view``` we want to render our scene. We will use a **Perspective Camera** type with FOV of ```75 deg``` and the aspect ratio defined below. Similarly, we will need to add the camera to the scene.

``` js
const sizes = {
    width: 800,
    height: 600
}

const camera = new THREE.PerspectiveCamera(75, sizes.width / sizes.height) // 75 degrees field of view, aspect ratio of the width to the height
scene.add(camera) // Add the camera to the scene
```


### 1.4 The Renderer
The job of the renderer is to render the scene from the camera's point of view which will be displayed on a **canvas**. We can add a canvas to the HTML file and send it to the renderer. We will use ```WebGLRenderer``` to create the renderer.

```js
// Canvas
const canvas = document.querySelector('canvas.webgl') // Get the canvas element

const renderer = new THREE.WebGLRenderer({
    canvas: canvas
}) // Create a renderer that will render the scene to the canvas
renderer.setSize(sizes.width, sizes.height) // Set the size of the renderer to the size of the canvas
renderer.render(scene, camera) // Render the scene to the canvas
```

When we first render our scene, we have a black render because the object and the camera are all at the location. 

<p align="center">
  <img src="https://github.com/user-attachments/assets/b8981b88-a959-4b0b-873b-e6bf2ba0c961" width="50%" />
</p>


```js
camera.position.z = 3 // 3 meters away from the scene
```

In order to see the cube, we can move the camera and/or move the object. We can control the ```x```, ```y``` and ```z``` direction for both the camera and object we want to move. And tadaa!!!

```js
mesh.position.x = .5 // .5 meters to the right
mesh.rotation.y = .5 // .5 radians (28.65 degrees) around the y-axis
```
<p align="center">
  <img src="https://github.com/user-attachments/assets/1e097199-572f-46c6-9f2c-74a7cfaf3bf4" width="50%" />
</p>




------------
<a name="t"></a>
## 2. Transformations

```js
const axesHelper = new THREE.AxesHelper(2) // create a new axes helper with a size of 2
scene.add(axesHelper) // add the axes helper to the scene as it is an object
```

### 2.1 Position

```js
mesh.position.z = -1
mesh.position.x = 0
mesh.position.y = 1
```


<table>
  <tr>
    <th></th>
    <th>-1</th>
    <th>0</th>
    <th>1</th>
  </tr>
  <tr>
    <td>Changing X</td>
    <td><img src="https://github.com/user-attachments/assets/5522fe73-8dc8-4c61-b0e4-fc552ce3d232" alt="Image -1, Row 2" width="150"></td>
    <td><img src="https://github.com/user-attachments/assets/fb6c2899-e32d-4f80-9b60-3d85d69086a0" alt="Image 0, Row 2" width="150"></td>
    <td><img src="https://github.com/user-attachments/assets/663f8e6f-1763-4520-b408-ef648293b5d0" alt="Image 1, Row 2" width="150"></td>
  </tr>
  <tr>
    <td>Changing Y</td>
    <td><img src="https://github.com/user-attachments/assets/44eea150-1345-48b0-8b52-a0d94da18d11" alt="Image -1, Row 1" width="150"></td>
    <td><img src="https://github.com/user-attachments/assets/b1c68b1d-1749-4ace-9dab-24f9cc640a05" alt="Image 0, Row 1" width="150"></td>
    <td><img src="https://github.com/user-attachments/assets/592368b6-30f9-446e-b72d-4e25a3890088" alt="Image 1, Row 1" width="150"></td>
  </tr>
  <tr>
    <td>Changing Z</td>
    <td><img src="https://github.com/user-attachments/assets/35e2e778-936b-4db3-874b-8b5448702b09" alt="Image -1, Row 3" width="150"></td>
    <td><img src="https://github.com/user-attachments/assets/6e370754-5ff3-4c9a-a6da-ad6dd08dbe97" alt="Image 0, Row 3" width="150"></td>
    <td><img src="https://github.com/user-attachments/assets/b7cace68-069b-4f63-9c38-1fa03093ed36" alt="Image 1, Row 3" width="150"></td>
  </tr>
</table>


```js
console.log(mesh.position.length()) // get the length of the vector from the origin to the mesh
```

```js
console.log(mesh.position.distanceTo(camera.position)) // get the distance between the mesh and the camera
```


### 2.2 Scale

### 2.3 Rotation



------------










## References
1. https://threejs.org/
2. https://3dgs-research.vercel.app/
3. https://threejs-journey.com/#summary
4. https://learnwebgl.brown37.net/
5. 
