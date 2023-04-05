#DL 
**[Lecture 3D Vision Michigan](https://www.youtube.com/watch?v=S1_nCdLUQQ8&list=PL5-TkQAfAZFbzxjBHtzdVCWE0Zbhomg7r&index=18)**

### Depth map
 
 RGB + D what is the distance between camera and pixel 
 
 **Possible approach**
 * Fully convolutional network + L2 loss
 * Scale invariant loss
 ![[Pasted image 20230308175240.png]]

**Surface Normals**
* What is the orientation of the surface for each pixel
![[Pasted image 20230308175508.png]]

**Possible approach**
 * Fully conv network + **per-pixel loss**

**Disadvantages**
* Can't represent occluded parts of objects


### Voxel Grid
![[Pasted image 20230308180245.png]]
**Advantages**
* Simple 3D grid

**Disadvantages**
* Need high spatial resolution to capture fine struct
	* Scaling Voxels with *Oct-Trees*
	* *Nested Shape Layers* 
* 
* Scale to high res is not trivial

**How to work**
* 3D convolutions --> Classification
* Generate 3D Voxel grid
	* CNN + 3D CNN + Binary classification
	* *Voxel Tubes* - use only 2D CNN
		* No 3D translation on z axe

2. Implicit surface
3. Pointcloud
4. Mesh

### Implicit surface
3D shape as some function - SDF

**SDF** - Signed Distance Function
![[Pasted image 20230308182110.png]]
* Learn a function to classify arbitrary 3D points as inside / outside the shape
### Pointcloud
Set of points in 3D space
![[Pasted image 20230308182240.png]]
**Advantages**
* Can represent **fine** structures w/o huge numbers of points

**Disadvantages**
* No explicit surface of the shape. To render requires post-processing

**Architectures**
* *PointNet*
	* Run MLP on each point
	* Get features
	* Max-Pool them
	* Fully connected --> Class score
	* **Order not important**
* To generate pointcloud outputs
	* How to measure loss function
		* *Chamfer distance*

### Triangle Mesh

**Advantages**
* Standard for graphics
* Explicitly represents 3D shape
* Adaptive with size
* Can attach RGB, colors, texture coordinates, normals

**Disadvantages**
* Not easy to process with neural nets

**How to process**
* *Pixel2Mesh*
	1. **Iterative mesh refinement**: From simple mesh deforms to object
	2. **Graph convolution**
	3. How to insert image information? --> Vertex aligned features
	4. Loss function: **Convert to pointclouds** --> Champfer loss
### Other
* *F1 score* 
	* Precision and Recall
	 ![[Pasted image 20230308184718.png]]
	 * Precision@t = 3/4, Recall@t = 2/3, F1@t = 0.7
	 * More **robust** than Champfer loss
* *Canonical Coordinates* 
	* Predict in the same coordinates regardless the input
* *View Coordinates* 
	* Predict 3D shape aligned to the viewpoint of the camera
	* **It's better** --> because of better generalisation
* *Datasets*
	* ShapeNet
		* **No context**
		* **Lots of chairs, cars and airplanes**
	* Pix3D
		* **Real images with context**
		* **Small, partial annotations**
* *Mesh R-CNN*
	* Input image --> 2D object recognition --> 3D object voxels --> 3D object meshes
	* **Mesh regularisation**: L2 norm of each edge
* Other domains:
	*  Diff graphics
	* Structure from Motion
	* View Synthesis
	* Multi-view stereo
	* Computing correspondences
	* SLAM

