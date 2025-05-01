### Sampling Artifacts(采样失真) in Computer Graphics

#### Artifacts due to sampling - "Aliasing"(走样)

- Jaggies(锯齿) - sampling in space
- Moire - undersampling images
- Wagon wheel effect - sampling in time
- more...
#### Behind the Aliasing Artifacts
- Signals are **==changing too fast==**( high frequency), but **==sampled too slowly==**.


**Antialiasing idea: Blurring(Pre-Filtering) Before Sampling(先模糊后采样)**
1 pixel-width box filter(low pass, blurring)

**Visualizing Image Frequency Content，对图片做傅里叶变换，从时域转为频域。**

图片通常低频位于中心（较多），高频位于外侧（较少）。
high-pass filter(高通滤波)，只有高频信号可以通过，通常为边界。
low-pass filter(低通滤波)，只有低频信号可以通过，缺少细节相对模糊。
经典图像处理（参考课程：数字图像处理），现代图像处理：深度学习。

**Convolution Theorem(卷积理论)**
时域的乘积等于频域的卷积

**How Can We Reduce Aliasing Error?**
- Increase sampling rate
- Antialiasing

**MSAA(multi-sample antialiasing)** :多次采样处理
**FXAA(Fast Approximate AA)**：后期处理，只处理锯齿
**TAA(Temporal AA)**：相邻两帧时间处理

**Super resolution / super sampling**
- From low resolution to high resolution
- Essentially still "not enough samples" problem
- DLSS(Deep Learing Super Sampling)