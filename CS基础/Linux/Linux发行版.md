## Ubuntu

## Debian



## CentOS



## WSL2

设置WSL2`wsl.exe --set-version Ubuntu-20.04 2`

检查分配给每个linux发行版的wsl版本`wsl -l -v`

### zsh配置

##

## 配置proxy

- https://learn.microsoft.com/en-us/windows/wsl/networking

1. 查看windows系统ip地址`ipconfig`
2. `export ALL_PROXY="http://[ip]:[端口]"`
    或者`export https_proxy=http://211.83.xxx.xxx:10809 http_proxy=http://211.83.xxx.xxx:10809`

> 因为WSL2基于 Hyper-V 运行，导致 Linux 子系统和 Windows 在网络上是两台各自独立的机器，从 Linux 子系统访问 Windows 首先需要找到 Windows 的 IP



方法二：针对WIndows 11 22H2之后的系统，在`C:\Users\user\.wslconfig`

```.wslconfig
[wsl2]
networkingMode = mirrored
autoproxy = true
```

