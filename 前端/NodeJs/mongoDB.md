## MongoDB

https://www.mongodb.com/

1. 关系型数据库
2. NoSQL非关系型

基于分布式文件存储(文档型)的数据库，使用json存储



1. 不需要事先创建数据库和集合
2. 不需要预先定义集合中字段类型和长度
3. 同一个集合中的数据不需要有相同的结构
4. 很容易做到一个字段有多个值



交互式命令终端`mongosh` 

`mongodb://localhost:27107`

## BSON

类似json，但是存在类型 

1. 每个文档最大16MB
2. 每个文档包含一个唯一ID，作为该文档的主键

## 语法

```sql
use game
switched to db game

show dbs
admin                       40.00 KiB
config                     108.00 KiB
local                       40.00 KiB
mongodbVSCodePlaygroundDB   40.00 KiB
// 插入
db.users.insertOne({name: 'zjt'})
{
  acknowledged: true,
  insertedId: ObjectId('67e3a002b8033adcbe26c653')
}
db.users.insertMany([{name: '张三'}, {name: '李四'}])
db.users.find()
db.users.find().limit(2).sort({level: 1/-1})
```



