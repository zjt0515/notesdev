[前言 — Godot Engine (4.x) 简体中文文档](https://docs.godotengine.org/zh-cn/4.x/about/introduction.html)

#### [GodoterCN——一个温馨友爱的Godot游戏引擎中文社区](https://godoter.cn/)

https://www.youtube.com/watch?v=nAh_Kx5Zh5Q

[与gdscript的API差异 — Godot Engine latest 文档 (osgeo.cn)](https://www.osgeo.cn/godot/getting_started/scripting/c_sharp/c_sharp_differences.html)

[PackedScene实例化 (reimenn.github.io)](https://reimenn.github.io/MyGDSciprtBook/Part-引擎交互/PackedScene实例化.html)

[GDScript/C# Converter (gdscriptformatter.com)](https://www.gdscriptformatter.com/convert)

https://www.bilibili.com/video/BV1nb421Y7Jt/?spm_id_from=333.1007.tianma.2-2-4.click&vd_source=a6f0ee69351d992f6798c937a32c9968

## bug调试

场景有没有保存

## 环境配置：steamGodot(c#)+c#+rider



## voxel



https://github.com/xun69/godot_voxel_chinese_doc

https://github.com/Zylann/godot_voxel

## 玩家移动

### 创建玩家场景

- CharacterBody3D
    - Node3D
        - Character(Node3D类型，3d模型)
    - 碰撞箱CollisionShape3D

### 移动和跳跃脚本

```C#
public override void _PhysicsProcess(double delta)
    {
        //每帧更新velocity
    }
```



## 怪物系统

### 使用池化技术创建销毁实例

### 移动脚本

```c#
public override void _PhysicsProcess(double delta)
    {
        //每帧更新方向
    }
```

### Mob动态生成脚本

### 与玩家交互

1. 设置层名称



## 背包系统



## 地形生成

VoxelTerrain：地形
VoxelViewer：决定地形加载区域

