## 系统服务/守护进程 daemons



## systemctl

`systemctl [command] [unit]`

| command                    |                  |      |
| -------------------------- | ---------------- | ---- |
| start/stop                 | 启动/关闭        |      |
| restart                    |                  |      |
| reload                     | 重新载入配置文件 |      |
| enable/disable             | 开机启动/不启动  |      |
| status/is-active/is-enable | 状态查询         |      |

```shell
[root@study ~]# systemctl status atd.service
atd.service - Job spooling tools
Loaded: loaded （/usr/lib/systemd/system/atd.service; enabled）# 开机自动启动

Active: active （running） since Mon 2015-08-10 19:17:09 CST; 5h 42min ago # 运行中
Main PID: 1350 （atd）
CGroup: /system.slice/atd.service
└─1350 /usr/sbin/atd -f
```

Active:

1. active(running)
2. active(exited)  → 仅执行一次
3. active(waiting)  → 等待中
4. inactive



1. enabled
2. disabled
3. static 不可以自己启动
4. mask 无法被启动，除非`systemctl unmask`

## 创建服务配置文件xx.service

```nginx
[Unit]
Description=描述
After=说明跟随xxx启动
Before=说明在xxx启动前启动
Wants=说明启动后最好还要启动的服务
Requires=明确依赖的daemon
Conflicts=冲突项
[Service]
type=
ExecStart=
PrivateTmp=
[Install]
```

```nginx
[Unit]
Description=php-fpm
After=network.target
  
[Service]
Type=forking
ExecStart=/usr/local/php7/sbin/php-fpm
PrivateTmp=true
  
[Install]
WantedBy=multi-user.target
```

Unit → unit自身的描述

Service → 



Install → 安装到的target

1. 