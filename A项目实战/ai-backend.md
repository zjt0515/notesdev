##  模块梳理

1. 用户模块
    1.  
2. 应用模块
3. 题目模块
4. 评分模块
5. 回答模块

##  库表设计

### 所有表的基础字段

```sql
    id              bigint auto_increment comment 'id' primary key,
    createTime      datetime default CURRENT_TIMESTAMP not null comment '创建时间',
    updateTime      datetime default CURRENT_TIMESTAMP not null on update CURRENT_TIMESTAMP comment '更新时间',
    isDelete        tinyint  default 0                 not null comment '是否删除',
```



### 用户表

```sql


```

### 应用表(核心)

```sql
create table if not exists app
(
    appName         varchar(128)                       not null comment '应用名称',
    appDesc         varchar(2048)                      null comment '应用描述',
    appIcon         varchar(1024)                      null comment '应用图标',
    appType         tinyint  default 0                 not null comment '应用类型',
    scoringStrategy tinyint  default 0                 not null comment '评分策略',
    reviewStatus    int      default 0                 null comment '审核状态',
    reviewerId      bigint                             null comment '审核人',
    reviewTime      datetime                           null comment '审核时间',
    userId          bigint                             null comment '创建用户id',
    index idx_appName (appName)
) comment '应用' collate = utf8mb4_unicode_ci
```

1. 需要根据应用名查询，给应用名加索引

### 题目表

将题目内容村为一个json格式

```sql
create table if not exists question
(
    questionContext text   null comment '题目内容(json)',
    appId           bigint not null comment '应用id',
    userId          bigint not null comment '创建用户id',
    index idx_appId (appId)
) comment '题目' collate = utf8mb4_unicode_ci;
```

### 评分结果表

```sql
create table if not exists result
(
    resultName       varchar(128)  not null comment '结果名称',
    resultDesc       text          null comment '结果描述',
    resultPicture    varchar(1024) null comment '结果图片',
    resultProp       varchar(128)  null comment '结果属性集合',
    resultScoreRange int           null comment '结果得分范围',
    appId            bigint        not null comment '应用id',
    userId           bigint        not null comment '创建 用户id',
    index idx_appId (appId)
) comment '评分结果' collate = utf8mb4_unicode_ci;
```

### 用户答题记录表

```sql
create table if not exists user_answer
(
    appId           bigint            not null comment '应用id',
    appType         tinyint default 0 not null comment '题目类型',
    scoringStrategy tinyint default 0 not null comment '评分策略',
    choices         text              null comment '用户答案(JSON数组)',
    resultId        bigint            not null comment '结果id',
    resultName      varchar(128)      null comment '结果名称',
    resultDesc      text              null comment '结果描述',
    resultPicture   varchar(1024)     null comment '结果图标',
    resultScore     int               null comment '得分',
    userId          bigint            not null comment '用户id',
    index idx_appId (userId)
) comment '用户答题记录' collate = utf8mb4_unicode_ci;
```

> 为什么有了id，还要存储别的表的数据？
>
> 冗余设计，创建了之后部分字段不会发生更新，减少联表查询次数，提高性能

## 应用业务梳理

### APP

1. 创建：校验数据
2. 根据id查询
3. （根据请求）分页查询列表：仅限管理
4. （根据请求）分页查询封装列表
5. 分页查询列表（当前用户创建的）
6. 编辑：用户或管理使用
7. 更新：仅限管理
8. 审核：仅限管理
9. 删除：仅限本人或管理

### 常见Request类

appRequest，注意，这里的字段名最好与app实体类的字段名称保持一致

1. appAddRequest：创建请求类，根据业务自定义
2. appUpdateRequest：更新类
    1. id
    2. ...

通用类

1. deleteRequest
    1. id
2. 



## 后端项目初始化

使用模板完成基本初始化

### mybatisX生成model-entity和mapper

修改entity：

1. 修改主键生成逻辑：`@TableId(type = IdType.ASSIGN_ID)`
2. 添加逻辑删除注解

# 基础业务流程

1. 用户注册登录
2. 用户创建应用 创建题目 创建评分规则
3. 管理员管理应用， 审核发布下架应用
4. 用户查询检索应用列表，在线答题，提交回答
5. 用户查看评分结果

# 

## 业务逻辑代码生成

使用codeGenerator生成模板代码

1. 构建枚举类（针对数据库，替换0 1）
    1. 应用类型
    2. 评分策略
    3. 审核状态

1. 修改dto
    1. 删除不必要的字段，一般只有需要前端用户输入的才留着
    1. 如果是数组类型，数据库存储String，dto就要修改为`List<String>`方便前端传参
    1. 如果是json类型，就要自定义dto对象

1. 修改vo
    1. 删除无用字段，字段类型修改

    1. 实现转换方法：如果2.2出现了，就必须转换

1. 写controller接口
    1. 比较简单的接口可以不用在service中再写一层



> 枚举类写法
>
> 定义字段，一般要有解释的String和数据int
>
> 辅助方法：
>
> - getEnumByValue
> - getValues：获取所有枚举值，展示用
>
> 注意：只有当枚举类需要频繁增删改查的时候，才要使用建表代替

## Controller

1. 需要将dto的字段参数设置到实体类中，其中部分字段可能需要进行转换(一般是增改(编辑))
2. 同时对dto参数进行初步的校验
3. 填充默认值：获取基本参数，补充到实体类中，一般是userId等字段
4. 写入数据库
5. 返回基本响应给前端

## serviceImpl

主要是参数校验，业务逻辑

首先必须获取全部参数，一个一个抉择

1. 一般字段，都要校验非空和长度
2. 对于冗余字段，一般不用校验？？？
3. 对于枚举类，要校验是否属于我们定义的枚举类



### 根据查询请求=》生成查询QueryWrapper

首先必须获取请求对象全部参数，一个一个抉择

对于不同的字段，查询方式不同，分为精确、模糊查询、从字段中搜索、JSON数组查询等等

> 多字段查询：查询多个字段，只要存在要查找的值，就能查询到

Mapsject???等骚操作？？？

### 获取封装类

1. 调用VO类的转换方法
2. 为封装对象补充值，不需要的也可以删除

### 分页获取封装类





## 通用能力

### FileController

上传图片功能

# 后端核心逻辑开发

1. 应用模块
    1. 管理员审核下架
2. 评分模块
    1. 根据回答计算评分结果
    2. 自定义测评规则
    3. 自定义打分规则
3. 回答模块

## 审核逻辑

> 管理员查询未审核的app，查到信息
>
> 点击审核完毕按钮=>
>
> 更新app的审核信息
>
> 1. 审核状态
> 2. 审核人
> 3. 

相关字段：

1. id
2. reviewStatus
3. reviewMessage
4. 序列化

### 写接口



## 评分模块实现

策略模式

