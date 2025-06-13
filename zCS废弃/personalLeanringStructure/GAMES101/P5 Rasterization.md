# Rasterization(Triangles) 光栅化

做完观测之后，所有矩阵都在经典的[-1,1]³

## 书接上回



## 1

看向一个区域，定义长宽比和垂直可视角度，可以推出水平角度

## What's after MVP

### 屏幕

屏幕：二维数组，每一个都是小像素，光栅成像设备

- Rasterize：将物体画在屏幕上
- Pixel： picture element

定义屏幕的空间：

- 原点：左下角
- X轴向右
- Y轴向上



：(0,0) to (width-1, height -1)

像素的中心：(x + 0.5, y + 0.5)

屏幕空间：(0,0) to (width, height)

### Canoical Cube to Screen

[-1, 1]² to [0, width] × [0, height] 


$$
视口变换:
M_{viewport}=
\left(
\begin{matrix}
\frac{width}{2} & 0 & 0 &\frac{width}{2}\\
0&\frac{height}{2}&0&\frac{height}{2}\\
0&0&1&0\\
0&0&0&1\\
\end{matrix}
\right)
$$

## 科普：不同光栅显示设备

crt

Frame  Buffer：Memory for a Raster Display

LCD：liquid crystal display

LED：light emitting diode

## 

三角形：

- 最基础的多边形，任何多边形都能拆成三角形
- 三角形内部一定是平面的
- 三角形内部外部是清晰的

## 判断像素中心点和三角形的位置关系

sampling a function

判断像素中心点是否在三角形内
$$
inside(tri,x,y) =
$$

### 具体函数实现

使用三次叉乘判断点是否在三角形内部
按逆时针选取三角形的三个向量，分别叉乘由向量初始点指向待测点所构成的新向量，要求三次结果都为正，如果是按顺时针选取的向量，则要求三次结果都为负

