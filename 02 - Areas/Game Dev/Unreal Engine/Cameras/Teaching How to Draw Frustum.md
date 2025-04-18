#### What is a Frustum ? 
___
A *frustum* is a geometric figure formed by truncating the top portion of either a cone or a pyramid. It is often used to ( but not limited to ) express how light emits from a surface or to represent a camera's line of sight within a 3D scene. 


While a frustum has many use cases we are more concerned with the latter use case as we can construct a *frustum* from the properties of a camera in 3D space and utilize it to determine what said camera can actually "see". Before we get into how to construct our *frustum*, it is crucial to understand what variables go into producing such a figure in the first place, what those variables represent, and how the variables are utilized within constructing the *frustum*. To lay the groundwork, let’s begin by understanding how a camera object — or any object in 3D space — is positioned and oriented within that space.

Within any 3-Dimensional space, we can refer to any singular point using a corresponding 3x3 matrix which tells us where along the X, Y, Z axis said point is situated. For example, the point (3, 3, 4) tells us how far we need to move from the origin (0, 0, 0) along each axis to reach that location. We've just done something interesting however: we've measured a point’s position **relative to a starting reference point**. This reference point, along with its associated axes, defines what’s known as a _coordinate system_. More often than not the objects within our scene are laid out utilizing  the *World Space* which is the coordinate system wherein all points are positioned relative to a fixed origin — often considered the center of the scene. We can also describe a point relative to our camera's position and orientation; this is called _camera space_, and it allows us to determine how far and in what direction an object is relative to the camera’s point of view.

#### Variables Used to Calculate Frustum 
___
**Field of View**: Field of View is the **extent of the observable world** that is visible at any given moment from a specific position and orientation. It is usually expressed in degrees and defines how much of the world our camera can see. The narrower the angle of view, the less our camera can see. Our Field of View determines how flared out our frustum is and it is used to determine the height of the near/far planes. 

**Aspect Ratio:** This defines the height and width of the image captured by the camera. It’s used to scale the camera’s view to match the proportions of the display or rendering medium (e.g., 16:9, 4:3).

**Near Distance**: This is the distance from our cameras origin to the center of the near clipping plane.

**Far Distance**: This is the distance from our cameras origin to the center of the far clipping plane.

#### Calculating Height and Width of clipping planes
___
The height and width of the near and far clipping planes can be determined using basic trigonometric identities. Since we know the distance from the camera to the center of each plane and the vertical field of view (FOV), we can construct a right-angled triangle where this distance forms the adjacent side, and half the height of the plane forms the opposite side. Using the identity `tan(FOV / 2) = (height / 2) / distance`, we solve for the full height. Once we have the height, the width is calculated by multiplying it by the aspect ratio. This gives us the full dimensions of the clipping planes, allowing us to construct the rectangular bounds of the camera's frustum.
#### Constructing the frustum 
___
Like any object in 3D space, our camera has positional properties that determine where it is located within the world. In addition to its position, the camera also provides directional vectors: a **forward vector** (indicating the direction the camera is facing, typically along the Z-axis), an **up vector** (defining orientation along the Y-axis), and a **right vector** (describing orientation along the X-axis). These vectors form the camera’s local coordinate system. We use them to construct the corners of the near and far clipping planes that we derived earlier, ensuring that each point is placed correctly in world space relative to the camera's orientation.

Let's start the construction of our frustums by placing the points of near clipping plane. We begin by taking the forward vector and scaling it by the near distance, what this does is give us how far in z we should travel to arrive at the center of near clipping plane. We are now in a perfect position to actually construct the points of the plane. 

$$\begin{align*}
\text{Let} \quad 
& \alpha&&= \text{Near Clipping Plane Distance (Scalar Value)} \\
& \beta &&= \text{Near Clipping Plane Width (Scalar Value)} \\
& \gamma&&= \text{Near Clipping Plane Height (Scalar Value)} \\
& \vec{v} &&= \text{Camera Position Vector} \\
& \vec{u} &&= \text{Up Position Vector}\\
& \vec{r} &&= \text{Right Vector}\\
& \vec{t} &&= \text{Forward Position Vector}
\end{align*}$$


$\text{Top-Left Near Plane Point}$ = $\vec{v} + (\vec{t} \cdot \alpha) - \left(\vec{r} \cdot \frac{\beta}{2}\right) + \left(\vec{u} \cdot \frac{\gamma}{2}\right)$
$\text{Top-Right Near Plane Point}$ = $\vec{v} + (\vec{t} \cdot \alpha) + \left(\vec{r} \cdot \frac{\beta}{2}\right) + \left(\vec{u} \cdot \frac{\gamma}{2}\right)$
$\text{Bottom-Right Near Plane Point}$ = $\vec{v} + (\vec{t} \cdot \alpha) + \left(\vec{r} \cdot \frac{\beta}{2}\right) - \left(\vec{u} \cdot \frac{\gamma}{2}\right)$
$\text{Bottom-Left Near Plane Point}$ = $\vec{v} + (\vec{t} \cdot \alpha) - \left(\vec{r} \cdot \frac{\beta}{2}\right) - \left(\vec{u} \cdot \frac{\gamma}{2}\right)$

Similar calculations can be carried out by replacing the near clipping distance, width, and height with their **far clipping** counterparts, allowing us to derive the corresponding points on the far clipping plane.

Once we have defined all eight corner points of the frustum , the final step is simply to connect them — forming the edges of the frustum. How this is drawn or visualized depends on the graphics engine you’re using, but the underlying geometry remains the same. But now that we have this figure the applications are basically endless. For example, we can utilize the geometry formed by the points of the frustum to perform a spatial check to tell whether an object is within bounds of our frustum. 