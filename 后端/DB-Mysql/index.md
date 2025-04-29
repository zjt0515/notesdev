## DBMS

SQL：Structured Query Language 操作关系型数据库的语言

客户端通过SQL语句向DBMS发送信息

关系型数据库：建立在虚关系模型基础上，由多张相互连接的二维表组成的数据库

- 关系表的设计就是要把信息分解成多个表，一类数据一个表

## 启动

`net start mysql` 启动服务

## 用户

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

### DDL1

数据定义语言，定义数据库对象(数据库，表，字段)

数据库操作

 显示所有数据库 `show databases;`

创建数据库 `create database (if not exists) 库名;`

切换数据库`use 库名`

显示当前数据库 `select database();` 

删除数据库 `drop database (if exists) 库名`

查询当前数据库所有表 `show tables;`



数据表操作

查询表结构 `desc 表名;`

查询建表语句 `show create table 表名;`

修改表名 `rename table 旧表名 to 新表名;`

删除表 `drop table (if exists) 表名`

## Linux

```shell
use mysql;
select host,user from user;

# 更新访问域，允许远程连接
update user set host='%' where user ='root';
```

![image-20241023215509908](./images/image-20241023215509908.png)

配置文件： `/etc/mysql/mysql.conf.d/mysqld.cnf`

