## sql-plus

```sql
set linesize 200;
set pagesize 100; 

COLUMN Title FORMAT A10
COLUMN Publisher FORMAT A10
COLUMN Author FORMAT A10

COLUMN CradID FORMAT A10
COLUMN Department FORMAT A10
COLUMN Name FORMAT A10

COLUMN CardID FORMAT A20
COLUMN BorrowDate FORMAT A20
COLUMN Remark FORMAT A20

COLUMN Name FORMAT A20
COLUMN Title FORMAT A20
```

https://juejin.cn/post/6844903822913978381#heading-21

## DCL

### 用户

1. system
2. sys可以创建数据
3. scott学习者

### 创建用户

```sql
create user B22040515 identified by 123456;
```

### 用户授权grant

```sql
grant create session, create table, create view to B22040515;
grant select, update, delete, insert on [table_name] to [user];
GRANT SELECT ANY TABLE, INSERT ANY TABLE, UPDATE ANY TABLE, DELETE ANY TABLE TO B22040515;

ALTER USER B22040515 QUOTA UNLIMITED ON USERS;

```

## DDL

### 建表

```sql
CREATE TABLE DEPT(
  DEPTNO NUMBER(2) CONSTRAINT PK_DEPT PRIMARY KEY,
	DNAME VARCHAR2(14) ,
	LOC VARCHAR2(13)
);

CREATE TABLE EMP(
  EMPNO NUMBER(4) CONSTRAINT PK_EMP PRIMARY KEY,
	ENAME VARCHAR2(10),
	JOB VARCHAR2(9),
	MGR NUMBER(4),
	HIREDATE DATE,
	SAL NUMBER(7,2),
	COMM NUMBER(7,2),
	DEPTNO NUMBER(2) CONSTRAINT FK_DEPTNO REFERENCES DEPT
);

```



```sql
CREATE TABLE Book (
    BookID NUMBER(10) PRIMARY KEY,          -- 图书编号，主键
    CategoryID VARCHAR2(20) NOT NULL,        -- 分类号，不允许为空
    Title VARCHAR2(100) NOT NULL,             -- 书名，不允许为空
    Author VARCHAR2(50),                      -- 作者
    Publisher VARCHAR2(100),                  -- 出版单位
    Price NUMBER(7,2)                         -- 单价（小数）
);
CREATE TABLE Reader (
    CardID NUMBER(10) PRIMARY KEY,            -- 借书证号，主键
    Name VARCHAR2(50) NOT NULL,                -- 姓名，不允许为空
    Department VARCHAR2(100),                  -- 单位
    Title VARCHAR2(20)                         -- 职称
);
CREATE TABLE Borrow (
    CardID VARCHAR2(10) NOT NULL,                -- 借书证号，外键
    BookID NUMBER(10) NOT NULL,                -- 图书编号，外键
    BorrowDate DATE DEFAULT SYSDATE NOT NULL,  -- 借阅日期，默认当前日期
    Remark VARCHAR2(100),                      -- 备注
    PRIMARY KEY (CardID, BookID, BorrowDate),  -- 联合主键：防止同一本书重复借同一天
    FOREIGN KEY (CardID) REFERENCES Reader(CardID), -- 引用完整性：借书证号 -> 读者表
    FOREIGN KEY (BookID) REFERENCES Book(BookID)    -- 引用完整性：图书编号 -> 图书表
);
CREATE TABLE Borrow (
    CardID VARCHAR2(10) NOT NULL,                -- 借书证号，外键
    BookID NUMBER(10) NOT NULL,                 -- 图书编号，外键
    BorrowDate DATE DEFAULT SYSDATE NOT NULL,   -- 借阅日期，默认当前日期
    Remark VARCHAR2(100),                       -- 备注
    CONSTRAINT pk_borrow PRIMARY KEY (CardID, BookID, BorrowDate),  -- 联合主键
    CONSTRAINT fk_borrow_reader FOREIGN KEY (CardID) REFERENCES Reader(CardID),
    CONSTRAINT fk_borrow_book FOREIGN KEY (BookID) REFERENCES Book(BookID)
);
```

### 修改表结构

```sql
ALTER TABLE Reader MODIFY CardID VARCHAR2(10);
```

### 查询table

```sql
SELECT table_name FROM user_tables;
// 管理原
SELECT owner, table_name FROM dba_tables;

```

### drop table

```sql
drop table borrow;
```



## DML

> [!warning]
>
> DML之后需要`commit;`
>
> 或者`SET AUTOCOMMIT ON;`

idus?

### 增insert

```sql
-- 向图书表插入数据
INSERT INTO Book (BookID, CategoryID, Title, Author, Publisher, Price)
VALUES (1, 'TP31', '计算机基础', 'WANG', '高等教育', 17.00);

INSERT INTO Book (BookID, CategoryID, Title, Price)
VALUES (2, 'TP32', '数据库原理', 16.50);

INSERT INTO Book (BookID, CategoryID, Title, Author, Publisher, Price)
VALUES (3, 'TN31', '并行计算机', 'YANG', '清华大学', 12.80);



-- 向读者表插入数据
INSERT INTO Reader (CardID, Name, Department, Title)
VALUES ('T201', 'LIXIN', '计算机系', '中级');

INSERT INTO Reader (CardID, Name, Department, Title)
VALUES ('S981', 'WANG', '通信系', '高级');

INSERT INTO Reader (CardID, Name, Department, Title)
VALUES ('Z003', 'CHEN', '工厂', '初级');

-- 向借阅表插入数据
INSERT INTO Borrow (CardID, BookID, BorrowDate)
VALUES ('T201', 1, TO_DATE('2001-3-10', 'YYYY-MM-DD'));

INSERT INTO Borrow (CardID, BookID, BorrowDate)
VALUES ('T201', 3, TO_DATE('2001-4-1', 'YYYY-MM-DD'));

INSERT INTO Borrow (CardID, BookID, BorrowDate)
VALUES ('S981', 2, TO_DATE('2001-2-20', 'YYYY-MM-DD'));

INSERT INTO Borrow (CardID, BookID, BorrowDate)
VALUES ('Z003', 1, TO_DATE('2001-3-3', 'YYYY-MM-DD'));

```



### 删delete

```sql
DELETE FROM Borrow WHERE CardID LIKE 'S%';
DELETE FROM Reader WHERE CardID LIKE 'S%';
```



### 改updte

`update [table] set column = value [, column = value, ...] where [condition]`

```sql
update Book set Author='ZHANG', Publisher='高等教育' where BookId = 2;
UPDATE Book SET Price = Price * 1.05;
UPDATE Book SET CategoryID = 'TP38' WHERE Title LIKE '%计算机%';
```



### 查select

`select * from Book;`

```sql
SELECT Title, Publisher FROM Book;
-- 查询工厂所有借阅了图书的读者姓名和职称：
SELECT R.Name, R.Title FROM Reader R 
JOIN Borrow B ON R.CardID = B.CardID 
WHERE R.Department = '工厂';
-- 查询藏书中比高等教育出版社所有图书单价更高的书籍：
SELECT Title, Price FROM Book
WHERE Price > (SELECT MAX(Price) FROM Book WHERE Publisher = '高等教育');
-- 查询各出版社图书的最高价、最低价和平均价格：
SELECT Publisher, 
       MAX(Price) AS MaxPrice, 
       MIN(Price) AS MinPrice, 
       AVG(Price) AS AvgPrice
FROM Book
GROUP BY Publisher;
-- 
SELECT R.Name, R.Department
FROM Reader R
JOIN Borrow B ON R.CardID = B.CardID
GROUP BY R.Name, R.Department
HAVING COUNT(B.BookID) >= 5;
```

