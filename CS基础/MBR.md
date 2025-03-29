## BIOS

Base input and output systerm

ROM映射在0xF0000~0xFFFFF

bios的入口地址在0xFFFF0

开机一瞬间，CPU 的 cs：ip 寄存器被强制初始化为 0xF000：0xFFF0

实模式下：物理地址=段地址*16+偏移地址

## 实模式

默认用到的寄存器都是16位宽

### 实模式内存布局

20条地址线下，2^20^=1MB，0x00000 ~ 0xFFFFF

### 实模式CPU内存寻址

寻址方式

1. 寄存器寻址
2. 立即数寻址
3. 内存寻址

内存寻址

1. 直接寻址
2. 基址
3. 变址
4. 基址变址寻址



## 主引导记录MBR

扇区末尾的两个字节分别是魔数 0x55 和 0xaa，BIOS 便认为此扇区中确实存在可执 行的程序（在此先剧透一下，此程序便是久闻大名的主引导记录 MBR），便加载到物理地址 0x7c00，随 后跳转到此地址，继续执行。

1. 本身大小512B，加上栈的空间



创建硬盘镜像

`/your_path/bochs/bin/bximage -q -hd=16 -func=create -sectsize=512 -imgmode=flat master.img`

boot.bin写入主引导扇区

`dd if=boot.bin of=master.img bs=512 count=1 conv=notrunc`

## NASM

`nasm -f <format> <filename> [-o <output>]`

`nasm -f bin boot.asm -o boot.bin`

> 伪指令：编译器定义的，cpu看不懂，只是方便开发人员写代码
>
> nasm中的伪指令：
>
> 1. $: 当前行
>    1. $$：当前section

