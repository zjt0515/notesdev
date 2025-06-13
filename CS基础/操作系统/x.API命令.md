```shell

gcc -Wl,--verbose hello.c -static // -Wl, --verbose 查看所有链接选项
gcc -Wl,--verbose hello.c -static | less // --verbose查看所有编译选项

// 拆开来
gcc -c hello.c && ld hello.o
```

## signal.h

`signal(sig,func)`进程控制软中断信号

