# Transformation Continue

## 旋转矩阵的逆等于旋转矩阵的转置

数学上，这样的矩阵叫做正交矩阵

## 用齐次坐标整合平移变换

## 三维变换

Viewing transformation

- View / Camera transfmation 视图变换
- Projection transformation投影变换

用齐次坐标表示三维的点、向量

- 点：(x,y,z,1)
- 向量：(x,y,z,0)

### Use 4x4 matrices for affine transformations 使用4x4矩阵进行仿射变换

第四列前三个元素：平移的量
左上3*3：仍然表示三维的线性变换

> What's the order?
> Linear Transform first or Translation first?
> 先应用线性变换，再加上平移量

### 三维空间的旋转

绕着x轴旋转, x不变, j-hat变成(0,cosa,sina), k-hat变成(-sina,cosa), z轴类似x轴

绕着y轴旋转, y不变, 但其余两个hat的符号在sin上与前两种情况相反

循环对称性质xyzxyzxyzxyzxyz,
xyz yzx zxy
z × x得到y, x × y 得到z, y × z 得到x

#### 简单旋转的复合与复合旋转的分解

R<sub>xyz</sub> = R<sub>x</sub> (α) R<sub>y</sub> (β)R<sub>z</sub> (γ)

罗德里格斯旋转公式
Rotation by angle α around axis n 绕着n轴旋转α角

沿着任意轴旋转：先让该轴移到原点再旋转，最后移动回去

## View / Camera transfmation

模型视图投影变换mvp
model transformation
view transformation
projection transformation

define the camera

- positon _e_  
- Look-at _g_  
- Up direction _t_  

默认位置
_e_ to origin 平移
_g_ to -Z 旋转
_t_ to Y 旋转
物体跟着相机做同样的变换即可

先求逆变换矩阵
Y to _t_
Z to -_g_

再由旋转矩阵的逆等于旋转矩阵的转置可得该变换

## Projection transformation 投影变换

- Orthographic 正交投影
- Perspective 透视投影

正交投影：不会带来近大远小

透视投影：会带来近大远小
[note](https://www.bilibili.com/video/BV1X7411F744/?p=4&vd_source=a6f0ee69351d992f6798c937a32c9968)

### Orthographic 正交投影

放好照相机
将Z轴扔掉
无论XY轴范围多大，物体都移动到[-1,1]

正式做法：
6个数字定义立方体
映射成canonical cube[-1, 1]³：平移到原点后缩放 

![image-20231225215902181](./images/image-20231225215902181.png)

正交矩阵：2个这样的矩阵相乘
第一个矩阵：向原点移动，负号的含义：向原点移动就是取负，比如一开始是正的，向原点就是向负轴移动，一开始负的，负负得正，向正轴移动
第二个矩阵：长宽高都变为2，体积是8，保证立方体在[-1, 1]³

### Perspective Projection 透视投影

数学基础：齐次坐标的定义

- (x, y, z, 1)表示(x, y, z)点，乘上一个非零k，(kx, ky, kz, k)也表示这个点，那么我们可以乘上一个z，(xz,yz,z<sup>2</sup>)也表示这个点
- e.g. (1,0,0,1)和(2,0,0,2)都表示点(1,0,0)

根据相似三角形算出经过挤压之后点的x、y坐标

y' = n/z y

x' = n/z x

![image-20231225224322712](./images/image-20231225224322712.png)

对于(x,y,n,1)也就是近平面上的点坐标都不变
对于(x,y,f,1)也就是远平面上的点x和y变，z不变

#### 确定M<sub>persp->ortho</sub>矩阵的第三行

$$
设n为近平面的z坐标，f为远平面的z坐标
$$

利用远平面的中心点映射后坐标同样不变
$$
\left(
\begin{matrix}
0\\
0\\
f\\
f\\
\end{matrix}
\right)

\rightarrow

\left(
\begin{matrix}
0\\
0\\
f\\
f\\
\end{matrix}
\right)

==

\left(
\begin{matrix}
0\\
0\\
f^2\\
f\\
\end{matrix}
\right)
Af+B=f^2
$$


$$
\begin{cases}
Af+B=n^2\\
Af+B=f^2\\
\end{cases}
\begin{cases}
A=n+f\\
B=-nf
\end{cases}
$$

