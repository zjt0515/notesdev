## 软件环境

1. nasm 汇编编译器
2. bochs 调试虚拟机

ssh连接本地archlinux

```shell
// 更改密码
sudo passwd root
// 查看本地ip
ip add
ssh root@ip
```

创建磁盘

```shell
lsblk
fdisk /dev/sda
n
lsblk
// 格式化
mkfs.ext4 /dev/sda1
// 挂载
mount /dev/sda1 /mnt
```

更新镜像

```shell
pacman -Sy
pacman -Ss mirrorlist
pacman -S pacman-mirrorlist
cat mirrorlist.pacnew | grep China -A 42 > mirrorlist
 pacstrap -i /mnt base base-devel linux linux-firmware  
```

配置系统

```shell
// 生成文件系统表
genfstab -U -p /mnt > /mnt/etc/fstab
// 进入新系统
arch-chroot /mnt
// 安装
pacman -S vim
// 配置文字编码，打开所有zh_CN和 en_US-utf8
vim /etc/locale.gen
// 生成
locale-gen
echo LANG=en_US.UTF-8 > /etc/locale.conf

ln -s /usr/share/zoneinfo/Asia/Shanghai /etc/localtime
hwclock --systohc --localtime
// 设置主机名
echo genshinya > /etc/hostname
```



Archlinux上：

```console
sudo pacman -S nasm
sudo pacman -S bochs
```



## 