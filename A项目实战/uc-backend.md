 react+ antdesignpro

后端

- java spring
- mybatis mp
- junit
- mysql

## 链接

1. https://www.code-nav.cn/course/1790943469757837313/section/1791080238927097858?contentType=video&tabKey=info&type=
2. https://pro.ant.design/zh-CN/docs/getting-started/
3. 

## 计划

1. 前端初始化
2. 后端初始化
3. 数据库初始化



## 后端初始化

https://baomidou.com/getting-started/

1. 引入依赖，编辑pom.xml
2. 编辑application.yml，连接数据库
3. 编写model和mapper
4. 编写Tests测试类
5. 启动测试方法

<img src="./images/image-20240905205549504.png" alt="image-20240905205549504" style="zoom:50%;" />

> [!caution]
>
> 使用junit4包下的内容，如@Test
>
> 必须同时在类上添加@RunWith(SpringRunner.class)



> [!caution]
>
> 引入 `MyBatis-Plus` 之后请不要再次引入 `MyBatis` 以及 `mybatis-spring-boot-starter`和`MyBatis-Spring`，以避免因版本差异导致的问题。
>
> 自**3.5.4**开始，在没有使用`mybatis-plus-boot-starter`或`mybatis-plus-spring-boot3-starter`情况下，请自行根据项目情况引入`mybatis-spring`。

## 数据库表设计

主键：id

字段名称设计规范：一般是下划线，驼峰...也行

```sql
id（主键）bigint

username 昵称  varchar

userAccount 登录账号

avatarUrl 头像 varchar

gender 性别 tinyint

userPassword 密码  varchar

phone 电话 varchar

email 邮箱 varchar

userStatus 用户状态 int  0 - 正常

createTime 创建时间（数据插入时间）datetime

updateTime 更新时间（数据更新时间）datetime

isDelete 是否删除 0 1（逻辑删除）tinyint

userRole 用户角色 0 - 普通用户 1 - 管理员

```

```
use uc;
drop table  if exists user;
create table user
(
    uuid          BIGINT auto_increment comment 'id' primary key ,
    user_account  varchar(256)                       null comment '用户账号',
    user_name     varchar(256)                       null comment '用户昵称',
    user_role     tinyint                            null comment '用户身份',
    avatar_url    varchar(256)                       null comment '头像',
    gender        tinyint                            null comment '性别',
    user_password varchar(256)                       not null comment '用户密码',
    phone         varchar(256)                       null comment '电话',
    email         varchar(256)                       null comment '邮箱',
    user_status   int      default 0                         not null comment '用户状态',
    create_time   datetime default current_timestamp null comment '创建时间',
    update_time   datetime default current_timestamp null on update current_timestamp comment '更新时间',
    is_deleted    tinyint  default 0                 not null comment '逻辑删除'
)
    comment '用户';

```

> [!caution]
>
> 



### 索引

## 插件

### mybatisX代码生成器生成model

使用mybatisX插件生成domain实体对象、mapper、mapper.xml(定义mapper对象和数据库的关联)、service、serviceimlp

> 如果数据库字段是驼峰，就勾上actual column

![image-20240910185808572](./images/image-20240910185808572.png)

### SonarLint检查代码规范

安装使用即可

### generatorAllsetter

alt+enter用默认值调用所有setter方法

![image-20240910191047127](./images/image-20240910191047127.png)

### AutoFillcall paremater

自动填充实参  

## 项目结构

- controller：封装成接口允许前端调用
- service：业务逻辑，如登录注册
- mapper：数据库。。。
- model：对应数据库的模型
    - dto
    - vo
- utils：存放工具类

## 测试

为需要测试的类 添加测试类

```java
/**
 * 用户服务测试
 * @author tt
 */
@SpringBootTest
class UserServiceTest {
    @Resource
    private UserService userService;
    @Test
    void testAddUeser(){
        User user = new User();
        user.setUserName("steve");
        user.setUserAccount("11233");
        user.setUserRole(0);
        user.setUserPassword("123456");
        user.setUserStatus(0);

        boolean result = userService.save(user);
        System.out.println(user.getUuid());
        assertTrue(result);
    }
}
```

测试一般需要利用断言

> [!caution]
>
> @TableField
>
> 自动驼峰命名规则映射，将数据库列名下划线命名 -> 驼峰命名

### debug

f9: 到下一个断点的位置

f8: 下一步

## Service逻辑

工具库：Apache Commons Lang/Google grave?/hutool

### 注册逻辑

1. 账户校验
    1. 非空、位数
    2. 不能重复
    3. 不包含特殊字符
2. 密码校验
    1. 非空、位数
    2. 强校验，正则表达式
    3. 密码加密
    4. 密码和(用户)校验密码相同

>对于需要查询数据库的校验，尽量放到后面去

>问题：注入userMapper还是使用this

```java
@Override
    public long userRegister(String userAccount, String userPassword, String checkPassword) {
        // 非空校验
        if (StringUtils.isAnyBlank(userAccount, userPassword, checkPassword)) {
            return -1;
        }
        // 位数校验
        if (userAccount.length() < 4) {
            return -1;
        }
        if (userPassword.length() < 8 || checkPassword.length() < 8) {
            return -1;
        }
        // 账户校验特殊字符
        Pattern pattern = Pattern.compile(SPECIAL_CHARACTERS_PATTERN);
        Matcher matcher = pattern.matcher(userAccount);
        if (matcher.find()) {
            return -1;
        }
        // 密码是否相同
        if (!userPassword.equals(checkPassword)) {
            return -1;
        }
        // 账户不能重复
        QueryWrapper<User> queryWrapper = new QueryWrapper<>();
        queryWrapper.eq("user_account", userAccount);
        long count = userMapper.selectCount(queryWrapper);
        if (count > 0) {
            return -1;
        }
        // 密码加密
        // MessageDigest md5 = MessageDigest.getInstance("MD5");
        final String SALT = "test";
        String encryptPassword = DigestUtils.md5DigestAsHex((SALT + userPassword).getBytes());

        // 插入数据
        User user = new User();
        user.setUserAccount(userAccount);
        user.setUserPassword(encryptPassword);
        boolean saveResult = this.save(user);
        if (!saveResult){
            return -1;
        }
        return user.getUuid();
    }
```

### 登录逻辑

单机登录-> redis单点登录

> 请求类型：Post
> 请求参数很长时不建议Get
>
> 请求体：Json

1. 账户校验

    1. 非空、位数
    2. 不能重复
    3. 不包含特殊字符

2. 密码校验

    1. 非空、位数
    2. 强校验，正则表达式
    3. 密码加密
    4. 密码和(用户)校验密码相同

    

3. 账号
    1. 是否存在
4. 密码
    1. 加密密码是否相等
5. 限流：登录次数过多
6. 返回：脱敏用户信息
7. 记录用户登录态，存入服务器(tomcat/)或者某个服务里（redis/缓存/

> lombok 
>
> @Slf4j
>
> 使用log.记录日志

> 记录用户登录态
>
> 1. 连接服务器端后，session状态返回前端
> 2. 登录成功，获得登录成功session，返回前端一个设置cookie的命令
> 3. 前端设置cookie，保存到浏览器内
> 4. 相同域名再次请求，在请求头中带上cookie
> 5. 后端接受前端的cookie，查找对应的session 
>
> `request.getSession().setAttribute(USER_LOGIN_STATE, safeUser);`
>
> 向request的session的attribute设置一个键值对map



> 配置逻辑删除字段
>
> ```
> @TableLogic
> ```

### 用户管理（用户查询/状态更改







### 用户注销

1. UserService
2. UserServiceImpl
3. UserController



将登录时的操作反向执行即可 

### 增加字段，增加校验逻辑

1. 数据库修改
2. model修改
3. xml修改
4. 请求对象修改
5. controller接口修改
6. service修改 

## Controller接口

> @RestController
>
> 适用于编写 restful 风格的api，返回值默认为json
>
> 
>
> @RequestBody，让框架将前端参数与后端对象进行关联 
>
> 
>
> 配置请求路径：`@RequestMapping("/user")`
>
> @PostMapping("/login")



> 编写请求对象，前端使用Json发送请求，对应后端的对象
>
> ```java
> //model.domain.request
> @Data
> public class UserRegisterRequest implements Serializable {
> 
>     private static final long serialVersionUID = 5435233989292815834L;
> 
>     private String userAccount;
> 
>     private String userPassword;
> 
>     private String checkPassword;
> }
> ```
>
> 

> Controller层校验：
>
> 倾向于对请求参数本身的校验，不涉及业务逻辑，加一次校验增加保险
>
> Service层校验：
>
> 对业务逻辑的校验

### 注册和登录

```java
@RequestMapping("/register")
    public Long userRegister(@RequestBody UserRegisterRequest userRegisterRequest){
        if (userRegisterRequest == null){
            return null;
        }
        String userAccount = userRegisterRequest.getUserAccount();
        String userPassword = userRegisterRequest.getUserPassword();
        String checkPassword = userRegisterRequest.getCheckPassword();
        // 校验
        if (StringUtils.isAnyBlank(userAccount, userPassword, checkPassword)) return null;

        return userService.userRegister(userAccount, userPassword, checkPassword);
    }

    @PostMapping("/login")
    public User userLogin(@RequestBody UserLoginRequest userLoginRequest, HttpServletRequest httpServletRequest){
        if (userLoginRequest == null){
            return null;
        }
        String userAccount = userLoginRequest.getUserAccount();
        String userPassword = userLoginRequest.getUserPassword();
        // 校验
        if (StringUtils.isAnyBlank(userAccount, userPassword)) return null;

        return userService.userLogin(userAccount, userPassword, httpServletRequest);
    }
```

### 

### 查询用户

> 使用Get





### 测试

Tools->HTTP Cilent -> Create Request
或者直接点击方法旁边的绿色图标



> [!caution]
>
> # Data truncated for column 错误
>
> 当修改数据库字段为not null时，如果数据库中对应字段存在null值，就修改不了
>
> 

## 全局反馈对象优化

1. 公共错误码：Error:code
1. 公共错误消息：Error:message
1. 返回对象：泛型，根据具体接口，灵活返回



## 自定义异常？错误码(自定义报错类)



## 全局异常处理类

无论是controller还是service都能捕获  
