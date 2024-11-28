## color

- const color
- "#hex"
- np.array([114,51,4])

### 颜色转换

## 创建与销毁动画

### 创建

ShowCreation
FadeIn
Write
add

### 销毁

`Uncreate`
`FadeOut`
`remove`

`self.clear()`

https://docs.manim.org.cn/documentation/animation/creation.html#

https://docs.manim.org.cn/documentation/animation/fading.html#

https://docs.manim.org.cn/documentation/animation/growing.html



## 常见Mobject方法



## 位置

### 绝对

`set_x`(*x: float*, *direction: numpy.ndarray = array([0., 0., 0.])*)

将 x 轴坐标设置为 x

### 获取

`get_left`() → numpy.ndarray

获取左边缘中心

`get_bottom`() → numpy.ndarray

获取下边缘中心

`get_height`() → float

获取物件高度

### 移动

二维坐标点(向量)：`np.array([x,y,0])`
8个方向的向量：`UP、RIGHT、LEFT、DOWN、UR、UL、DR、DL`
四边：`TOP、LEFT_SIDE、RIGHT_SIDE、BOTTOM`

默认FRAME_HEIGHT: 8
宽度由长宽比决定



移动：
相对移动`shift(*vector)`
绝对移动`move_to(*vector, aligned_edge: RIGHT)`对齐方式：将物体的右边与该点对齐
移动到角落`to_corner(UL,buff=2)`

### 对齐

- `to_corner`(*corner: numpy.ndarray = array([- 1., - 1., 0.])*, *buff: float = 0.5*)

    和 `corner` 这个角落对齐

- `to_edge`(*edge: numpy.ndarray = array([- 1., 0., 0.])*, *buff: float = 0.5*)

    和 `edge` 这个边对齐

- `align_to(mob, RIGHT)` 与mob的RIGHT边缘对齐，一般使用UL UR DL DR

- `next_to(mob, UP, aligned_edge=LEFT)`紧紧挨着，没有重合，第一个方向表示上下左右关系，第二个方向表示沿着那条边对齐

- `match_x`(*mobject_or_point: manimlib.mobject.mobject.Mobject | numpy.ndarray*, *direction: numpy.ndarray = array([0., 0., 0.])*)

    移动到与 `mobject` 相同的 x 轴坐标


```
# 你可以通过.animate语法来动画化物件变换方法
        self.play(grid.animate.shift(LEFT))
```

### 缩放旋转翻转拉伸变换

## 高亮

https://docs.manim.org.cn/documentation/animation/indication.html#

- 聚焦：`self.play(FocusOn(obj,color=color))`
- 高亮： `self.play(Indicate(mob))`
- 圈中：` self.play(CircleIndicate(obj))`

## 移动

### 方法一

```python
# 由于直接用shift是瞬间移动，必须动画化
self.play(block_list[j].animate.shift(RIGHT * 0.7))
```



## 指针

Arr

## Mobject



- `add`(**mobjects: [manimlib.mobject.mobject.Mobject](https://docs.manim.org.cn/documentation/mobject/mobject.html#manimlib.mobject.mobject.Mobject)*)

    将 `mobjects` 添加到子物体中

- `add_background_rectangle`(*color: ManimColor | None = None*, *opacity: float = 0.75*, ***kwargs*)

    添加背景矩形

- `add_background_rectangle_to_submobjects`(***kwargs*)

    给子物件添加背景矩形

- `add_event_listner`(*event_type: EventType*, *event_callback: Callable[[[Mobject](https://docs.manim.org.cn/documentation/mobject/mobject.html#manimlib.mobject.mobject.Mobject), dict[str]]]*)

    添加事件侦听

- `add_to_back`(**mobjects: [manimlib.mobject.mobject.Mobject](https://docs.manim.org.cn/documentation/mobject/mobject.html#manimlib.mobject.mobject.Mobject)*)

    将 `mobjects` 添加到子物体前面（覆盖关系在下）

- `add_updater`(*update_function: Updater*, *index: int | None = None*, *call_updater: bool = True*)

    添加 `updater` 函数

- `align_on_border`(*direction: numpy.ndarray*, *buff: float = 0.5*)

    以 `direction` 这个边界对齐

- `align_to`(*mobject_or_point: manimlib.mobject.mobject.Mobject | numpy.ndarray*, *direction: numpy.ndarray = array([0., 0., 0.])*)

    对齐例子： `mob1.align_to(mob2, UP)` 会将 `mob1` 垂直移动，顶部与 `mob2` 的上边缘对齐

- `append_points`(*new_points: npt.ArrayLike*)

    添加锚点

- `apply_complex_function`(*function: Callable[[complex], complex]*, ***kwargs*)

    施加一个复变函数

- `apply_function`(*function: Callable[[np.ndarray], np.ndarray]*, ***kwargs*)

    把 `function` 作用到所有锚点上

- `apply_function_to_position`(*function: Callable[[np.ndarray], np.ndarray]*)

    给物体所在的位置执行 `function`

- `apply_function_to_submobject_positions`(*function: Callable[[np.ndarray], np.ndarray]*)

    给所有子物体所在的位置执行 `function`

- `apply_matrix`(*matrix: npt.ArrayLike*, ***kwargs*)

    把 `matrix` 矩阵作用到所有点上

- `apply_points_function`(*func: Callable[[np.ndarray], np.ndarray]*, *about_point: np.ndarray = None*, *about_edge: np.ndarray = array([0., 0., 0.])*, *works_on_bounding_box: bool = False*)

    以 `about_point` 为不变基准点，或以 `about_edge` 为不变基准边，对所有点执行 `func`

- `are_points_touching`(*points: numpy.ndarray*, *buff: float = 0.25*) → bool

    判断某一点是否在本物件的包围框范围内

- `arrange`(*direction: numpy.ndarray = array([1., 0., 0.])*, *center: bool = True*, ***kwargs*)

    将子物件按照 `direction` 方向排列

- `arrange_in_grid`(*n_rows: Optional[int, None] = None*, *n_cols: Optional[int, None] = None*, *buff: Optional[float, None] = None*, *h_buff: Optional[float, None] = None*, *v_buff: Optional[float, None] = None*, *buff_ratio: Optional[float, None] = None*, *h_buff_ratio: float = 0.5*, *v_buff_ratio: float = 0.5*, *aligned_edge: numpy.ndarray = array([0., 0., 0.])*, *fill_rows_first: bool = True*)

    将子物件按表格方式排列`n_rows`, `n_cols` : 行数、列数`v_buff`, `h_buff` : 行距、列距`aligned_edge` : 对齐边缘

- `become`(*mobject: [manimlib.mobject.mobject.Mobject](https://docs.manim.org.cn/documentation/mobject/mobject.html#manimlib.mobject.mobject.Mobject)*)

    重构物件数据并将它变成传入的 `mobject`

- `center`()

    放到画面中心

- `clear_event_listners`(*recurse: bool = True*)

    清空事件侦听

- `clear_points`() → None

    清空物件锚点

- `clear_updaters`(*recurse: bool = True*)

    清空所有的 `updater` 函数

- `compute_bounding_box`() → numpy.ndarray

    计算包围框

- `digest_mobject_attrs`()

    确保所有对象属性都包含在子对象列表中

- `fade`(*darkness: float = 0.5*, *recurse: bool = True*)

    变暗

- `fix_in_frame`()

    将物件锁定在屏幕上，常用于 3D 场景需要旋转镜头的情况

- `flip`(*axis: numpy.ndarray = array([0., 1., 0.])*, ***kwargs*)

    绕 `axis` 轴翻转

- `generate_target`(*use_deepcopy: bool = False*)

    通过复制自身作为自己的 target, 生成一个 target 属性

- `get_all_points`() → numpy.ndarray

    获取物件所有锚点

- `get_ancestors`(*extended: bool = False*) → list

    Returns parents, grandparents, etc. Order of result should be from higher members of the hierarchy down.If extended is set to true, it includes the ancestors of all family members, e.g. any other parents of a submobject

- `get_bottom`() → numpy.ndarray

    获取下边缘中心

- `get_bounding_box`() → numpy.ndarray

    获取物件的矩形包围框（碰撞箱）包含三个元素，分别为左下，中心，右上

- `get_center`() → numpy.ndarray

    获取物件中心坐标

- `get_center_of_mass`() → numpy.ndarray

    获取重心

- `get_color`() → str

    获取颜色

- `get_coord`(*dim: int*, *direction: numpy.ndarray = array([0., 0., 0.])*) → float

    获取物件在 `dim` 维度上的坐标

- `get_corner`(*direction: numpy.ndarray*) → numpy.ndarray

    获取某一个角落

- `get_depth`() → float

    获取物件深度（即 z 轴方向的宽度）

- `get_edge_center`(*direction: numpy.ndarray*) → numpy.ndarray

    获取某一边缘的中心

- `get_end`() → numpy.ndarray

    获取终止点

- `get_event_listners`()

    获取事件侦听

- `get_grid`(*n_rows: int*, *n_cols: int*, *height: Optional[float, None] = None*, ***kwargs*) → [manimlib.mobject.mobject.Group](https://docs.manim.org.cn/documentation/mobject/mobject.html#manimlib.mobject.mobject.Group)

    Returns a new mobject containing multiple copies of this one arranged in a grid

- `get_height`() → float

    获取物件高度

- `get_left`() → numpy.ndarray

    获取左边缘中心

- `get_nadir`() → numpy.ndarray

    获取内边缘中心（这里的内，指垂直于屏幕向内的平面）

- `get_num_points`() → int

    获取锚点数量

- `get_opacity`() → float

    获取透明度

- `get_pieces`(*n_pieces: int*) → [manimlib.mobject.mobject.Group](https://docs.manim.org.cn/documentation/mobject/mobject.html#manimlib.mobject.mobject.Group)

    将物体拆成 `n_pieces` 个部分，便于部分解决 3D 中透视问题

- `get_points`() → numpy.ndarray

    获取物件锚点

- `get_reflectiveness`() → float

    获取反光度

- `get_right`() → numpy.ndarray

    获取右边缘中心

- `get_shader_data`()

    获取 shader 数据

- `get_shader_wrapper`()

    获取 shader 包装

- `get_shader_wrapper_list`() → list

    获取 shader 包装列表

- `get_shadow`() → float

    获取阴影

- `get_start`() → numpy.ndarray

    获取起始点

- `get_start_and_end`()

    获取起始点和终止点

- `get_top`() → numpy.ndarray

    获取上边缘中心

- `get_width`() → float

    获取物件宽度

- `get_x`(*direction=array([0., 0., 0.])*) → float

    获取 x 坐标

- `get_y`(*direction=array([0., 0., 0.])*) → float

    获取 y 坐标

- `get_z`(*direction=array([0., 0., 0.])*) → float

    获取 z 坐标

- `get_zenith`() → numpy.ndarray

    获取外边缘中心（这里的外，指垂直于屏幕向外的平面）

- `has_points`() → bool

    判断是否有锚点

- `is_off_screen`()

    判断是否在画面外

- `length_over_dim`(*dim: int*) → float

    在 `dim` 维度的长度

- `lock_data`(*keys: Iterable[str]*)

    为了加速一些动画，尤其是 Transform，它可以很方便地确认哪些数据片段不会在动画期间改变， 以便调用插值可以跳过这一点，这样它就不会被不必要地读入 shader_wrapper 对象

- `match_color`(*mobject: [manimlib.mobject.mobject.Mobject](https://docs.manim.org.cn/documentation/mobject/mobject.html#manimlib.mobject.mobject.Mobject)*)

    将自己的颜色与 `mobject` 匹配

- `match_depth`(*mobject: [manimlib.mobject.mobject.Mobject](https://docs.manim.org.cn/documentation/mobject/mobject.html#manimlib.mobject.mobject.Mobject)*, ***kwargs*)

    将自己的深度与 `mobject` 匹配（这里的深度指 z 轴方向的宽度）

- `match_height`(*mobject: [manimlib.mobject.mobject.Mobject](https://docs.manim.org.cn/documentation/mobject/mobject.html#manimlib.mobject.mobject.Mobject)*, ***kwargs*)

    将自己的高度与 `mobject` 匹配

- `match_points`(*mobject: [manimlib.mobject.mobject.Mobject](https://docs.manim.org.cn/documentation/mobject/mobject.html#manimlib.mobject.mobject.Mobject)*)

    将自身锚点与 `mobject` 的锚点匹配

- `match_updaters`(*mobject: [manimlib.mobject.mobject.Mobject](https://docs.manim.org.cn/documentation/mobject/mobject.html#manimlib.mobject.mobject.Mobject)*)

    将自己的 `updater` 函数

## 几何

`Line(*vector1, *vector2)`

`Arrow(*vector1, *vector2)`



## VGroup()

`all.arrange(LEFT, aligned_edge=DOWN)`将子物件按向量LEFT的顺序排列，对齐方式为

`add()`
`add_to_back()`
`remove()`

可以对整体移动

arrange(DOWN, center=True, aligned_edge=LEFT)

## 算法与动画制作建议

如果只有交换的操作，那么直接写一个辅助函数swap

如果有前移、后移操作，可以用shift，shift的距离是间距+方块宽度?

