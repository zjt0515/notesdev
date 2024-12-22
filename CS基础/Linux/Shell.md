##

-

/bin/bash

# Bash Shell

功能

1. command history 补全 alias
2.

## 变量





## 环境变量

通过环境变量获取系统信息、存储临时数据和配置信息

全局环境变量

```shell
# 查看全局变量
env
printenv
# 显示某个变量的值
echo $HOME
# 创建全局环境变量：先创建局部变量，然后导出
export MY_VAR=123
echo $MY_VAR
```

局部环境变量，分为

1. 系统默认的标准局部环境变量，大写
2. 用户自定义局部变量，小写

- 只在定义它的进程中可见

```shell
# 显示特定进程的所有环境变量(全局+局部)
set
# 用户自定义局部变量
my_var=hello
echo $my_var
# 删除环境变量 
unset my_var
```

> [!tip]
>
> $符号
>
> 使用变量时，要用$，即要取到变量内容
>
> 操作变量时，不使用$符号

| 常用全局环境变量 | 描述           |
| ---------------- | -------------- |
| HOME             | 当前用户主目录 |
| SHELL            | 默认的shell    |
| USER             | 登录用户名     |
| UID              | 用户ID         |
|                  |                |

### 数组型环境变量

```shell
 myarr=(1 2 3 4)
 # 显示单个元素
 echo ${myarr[index]}
 # 显示整个数组
 echo ${myarr[*]}
 # 改变值
 myarr[2]=6
 # 删除
 unset myarr[2]
 echo ${myarr[2]}
 unset myarr
 echo ${myarr[*]}
```

# Zsh Shell

