# Rasterization(Antialiasing and Z-Buffering)抗锯齿和深度缓冲

> Sampling Artifacts (errors/mistakes\inaccuracies) 采样瑕疵

- Jaggies
- Moire
- Wagon wheel effect

本质：信号变化太快，以至于采样跟不上

### Blurred Aliasing

采样之前先模糊化(顺序反过来不行)

![image-20231227222404932](./images/image-20231227222404932.png)

pre-filtering

frequency domain

傅里叶级数展开：任何一个周期函数，写成一系列正弦和余弦函数的线性组合以及一个常数项

![image-20231227223306897](./images/image-20231227223306897.png)

采样频率和函数频率

![image-20231227223712060](./images/image-20231227223712060.png)

走样：同样的采样方法采用2种不同函数，得到的结果无法区分

![image-20231227223952777](./images/image-20231227223952777.png)

### Filtering滤波

 高频黑，低频白

图像信息变化快的地方频率越高

![image-20231227224701017](./images/image-20231227224701017.png)

![image-20231227225012817](./images/image-20231227225012817.png)

### Filtering = Convolution = Averaging

![image-20231227225744406](./images/image-20231227225744406.png)

![image-20231227225817027](./images/image-20231227225817027.png)

时域卷积等于频域乘积