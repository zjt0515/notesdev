## 参考资料

https://threejs.org/docs/index.html#manual/zh/introduction/Installation

https://discoverthreejs.com/zh/book/first-steps/

http://www.hewebgl.com/article/articledir/1

https://github.com/puxiao/threejs-tutorial

## 起步程序

1. 场景
2. 相机
3. 渲染器

> **requestAnimationFrame** 有很多的优点。最重要的一点或许就是当用户切换到其它的标签页时，它会暂停，因此不会浪费用户宝贵的处理器资源，也不会损耗电池的使用寿命。

## 

1. 几何形状geomtery
2. 材质material

光照材质：`Phong/Lambert`

### 材质

基于物理的材质，计算量大，更逼真

1. Standard
2. Physical

### 摄像机

1. 透视摄像机，近大远小
    1. fov
    2. aspect纵宽比
    3. near最近的平面
    4. far最远的平面
2. 正交投影摄像机
    1. 前后左右上下六个面的位置