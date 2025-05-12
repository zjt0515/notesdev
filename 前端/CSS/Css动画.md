https://h-wakanda.github.io/css-animation-101-cn/



## transition

过渡：从一个“状态”到另一个“状态”的动画模拟，A to B

触发方式：

1. 鼠标悬停
2. js添加/删除样式类

```
transition: [property] [duration] [delay] [timing-function];
```

| transition属性 | 描述                                                 |
| -------------- | ---------------------------------------------------- |
| Property       | 需要过渡的css属性                                    |
| duration       | 持续时间 xs                                          |
| delay          | 延迟时间，开始前的等待时间                           |
| Time-function  | 时间函数，描述属性值变化速度<br />本质都是被塞尔曲线 |

time-function

1. Linear 线性
2. Ease-in  慢-快
3. Ease-out 快-慢，适合屏外-内
4. Ease-in-out 慢-快-慢，适合加载
5. Cubic-bezier

> [!caution]
>
> 不能使用过渡效果的css属性：
>
> 1. font-family



### animation

过渡（transition）和动画（animation）是相似的。两者都是 CSS 的属性，并且都可以通过持续时间（duration），延迟（delay）以及其他属性控制浏览器制作动画效果。