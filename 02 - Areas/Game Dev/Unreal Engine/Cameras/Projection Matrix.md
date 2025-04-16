Projection of 3D view to 2D. It determines how objects are scaled and flattened onto a 2D space. It is derived as follows...
  $$
\text{Projection Matrix} =
\begin{bmatrix}
a \cdot f \cdot x \\
f \cdot y \\
\lambda \cdot z
\end{bmatrix}
$$

Where:

$$
a = \text{aspect ratio of viewing medium} = \frac{\text{width}}{\text{height}}
$$

$$
f = \text{Field of view scaling factor} = \frac{1}{\tan\left(\frac{\theta}{2}\right)}
$$

$$
z = \text{Normalization of depth} = \frac{z_{\text{far}} + z_{\text{near}}}{z_{\text{far}} - z_{\text{near}}} - \left( \frac{2 \cdot z_{\text{far}} \cdot z_{\text{near}}}{z_{\text{far}} - z_{\text{near}}} \right) \cdot z
$$

We are then left with the final Projection Matrix : 
$$
\text{Projection Matrix} =
\begin{bmatrix}
\frac{a}{\tan(\theta / 2)} & 0 & 0 & 0 \\
0 & \frac{1}{\tan(\theta / 2)} & 0 & 0 \\
0 & 0 & \frac{z_{\text{far}} + z_{\text{near}}}{z_{\text{near}} - z_{\text{far}}} & \frac{2 \cdot z_{\text{far}} \cdot z_{\text{near}}}{z_{\text{near}} - z_{\text{far}}} \\
0 & 0 & -1 & 0
\end{bmatrix}
$$

___
Tags : #programming #game-dev #unreal-engine #cpp