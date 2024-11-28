# 目标

- 只适用一台设备连接，支持多台设备需要修改adb指令等



## 参考资料

[COC部落冲突自动找鱼 python脚本_部落冲突脚本-CSDN博客](https://blog.csdn.net/weixin_52430761/article/details/128429180)

[android - Awesome Adb——一份超全超详细的 ADB 用法大全 - mzlogin 的专栏 - SegmentFault 思否](https://segmentfault.com/a/1190000006729971)

[PyautoGui 常用教程(一篇就够)-CSDN博客](https://blog.csdn.net/weixin_38640052/article/details/112387653)

[Python3 subprocess | 菜鸟教程 (runoob.com)](https://www.runoob.com/w3cnote/python3-subprocess.html)

[subprocess --- 子进程管理 — Python 3.8.18 文档](https://docs.python.org/zh-cn/3.8/library/subprocess.html#subprocess.run)



[GitHub - xtyzhen/COC_helper_xtyzhen: 可以运行于Windows模拟器下的部落冲突自动捐兵辅助程序。](https://github.com/xtyzhen/COC_helper_xtyzhen)

[OpenCV模板匹配（cv2.matchTemplate）-CSDN博客](https://blog.csdn.net/m0_37579176/article/details/116950903)

## python库和工具

python库

```
from datetime import timedelta
import os
import subprocess
import sys
from transitions import Machine
from util.adb import adb_command, adb_command_full
from game_controller import GameController
import time
import config
import logging
import re
```

- pyautogui
- pillow：图形处理库，将资源数据裁剪出来
- 文字识别：识别战利品信息

### adb

连接安卓模拟器

```shell
//连接安卓模拟器
adb--version

```



模拟鼠标操作

```python
//点击
adb shell input tap x y
//滑动
adb shell input swipe x1 y1 x2 y2 [xxms]
```



- 



图像处理

- numpy：将二进制图像数据读取为数组



### random

生成随机数，用于模拟点击误差

```python
# 随机整数
randint(1,10)
# [0,1)随机浮点数
random()
# [a,b]随机浮点数
uniform(a,b)
```



### logging

生成日志文件

## 流程

### python脚本中执行shell命令

```python
subprocess.run(command,shell=True)
```

### yolo

识别位置不确定的按钮或者元素，例如采集器

### 图像识别

1. 直接定位
2. 模板识别(适用于位置未知，但模板固定，大小固定)
3. yolo

## 防封？

点击位置随机化

时间处理随机化：每个点击事件之后都要sleep