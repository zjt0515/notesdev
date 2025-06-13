# 汇编

## 基本概念

本课程以8086CPU作为平台

### 组成

1. 汇编指令
2. 伪指令
3. 其他符号

### 通用寄存器

8086所有寄存器都是16位=2个字节=4个16进制位
通用寄存器：AX、BX、CX、DX，存放一般性数据
AX-> AH、AL：每个通用寄存器可以分为 **2个独立的**8位寄存器使用

## 汇编工具

### DOSBox使用

启动

```shell
mount c o:masm
c:
debug
-r//显示
-a//开始写代码
xxx
-t//执行刚才写的一行代码
```



### debug instructions(true ad)

register 寄存器

`r`查看 或 改变CPU寄存器
`r ax` 修改axCPU寄存器

assemble 汇编

`a CS:IP`写入汇编指令

`a 2000:0013`在指定内存的位置写入汇编指令

> `-a`之后可以输入n行指令，然后依次输入`t`就可以依次执行 

display 显示

`d [地址] n`查看某个地址中n个数，n用16进制表示
`d [地址]` 查看内存内容

enter 输入

`e [地址] 值`改变内存内容，如果不输入值，那么可以依次修改

trace 跟踪(执行一步)

`t`单步执行
`G`运行

> 每次t之后，会显示下一次输入t之后执行的指令  

unassemble 反汇编

`u [地址]`翻译成汇编指令


`mount c o:masm`将c挂载到指定路径
`c:`进入c
`dir`查看文件ls
``

### 地址

格式：段地址:偏移地址



## hello world

1. 编写asm源程序
2. 编译，生成obj目标文件
3. 连接，生成.exe文件

```bash
# 编译
masm c:\1;
# 连接
link 1;
# 执行
1
```



```assembly
; helloworld.asm
assume cs:codesg
codesg segment
	mov ax,0123H
codesg ends
end
```

![image-20250611155533456](./images/image-20250611155533456.png)

### 汇编指令和伪指令

汇编指令有对应的机器码指令，最终为CPU执行，
伪指令没有对应机器码指令，由编译器执行的指令

> 打开Multisim软件，拿出示波器，信号发生器，电阻，地线符号，连接好电路，点击信号发生器，设置信号参数(Frecency:10kHz,Duty cycle:10%
>
> Amplitude:5Vp Offset:0V).
>
> OptionsL里面点击Sheet Properties,设置网络名
>
> Simulate里面点击Analyses，再点击Fourier，出现傅里叶分析设置窗口，设置相关参数
>
> 最后运行，观察谱线图，按照原始数据表中的数据，依次改变波形和占空比，并重复操作。

