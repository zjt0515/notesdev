## 1. **数据类型不同**



| 功能         | Oracle                                                | MySQL                                       |
| ------------ | ----------------------------------------------------- | ------------------------------------------- |
| 字符串类型   | `VARCHAR2(n)`                                         | `VARCHAR(n)`                                |
| 日期时间类型 | `DATE`（日期+时间）                                   | `DATE`（只有日期）+ `DATETIME`（日期+时间） |
| 自动增长字段 | `序列 (SEQUENCE)` + `触发器` 实现                     | `AUTO_INCREMENT`                            |
| 布尔类型     | 没有专门的`BOOLEAN`类型，需要用`CHAR(1)`或`NUMBER(1)` | 有`BOOLEAN`（实质是TINYINT(1))              |

------

## 2. **函数不同**



| 功能       | Oracle                         | MySQL                             |
| ---------- | ------------------------------ | --------------------------------- |
| 字符串拼接 | 用 `                           |                                   |
| 取子串     | `SUBSTR(列名, 起始位置, 长度)` | `SUBSTRING(列名, 起始位置, 长度)` |
| 取系统日期 | `SYSDATE`                      | `NOW()`                           |
| 空值处理   | `NVL(expr1, expr2)`            | `IFNULL(expr1, expr2)`            |

------

## 3. **事务控制默认行为不同**

- **Oracle**：
    - 默认手动提交（`commit`）。
    - 不提交，断开连接时自动 `rollback`。
- **MySQL**：
    - 取决于存储引擎：
        - `InnoDB`支持事务，需要手动 `commit`。
        - `MyISAM`不支持事务，自动提交。

------

## 4. **约束写法稍有不同**

- 外键约束在 Oracle 里经常写得更完整，比如明确指定 `ON DELETE CASCADE`。
- MySQL里定义外键，有时候需要手动设置存储引擎为 `InnoDB`。

------

## 5. **分页查询不同**



| 功能     | Oracle                                   | MySQL                 |
| -------- | ---------------------------------------- | --------------------- |
| 分页查询 | `ROWNUM` / `OFFSET...FETCH` / 子查询包装 | `LIMIT offset, count` |

- **Oracle示例**（老版写法）：

    ```
    sql复制编辑SELECT * FROM (
        SELECT a.*, ROWNUM rnum FROM (SELECT * FROM 表) a
        WHERE ROWNUM <= 20
    )
    WHERE rnum > 10;
    ```

- **MySQL示例**：

    ```
    sql
    
    
    复制编辑
    SELECT * FROM 表 LIMIT 10, 10;
    ```

------

## 6. **视图、索引、触发器**

- 都支持，但语法细节略有不同。
- Oracle对视图、触发器、存储过程支持得更强大更严谨。

------

## 7. **权限管理和角色**

- Oracle权限划分特别细，例如`CREATE SESSION`、`CREATE TABLE`等。
- MySQL主要是基于用户+库+表授权，不那么细颗粒。

## 8. **系统表/数据字典查询方式不同**

- Oracle系统表查询示例：

    ```
    sql复制编辑SELECT * FROM USER_TABLES;
    SELECT * FROM ALL_OBJECTS WHERE OBJECT_TYPE = 'TABLE';
    ```

- MySQL系统表查询示例：

    ```
    sql复制编辑SHOW TABLES;
    DESCRIBE 表名;
    ```

------

## 总结一句话：

> **MySQL简单快速，适合小型项目；Oracle专业严谨，适合大型复杂系统。**

