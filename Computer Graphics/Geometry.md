###### Texture纹理（实际是一组数据）可以是：Environment lighting环境光照，Store microgeometry微观几何，Procedural textures，Solid modeling，Volume rendering...

[[凹凸贴图和法线贴图]] : Bump Map and Normal Map

Displacement Mapping: Use the same texture as in bump map和凹凸贴图一样的纹理，but Actually **moves the vertices** 移动了顶点。

Environment Map环境光照 ：Spherical球形
Cube Map立方体光照：Much less distortion，比起球体有更少的扭曲

###### Implicit and Explicit Geometry隐式和显示几何
- 隐式：Based on classifying point满足某些特定的关系；
- 显示：All points are **given directly** or **via parameter mapping**

- Algebraic Surface代数方法 (implicit)
- Constructive Solid Geometry (implicit) : Combine implicit geometry via Boolean operations(不同几何间的布尔运算：交集并集等)
- Distance function距离函数 (implicit) : Instead of booleans, gradually blend surfaces together using Distance function: giving minimum distance from anywhere to object.
- Level Set Methods水平集(implicit)类似地理的等高线
- Fractals分形(implicit)
