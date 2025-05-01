# Illmination, Shading, Graphics pipeline

## Z-buffer Complexity

Complexity
- *o(n)* for n triangles (assuming constant converage).
- 对于n个三角形来说复杂度为*o(n)* . (对每个像素求最小值)

**Flat shading, Gouraud shading, Phong shading**



**重心坐标在投影变换下会发生变化**

## Textrue Magnification [[纹理采样与优化]]

### 纹理放大

线性插值  **$lerp(x,v_{0},v_{1})_=v_{0}+x(v_{1}-v_{0})$**
Binear interpolation 双线性插值

### 纹理缩小

MipMap: Allowing(fast, **approx**, **squre**) range queries， 开销 $4/3$

Anisotropic Filtering:各向异性过滤 对矩形区域过滤， 开销3倍

EWA filtering：圆形区域，开销更大
