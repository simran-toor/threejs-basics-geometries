# 09 GEOMETRIES

## WHAT IS A GEOMETRY
* Three.js geometries are composed of vertices (point coordinates in 3D spaces) and faces (trianles that join those vertices to create a surface)
* we use geometries to create meshes
* also used to form particles 
* each vertix corresponds to a particle 

## THE DIFFERENT BUILT-IN GEOMETRIES 
* all built-in geometries are inherited from `BufferGeometry` class which has built in methods like:
    - `translate(...)`
    - `rotateX(...)`
    - `normalize()`
### `BoxGeometry`: create a box 
### `PlaneGeometry`: create a rectangle plane
### `CircleGeometry`: create a disc or portion of a disc (e.g. pie chart)
### `ConeGeometry`: create cone or portion of a cone (can open/close base)
### `CylinerGeometry`: create a cyliner (can open/close ends of cyliner and change radius)
### `RingGeometry`: create flat ring or portion of a flat circle
### `TorusGeometry`: create ring that has a thickness (e.g. donut) or portion of a ring
### `TorusKnotGeometry`: create some sort of knot geometry
### `DodecahedronGeometry`: create a 12 faces sphere (can add details for a rounder sphere)
### `OctahedronGeometry`: 4 faces sphere
### `IcosahedronGeometry`: sphere composed of triangles that have roughly the same size
### `SphereGeometry`: most popular type of sphere where faces look like quads (2 triangles)
### `TubeGeometry`: create tube following a path
### `ExtrudeGeometry`: create an extrusion based on a path (can add and control the bevel)
### `LatheGeometry`: create a vase or portion of a vase (more like a revolution)
### `TextGeometry`: create 3D text (have to provide font in typeface json format)
* can create own geometry in JS or make it in 3D software and export it and import it into project

## BOX EXAMPLE
* Most geometries have parameters, so always look at docs before using it
* `BoxGeometry` has 6 parameters:
    1. `width`: size on `x` axis
    2. `height`: size on `y` axis
    3. `depth`: size on `z` axis
    4. `widthSegments`: how many subdivisions in the `x` axis
    5. `heightSegments`: how many subdivisions in the `y` axis
    6. `depthSegments`: how many subdivisions in the `z` axis
* subdivisions correspond to how much triangles the face in composed of
    - `1` by default (2 triangles per face)
    - if subdivision set to `2`, there will be 9 triangles per face
    ```
    const geometry = new THREE.BoxGeometry(1, 1, 1, 2, 2, 2)
    ```
* add `wireframe: true` to material to show lines hat delimit each triangle
    ```
    const material = new THREE.MeshBasicMaterial({ color: 0xff0000, wireframe: true })
    ```
    - shows 8 triangles per face 
* create `SphereGeometry`:
    ```
    const geometry = new THREE.SphereGeometry(1, 32, 32)
    ```
    - more subdivisions added, the less you can distinguish the faces
    - too many vertices and faces will affect performance 

## CREATING YOUR OWN BUFFER GEOMETRY
* sometimes need to create own geometry 
* if it's very complex or with precise shape better to create in 3D software 
* if not too complex use `BufferGeometry` to build 
    ```
    // Create an empty BufferGeometry
    const geometry = new THREE.BufferGeometry()
    ```
* to add vertices start with a `Float32Array`
    - native JS typed array
    - can only store floats inside
    - length of array fixed 
    - can specify its lenth and fill it later
    ```
    const positionsArray = new Float32Array(9)

    // First vertice
    positionsArray[0] = 0
    positionsArray[1] = 0
    positionsArray[2] = 0

    // Second vertice
    positionsArray[3] = 0
    positionsArray[4] = 1
    positionsArray[5] = 0

    // Third vertice
    positionsArray[6] = 1
    positionsArray[7] = 0
    positionsArray[8] = 0
    ```
* or pass an array 
    ```
    const positionsArray = new Float32Array([
        0, 0, 0, // First vertex
        0, 1, 0, // Second vertex
        1, 0, 0  // Third vertex
    ])
    ```
