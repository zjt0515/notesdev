# 数据库

数据库排名参考：https://db-engines.com/en/ranking



## DBMS

SQL：Structured Query Language 操作关系型数据库的语言

客户端通过SQL语句向DBMS发送信息

关系型数据库：建立在虚关系模型基础上，由多张相互连接的二维表组成的数据库

- 关系表的设计就是要把信息分解成多个表，一类数据一个表



## 数据库安装

```Mysql	
```

docker

## 启动

`net start mysql` 启动服务

### 登录

`mysql -u<UserName> -p` 登录

> [!caution]
>
> 修改本地mysql密码
>
> https://cloud-tencent-com.translate.goog/developer/article/2093403?_x_tr_sl=zh-CN&_x_tr_tl=en&_x_tr_hl=en&_x_tr_pto=sc

## SQL语句

1. 分号结尾
2. 不区分大小写
3. 注释：# 或 -- 注释内容 /\*注释\*/

列是否区分大小写？



## Linux

```shell
use mysql;
select host,user from user;

# 更新访问域，允许远程连接
update user set host='%' where user ='root';
```

![image-20241023215509908](./images/image-20241023215509908.png)

配置文件： `/etc/mysql/mysql.conf.d/mysqld.cnf`

## 关系型数据库

1. 易于维护、使用方便、支持复杂计算的查询	
2. 读写性能差，灵活性差
3. 各类业务系统、管理系统、安全性要求高的场景

### 关系模型

1. 一对一
2. 一对多
3. 多对多

### ERD图

> Entity Relation Digram 实体关系图

1. 表名
2. key、类型、属性
3. 关联关系(连线)

ERD设计工具

1. Navicat
2. dbDesigner
3. QuickDBD

数据库参考：open.yesapi.cn/list.html

## 非关系型数据库

1. 易于拓展，大文件存储，查询速度快
2. 复杂计算、联合查询效率低
3. 场景：多格式&海量数据、统计排行

## ORM

Object Relation map对象关系映射
