

## boot.asm

编译

`nasm -f bin boot.asm -o boot.bin`

boot.bin写入主引导扇区

`dd if=boot.bin of=master.img bs=512 conv=notru`

## GDT

> 实模式下寻址方式不安全，所以在保护模式下需要加一些限制，而这些限制不是一个寄存器能够容纳的，于是这些关于内存段的限制信息被存放在一个叫做全局描述符表（GDT）的结构里
>
> 1. GDT有且只有一个，可以存在在内存中任意位置
> 2. GDTR 48位寄存器，存储GDT内存地址、大小

### 实模式



1. 

## 实验

### INT 0x13中断加载内核

```assembly
load_kernel_from_disk:

  mov bx, MSG_LOAD_KERNEL ; Print message for kernel load.
  call print_string

  ; 设置读取参数
  mov ah, 0x02          ; INT 0x13 功能号：读取扇区
  mov al, 10            ; 每次读取10个扇区
  mov ch, 0             ; 柱面号 (Cylinder) 设为 0
  mov cl, 2             ; 起始扇区号为 2 (第 1 扇区为引导扇区)
  mov dh, 0             ; 磁头号 (Head) 设为 0
  mov dl, [BOOT_DRIVE]  ; 启动盘号 (BIOS在dl中保存)
  ; 设置数据加载地址
  mov bx, KERNEL_OFFSET ; ES:BX 指向内核要加载的位置
  mov es, bx            ; ES = 0x1000 (KERNEL_OFFSET)
  xor bx, bx            ; 偏移地址为 0

  ; 调用 BIOS 中断，读取磁盘
  int 0x13

  ; 读取失败则跳转
  jc disk_error         ; 如果 CF (进位标志) 置位，表示读取失败

  ret

disk_error:
    mov bx, MSG_DISK_ERROR ; 打印 "DISK READ ERROR!"
    call print_string
    hlt                    ; 出错时停机
```

### gdt设置

```assembly
; Part 2
; 设置gdt
; Code for setting up the global descriptor table
; Implement your GDT set up code below
;
gdt_start:
  ; 空描述符
  dd 0x0
  dd 0x0

  ; gdt代码段描述符
  dw 0xFFFF    ; Limit (段界限) 低16位
  dw 0x0000    ; Base (段基址) 低16位
  db 0x00      ; Base 中8位
  db 0x9A      ; Type (代码段，特权级0，存在位)
  db 0xCF      ; Limit 高4位 + 标志位 (4KB 粒度, 32位模式)
  db 0x00      ; Base 高8位

  ; gdt数据段描述符
  dw 0xFFFF    ; Limit (段界限) 低16位
  dw 0x0000    ; Base (段基址) 低16位
  db 0x00      ; Base 中8位
  db 0x92      ; Type (数据段，特权级0，存在位)
  db 0xCF      ; Limit 高4位 + 标志位 (4KB 粒度, 32位模式)
  db 0x00      ; Base 高8位

gdt_end:

gdt_descriptor:
  dw gdt_end - gdt_start - 1 ; GDT长度
  dd gdt_start ; GDT起始地址

```

```assembly
gdt_start:
; 第一个描述符必须是空描述符
gdt_null:
    dd 0
    dd 0
; 代码段描述符
gdt_code:
    dw 0xffff ; Limit (bits 0-15)
    dw 0x0 ; Base (bits 0-15)
    db 0x0 ; Base (bits 16-23)
    db 10011010b ; Access Byte
    db 11001111b ; Flags , Limit (bits 16-19)
    db 0x0 ; Base (bits 24-31)
; 数据段描述符
gdt_data:
    dw 0xffff ; Limit (bits 0-15)
    dw 0x0 ; Base (bits 0-15)
    db 0x0 ; Base (bits 16-23)
    db 10010010b ; Access Byte
    db 11001111b ; Flags , Limit (bits 16-19)
    db 0x0 ; Base (bits 24-31)
; 栈段描述符
gdt_stack:
    dw 0x7c00 ; Limit (bits 0-15)
    dw 0x0 ; Base (bits 0-15)
    db 0x0 ; Base (bits 16-23)
    db 10010010b ; Access Byte
    db 01000000b ; Flags , Limit (bits 16-19)
    db 0x0 ; Base (bits 24-31)
gdt_end:

; GDT descriptior
gdt_descriptor:
dw gdt_end - gdt_start - 1 ; Size of our GDT, always less one of the true size
dd gdt_start ; Start address of our GDT
```

### 实模式切换保护模式

https://mp.weixin.qq.com/s/VGhpbZaeyVwq3Ghs2E6eEw

1. 准备GDT
2. 设置GDTR(写入gdt地址)
3. 配置CR0寄存器，打开保护模式(CR0.PE bit = 1)
4. jmp 跳转 加载段寄存器

```assembly

```



### enter_kernel

```assembly
    ; 设置栈指针，确保内核拥有安全的栈
    mov esp, 0x90000
    ; 设置段寄存器
    mov ax, 0x10        ; GDT 数据段选择子
    mov ds, ax
    mov es, ax
    mov fs, ax
    mov gs, ax
    mov ss, ax

    ; 跳转到 C 内核
    jmp 0x08:_start     ; 0x08 是 GDT 代码段选择子，_start 是 C 内核的入口点
```

```assembly
    ; 设置段寄存器
    mov ax, 0x10      ; 数据段选择子
    mov ds, ax
    mov es, ax
    mov fs, ax
    mov gs, ax
    mov ss, ax
    ; 设置栈
    mov esp, 0x90000  ; 设置栈顶
    mov ebp, esp      ; 设置栈底
    ; 调用C语言内核
    call kernel_main  ; 调用主函数
    ; 如果kernel_main返回，进入死循环
    jmp $            ; 无限循环
```

