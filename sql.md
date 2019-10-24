# sql

## DDL语言

### 库和表的管理

### 常见数据类型

#### 数值型

#####  整型

1. tinyint                       1字节  类似Java中的boolean  
2. samllint                     2字节   
3. mediumint                3字节     
4. int\interger                4字节     int 
5. bigint                        8字节     long

##### 小数型

m: 表示当前小数类型的整数部分+小数的总长度

d:表示小数的取值范围 如果小数长度大于d则会四舍五入

1. 浮点类型
   1. float（m,d） 	4字节		
   2. double(m,d)      8字节
2. 定点数类型
   
1. decimal 			常用于金钱相关的数据存储
   
3. 位类型

   ​	bit                      1-8

#### 字符类型

1. var(m) m为0~255 固定的字符长度     固定长度   只会开辟m长度的空间        浪费空间 
2. varchar(m) m在0~655535的范围       可变长度   根据插入的字符长度开辟    节省空间

#### 日期类型

date日期     4字节     1000-01-01~9999-12-31

time时间     3字节      -838:59:59~838:59:59

year年		1字节		1901-2155

datetime 日期+时间             8个字节 1000-01-01 00:00:00~9999-12-31  23:59:59

timestamp 日期+时间         4个字节   1970年到2038年  1970010108001~2038某个时间  受时区  和sql的版本影响 更加准确反映插入数据的时间

### 常见约束

#### 约束类型

1. not null 非空约束
2. default  默认约束  有默认值 
3. primary key 主键约束 保证字段的值具有唯一性 并且非空
4. unique 唯一 用于保证该字段的值唯一但是可以为空
5. check 检查约束 mysql不支持
6. foreign key 外键约束

#### 列级约束

外键约束不支持

```mysql
CREATE TABLE studentinfo (
	id INT PRIMARY KEY,
	stuName VARCHAR ( 20 ) NOT NULL,
	gender CHAR ( 1 ),
	seat INT UNIQUE,
	age INT DEFAULT 18 
);
```

<img src=".\img\约束.png" alt="约束" style="zoom:50%;" />



#### 表级约束

表级约束不支持not null 和 default约束

```mysql
CREATE TABLE studentinfo(
 id int ,
 studentName VARCHAR(50),
 gender VARCHAR(1),
 seat int ,
 age int ,
 majorId int ,
 CONSTRAINT pk PRIMARY key(id),
 CONSTRAINT ux UNIQUE(seat),
 CONSTRAINT fk_studeninfo_major FOREIGN KEY(majorId) REFERENCES major(id)
)

```

<img src =".\img\表级约束.png" style="zoom:50%;" />

#### 设置约束通用写法

外键使用表级约束方式 别的都是用列级约束

```mysql
CREATE TABLE studentinfo(
 id int PRIMARY KEY ,
 studentName VARCHAR(50) not null ,
 gender VARCHAR(1),
 seat int UNIQUE ,
 age int DEFAULT 18,
 majorId int ,
 CONSTRAINT fk_studeninfo_major FOREIGN KEY(majorId) REFERENCES major(id)
)
```

#### 主键和唯一的对比

|      | 保证唯一性 | 是否为空 | 可以多个 | 是否可以组合 |
| :--: | :--------: | :------: | :------: | :----------: |
| 主键 |     Y      |    N     |    N     |      Y       |
| 唯一 |     Y      |    Y     |    Y     |      Y       |

#### 外键特点

1. 要求在从表上设置外键关系
2. 从表的外键列的类型和主表的关联列的类型要求一致or兼容
3. 主表的关联列表是个key（一般为主键 or unique） 
4. 插入数据的时候先插入主表在插入从表
5. 删除数据的时候先删除从表在删除主表数据

#### 修改表时添加约束

1. 添加表级约束

   alte语法：r table  tablename modify 列名 类型  约束

   ```mysql
   alter table student modify id int primary key
   ```

2. 添加表级的外键约束

   alter  table 表名  add 约束类型 (字段名)  【外键的引用】

    ```mysql
   alter table student add constraint fk_student_major foreign key (majorid) references major(id)
    ```

## TCL语言 

### （事务）

#### 事务的四大特点

1. 原子性：一个事务是不可以再分割，要么都执行要不都不执行
2. 一致性：事务执行会使一个一致状态切换到另外一个一致的状态
3. 隔离性：一个事务的执行是不受其他事务的影响（根据事务的隔离级别）
4. 持久性：一个事务一旦提交后则会永久的的改变数据库中的数据

#### 开启事务

```mysql
#开启事务
SET autocommit = 0;
START TRANSACTION;
UPDATE employees 
SET employees.first_name = '哈哈哈' 
WHERE
	employees.department_id = 100;
# 事务提交
COMMIT
# 事务回滚
ROLLBACK
```

### 视图

一种虚拟存在的表，表中并不存储数据 只会在使用视图的时候动态生成，只保存sql逻辑不保存查询结果

```mysql
# 查询邮箱中包含a字符的员工名 部门名  和工种信息
# 创建视图
CREATE VIEW view1 as 
SELECT e.email,e.last_name,d.department_name,j.job_title from
employees e 
INNER JOIN departments d on e.department_id = d.department_id
INNER JOIN jobs j on j.job_id = e.job_id;

# 使用视图
SELECT * FROM view1 WHERE email like '%a%';
```

#### 视图的修改

语法：create or repalce view 视图名 as 查询语句

语法二：alter view 视图名 as 查询语句

#### 删除视图

drop view  视图名

#### 查看视图

desc  视图名

<img src=".\img\视图.png"  alt="约束" style="zoom:50%;" />







































