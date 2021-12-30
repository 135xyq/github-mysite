---
title: Oracle期末知识点总结
date: 2021-12-30 18:53:02
description: Oracle知识点总结
categories: "Oracle" #分类
tags:   #标签
    - oracle
    - 课程学习
---
# Oracle知识点总结


## [索引](https://www.cnblogs.com/wishyouhappy/p/3681771.html)

### 创建索引
```plsql
CREATE [UNIQUE] | [BITMAP] INDEX index_name  --unique表示唯一索引
ON table_name([column1 [ASC|DESC],column2    --bitmap，创建位图索引
[ASC|DESC],…] | [express])
[TABLESPACE tablespace_name]
[PCTFREE n1]                                 --指定索引在数据块中空闲空间
[STORAGE (INITIAL n2)]
[NOLOGGING]                                  --表示创建和重建索引时允许对表做DML操作，默认情况下不应该使用
[NOLINE]
[NOSORT];                                    --表示创建索引时不进行排序，默认不适用，如果数据已经是按照该索引顺序排列的可以使用
```



```plsql
为student1表的“注册日期”创建索引，并以降序排列，索引名为“DX1_02”。
create index DX1_02 on student1(注册日期 desc);
```

### 删除索引

```plsql
drop index index_sno;
```
### 查看索引

```plsql
select index_name,index-type, tablespace_name, uniqueness from all_indexes where table_name ='tablename';

 -- eg:    
create index index_sno on student('name');
select * from all_indexes where table_name='student';
```


## [同义词](https://www.cnblogs.com/moonsoft/p/12364941.html)

Oracle的同义词（synonyms）从字面上理解就是别名的意思，和视图的功能类似

### 创建公共同义词
```plsql
create public synonym synonym_name for table_name;
```

### 创建普通的同义词
```plsql
create  synonym synonym_name for table_name;
```

### 删除同义词
```plsql
drop synonym synonym_name;
```
## [序列](https://www.cnblogs.com/CandiceW/p/10062413.html)

序列(SEQUENCE)是序列号生成器，可以为表中的行自动生成序列号，产生一组等间隔的数值(类型为数字)。不占用磁盘空间，占用内存。其主要用途是生成表的主键值，可以在插入语句中引用，也可以通过查询检查当前值，或使序列增至下一个值。

### 创建序列
创建序列需要CREATE SEQUENCE系统权限。序列的创建语法如下：
```plsql
　　CREATE SEQUENCE 序列名
　　[INCREMENT BY n]
　　[START WITH n]
　　[{MAXVALUE/ MINVALUE n| NOMAXVALUE}]
　　[{CYCLE|NOCYCLE}]
　　[{CACHE n| NOCACHE}];
```
#### 其中：

1. > INCREMENT BY用于定义序列的步长，如果省略，则默认为1，如果出现负值，则代表Oracle序列的值是按照此步长递减的。

2. > START WITH 定义序列的初始值(即产生的第一个值)，默认为1。

3. > MAXVALUE 定义序列生成器能产生的最大值。选项NOMAXVALUE是默认选项，代表没有最大值定义，这时对于递增Oracle序列，系统能够产生的最大值是10的27次方;对于递减序列，最大值是-1。

4. > MINVALUE定义序列生成器能产生的最小值。选项NOMAXVALUE是默认选项，代表没有最小值定义，这时对于递减序列，系统能够产生的最小值是?10的26次方;对于递增序列，最小值是1。

5. > CYCLE和NOCYCLE 表示当序列生成器的值达到限制值后是否循环。CYCLE代表循环，NOCYCLE代表不循环。如果循环，则当递增序列达到最大值时，循环到最小值;对于递减序列达到最小值时，循环到最大值。如果不循环，达到限制值后，继续产生新值就会发生错误。

6. > CACHE(缓冲)定义存放序列的内存块的大小，默认为20。NOCACHE表示不对序列进行内存缓冲。对序列进行内存缓冲，可以改善序列的性能。

7. > NEXTVAL 返回序列中下一个有效的值，任何用户都可以引用。

8. > CURRVAL 中存放序列的当前值,NEXTVAL 应在 CURRVAL 之前指定 ，二者应同时有效。


 创建序列，该序列起始值50，步长为10，不缓冲，序列名为“DX1_06”。
```plsql
create sequence DX1_06 increment by 10 start with 50 nocache;
```

创建序列，该序列起始值为1000，步长为2，最大值为10000，不可循环，序列名为“seq_1”。
```plsql
create sequence seq_1 increment by 2 start with 1000  maxvalue 10000 nocycle;
```

### 修改序列
 **alter**

修改序列“DX1_06”，将该序列最大值设为“82000”，最小值设为“10”，步长设为“5”。
```plsql
alter sequence DX1_06 maxvalue 82000 minvalue 10 increment by 5;
````

### 删除序列
**drop**

删除序列seq_1。
```plsql
drop sequence seq_1;
```

### 一些常用函数

#### [查询一张表，而且要按照业务排序](https://www.cnblogs.com/mycoding/archive/2010/05/29/1747065.html)
  ```rank() over(partition)```

### [从右边对字符串使用指定的字符进行填充 ](https://www.cnblogs.com/BetterWF/archive/2012/07/18/2597472.html)
```rpad(string,padded_length,[pad_string]) 　```
-  string 表示：被填充的字符串 　　
-  padded_length 表示：字符的长度，是返回的字符串的数量，如果这个数量比原字符串的长度要短，rpad函数将会把字符串截取成从左到右的n个字符; 　　
- pad_string 是个可选参数，这个字符串是要粘贴到string的右边，如果这个参数未写，lpad函数将会在string的右边粘贴空格。 　


## [存储过程](https://blog.csdn.net/qq_39443053/article/details/104044530)

### 存储过程的定义
#### 无参数
```plsql
create or replace procedure 存储过程名
as
begin
  ----------------------------
end;
```

#### 有参数
```plsql
create or replace procedure myDemo02(name in varchar,age in int)
as
begin
  dbms_output.put_line('name='||name||', age='||age);
end;
```

## 知识点
1. 主键的创建有三种方法
2. 视图上不能完成的操作：在视图上定义新的基本表
3. 在sql中子查询是嵌入到另一个查询语句之中的查询语句
4. 减少外键能实现实体的完整性
5. 在全文的搜索的函数中，用于指定被搜索的列是match()
6. 中间连接不属于连接种类
7. 连接种类有：外连接、内连接、交叉连接
8. union可以组合多条SQL查询语句，形成组合查询
9. 分组：grouped by     ？？？
10. delete语句的使用DELETE FROM Person WHERE LastName = 'Wilson' 
11. 返回当前日期的函数：curdate()
12. 数据模型：网状模型、层次模型、网络模型
13. 交叉连接又可以看成笛卡尔连接
14. 为数据表创建索引的目的是提高查询的检索性能
15. SQL语言中的视图view是数据库的外模式
16. 查看数据库中的所有表：show tables
17. start transaction 表示一个新的事物处理快的开始
18. 格式化日期的函数：DATE_FORMAT()
19. SQL语言是非过程化语言
20. 在正则表达式中匹配任意一个字符的符号是' . '
21. DML语句就是数据库操作语句。包括update、 delete、select
22. DDL数据库定义语言。包括create、alter、drop、truncate
23. declimal是可变精度浮点值
24. 逻辑运算符优先级：not / and / or
25. [limit](https://www.yiibai.com/sql/sql-limit.html)































## 索引

### 创建

#### 单索引

``````sql
create  bitmap  index   索引名  on 表名( 变量名 desc );

desc 表示降序排序。  bitmap 为 位图索引 正常可不加
``````

#### 组合索引

               ``````sql
               create index 索引名 on 表名(列名1,列名2);              
               
               ``````

### 查看索引



```sql
select * from user_indexes/user_ind_columns ;
```



### 删除索引



```sql
drop index 索引名;
```

## 同义词

### 创建同义词

```sql
create synonym 同义词 for 目标
```

### 查看同义词

```sql
select * from user_synonyms;
select * from all_synonyms;
```

### 删除同义词

```sql
drop synonym 同义词;
```

## 序列

### 创建序列

```sql
create sequence 序列名称

start with 开始数字

increment by 增长数字

minvalue 最小值

maxvalue 最大值

cycle

nocache
```

**详细说明：**

start with 开始数字à从几开始

increment by 增长à步长，每次增长几个数

minvalue 最小值

maxvalue 最大值à可以不设置，不设置应写为nomaxvalue，也就是无穷大

cycle 循环，也就是说当长增长到最大值后，再从最小值开始重新增长

nocache 不设缓存

### 查看序列

```sql
select *  from user_SEQUENCES、all_SEQUENCES;
```



### 引用序列

   xx.nextval      /  xx.curval 

```sql
insert into xx表 values (  )  ,

insert into dept values( DX1_06.nextval,'ss','CN','s',NULL,NULL );

```



### 修改序列

```sql
 alter sequence student_id -- 序列名 也可以更改
 minvalue 1   
 maxvalue 99999  
 start with 1   
 increment by 1  
 cycle    -- 到99999后，从头开始
 nocache；  

```

## 用户

### 修改密码

```sql
alter user 用户名 identified by 密码;
```

### 创建用户

```sql
create  (c##)user username identified by password;    // 创建普通用户 需要添加 c##
```





### 锁定用户

```sql
ALTER USER username ACCOUNT LOCK; 锁定

ALTER USER username ACCOUNT UNLOCK; 解锁
```



### 删除用户

```sql
drop user username ;
```



## 新技能学习 如排序等

### 排序



```sql
(DENSE_)RANK( ) OVER ([ query_partition_clause ] order_by_clause)
rank():跳跃式，两个第1，下一个就是第3
dense_rank():非跳跃式,两个第1,下一个是第2
```



```
分为：（1）连续或不连续：dense_rank,rank

     （2）分区或不分区：使用partition，不使用partition
```



# PL/SQL

## .和/ 的差别

**在SQL*Plus中键入如下PL/SQL块，以点号（.）结束。如果想运行缓冲区的内容，那么可以使用“RUN”命令或者“ / ”命令。**
1
```plsql

在SQL*Plus中键入如下PL/SQL块，以点号（.）结束。如果想运行缓冲区的内容，那么可以使用“RUN”命令或者“ / ”命令。


set serveroutput on 命令是打开COMMAND命令窗口中的输出流。

不搞的话没输出 非常恐怖！！！！！！！！！！！！！！！！！！！

```



| 分隔符                 | 描述                       |
| ---------------------- | -------------------------- |
| `+`,`-`, `*`, `/`      | 加法，减法/负，乘法，除法  |
| `%`                    | 属性绑定                   |
| `'`                    | 字符串分隔符               |
| `.`                    | 组件选择符                 |
| `(,)`                  | 表达式或列表分隔符         |
| `:`                    | 主机变量指示符             |
| `,`                    | 项目分隔符                 |
| `"`                    | 引用标识符分隔符           |
| `=`                    | 关系运算符                 |
| `@`                    | 远程访问指示符             |
| `;`                    | 声明或语句终止符           |
| `:=`                   | 赋值运算符                 |
| `=>`                   | 关联运算符                 |
| ΙΙ                     | 连接运算符                 |
| `**`                   | 指数运算符                 |
| `<<`, `>>`             | 标签分隔符(开始和结束)     |
| `/*`, `*/`             | 多行注释分隔符(开始和结束) |
| `--`                   | 单行注释指示符             |
| `..`                   | 范围运算符                 |
| `<`, `>`, `<=`, `>=`   | 关系运算符                 |
| `<>`, `'=`, `~=`, `^=` | 不同版本的”不等于”运算符   |

## 程序

3、put：将内容写到内存，**等到put_line时一起输出**
4、put_line：不用多说了，输出字符





### 输出 语句

```plsql
dbms_output.put_line(  );   //  line 为换行

dbms_output.put()  正常输出
```



### 创建过程



```sql
CREATE [OR REPLACE] PROCEDURE procedure_name 
[(parameter_name [IN | OUT | IN OUT] type [, ...])] 
{IS | AS} 
BEGIN 
  < procedure_body > 
END procedure_name;
SQL
```



### 执行过程

- 使用EXECUTE关键字

```sql
EXECUTE 过程名;
```



- 从PL/SQL块调用过程的名称



```sql
begin 
 过程名;
end;
```

## 函数


### 创建函数

```sql
CREATE [OR REPLACE] FUNCTION function_name 
[(parameter_name [IN | OUT | IN OUT] type [, ...])] 
RETURN return_datatype 
{IS | AS} 
BEGIN 
   < function_body > 
END [function_name];
SQL
```

**其中，**

- **function-name是指定要创建的函数的名称。**
- **[OR REPLACE]选项指示是否允许修改现有的函数。**
- **可选参数列表包含参数的名称，模式和类型。 IN表示将从外部传递的值，OUT表示将用于返回过程外的值的参数。**
- **函数必须包含一个返回(RETURN)语句。**
- **RETURN子句指定要从函数返回的数据类型。**
- **function-body包含可执行部分。**
- **使用AS关键字代替IS关键字，用来创建独立的函数。**



### 查询函数







## 游标

# 1 概述

```sql
1. 游标是什么？
   用来存储多条查询数据的一种数据结构（'结果集'），
   它有一个 '指针'，从上往下移动（'fetch'），从而能够 '遍历每条记录'
   
2. 优缺点
   (1) 提高 sql '执行效率'
   (2) 牺牲 '内存'
```







### 隐式游标









### 显示游标

使用显式游标包括以下步骤 -

- 声明游标初始化内存
- 打开游标分配内存
- 从游标获取数据
- 关闭游标以释放分配的内存



声明游标

声明游标使用名称和相关的SELECT语句来定义游标。 例如 -

```sql
CURSOR c_customers IS 
   SELECT id, name, address FROM customers;
SQL
```

打开游标

打开游标将为游标分配内存，并使其准备好将SQL语句返回的行记录数据提取到其中。例如，打开上面定义的游标，如下所示：

```sql
OPEN c_customers;
SQL
```

获取游标获取游标一次仅访问一行。 例如，从上面打开的游标中获取行，如下所示代码：

```sql
FETCH c_customers INTO c_id, c_name, c_addr;
SQL
```

关闭游标

关闭游标意味着释放分配的内存。例如，关闭上面打开的游标，如下所示：

```sql
CLOSE c_customers;
SQL
```





## 异常处理



| 异常                 | Oracle错误代码 | SQLCODE  | 描述                                                         |
| -------------------- | -------------- | -------- | ------------------------------------------------------------ |
| `ACCESS_INTO_NULL`   | 06530          | `-6530`  | 当一个空对象被自动分配一个值时会引发它。                     |
| `CASE_NOT_FOUND`     | 06592          | `-6592`  | 当没有选择`CASE`语句的`WHEN`子句中的任何选项时，会引发这个错误，并且没有`ELSE`子句。 |
| `COLLECTION_IS_NULL` | 06531          | `-6531`  | 当程序尝试将`EXISTS`以外的集合方法应用于未初始化的嵌套表或`varray`时，或程序尝试将值分配给未初始化的嵌套表或`varray`的元素时，会引发此问题。 |
| `DUP_VAL_ON_INDEX`   | 00001          | `-1`     | 当尝试将重复值存储在具有唯一索引的列中时引发此错误。         |
| `INVALID_CURSOR`     | 01001          | `-1001`  | 当尝试进行不允许的游标操作(例如关闭未打开的游标)时会引发此错误。 |
| `INVALID_NUMBER`     | 01722          | `-1722`  | 当字符串转换为数字时失败，因为字符串不代表有效的数字。       |
| `LOGIN_DENIED`       | 01017          | `-1017`  | 当程序尝试使用无效的用户名或密码登录到数据库时引发。         |
| `NO_DATA_FOUND`      | 01403          | `+100`   | 当`SELECT INTO`语句不返回任何行时会引发它。                  |
| `NOT_LOGGED_ON`      | 01012          | `-1012`  | 当数据库调用没有连接到数据库时引发。                         |
| `PROGRAM_ERROR`      | 06501          | `-6501`  | 当PL/SQL遇到内部问题时会引发。                               |
| `ROWTYPE_MISMATCH`   | 06504          | `-6504`  | 当游标在具有不兼容数据类型的变量中获取值时引发。             |
| `SELF_IS_NULL`       | 30625          | `-30625` | 当调用成员方法时引发，但对象类型的实例未初始化。             |
| `STORAGE_ERROR`      | 06500          | `-6500`  | 当PL/SQL用尽内存或内存已损坏时引发。                         |
| `TOO_MANY_ROWS`      | 01422          | `-1422`  | 当`SELECT INTO`语句返回多行时引发。                          |
| `VALUE_ERROR`        | 06502          | `-6502`  | 当发生算术，转换，截断或者`sizeconstraint`错误时引发。       |
| `ZERO_DIVIDE`        | 01476          | `1476`   | 当尝试将数字除以零时引发。                                   |









## 异常处理的语法

异常处理的一般语法如下。在这里，可以列举尽可能多的异常并且指定处理方式。默认的异常将使用WHEN...THEN处理，如下语法所示 -

```sql
DECLARE 
   <declarations section> 
BEGIN 
   <executable command(s)> 
EXCEPTION 
   <exception handling goes here > 
   WHEN exception1 THEN  
      exception1-handling-statements  
   WHEN exception2  THEN  
      exception2-handling-statements  
   WHEN exception3 THEN  
      exception3-handling-statements 
   ........ 
   WHEN others THEN 
      exception3-handling-statements 
END;
```

**示例**

```sql
SET SERVEROUTPUT ON SIZE 99999;
DECLARE 
   c_id customers.id%type := 100; 
   c_name  customerS.name%type; 
   c_addr customers.address%type; 
BEGIN 
   SELECT  name, address INTO  c_name, c_addr 
   FROM customers 
   WHERE id = c_id;  
   DBMS_OUTPUT.PUT_LINE ('姓名: '||  c_name); 
   DBMS_OUTPUT.PUT_LINE ('地址: ' || c_addr); 

EXCEPTION 
   WHEN no_data_found THEN 
      dbms_output.put_line('没有找到符合条件的客户信息!'); 
   WHEN others THEN 
      dbms_output.put_line('Error!'); 
END; 
/
```







## 填充默认值。

NVL( xx  ,  0 )  默认为0      zero

 

**语法**

**NVL(eExpression1, eExpression2)**

**参数**
**eExpression1, eExpression2**

**如果 eExpression1 的计算结果为 null 值，则 NVL( ) 返回 eExpression2。如果 eExpression1 的计算结果不是 null 值，则返回 eExpression1。eExpression1 和 eExpression2 可以是任意一种数据类型。如果 eExpression1 与 eExpression2 的结果皆为 null 值，则 NVL( ) 返回 .NULL.。**



## 删除 delete

```sql
delete from xx  where 
```

## 插入 insert

```sql
insert into 表名 values(值1，值2，......);

insert into 表名(列1，列2，......)values(值1，值2，......);

insert into 表名2(列1，列2，......)select 值1，值2，...... from 表名1;  （表2必须存在，列1，列2，......必须存在）

insert into 表2 select * from 表1;

select 值1，值2，...... into 表名2 from 表名1; （表2不存在，插入时会自动创建表名2）
```



# 触发器

## old / new


1.当使用insert语句的时候，如果原表中没有数据的话，那么对于插入数据后表来说新插入的那条数据就是new，如图所示：

![img](https://images2015.cnblogs.com/blog/495456/201608/495456-20160804111235809-1841558199.png)

2.当使用delete语句的时候，删除的那一条数据相对于删除数据后表的数据来说就是od，如图所示：

![img](https://images2015.cnblogs.com/blog/495456/201608/495456-20160804111249215-346800140.png)

3.当使用update语句的时候，当修改原表数据的时候相对于修改数据后表的数据来说原表中修改的那条数据就是old，而修改数据后表被修改的那条数据就是new，如图所示：

![img](https://images2015.cnblogs.com/blog/495456/201608/495456-20160804111301528-856490776.png)





## RAISE_APPLICATION_ERROR

可能不是很多人知道 RAISE_APPLICATION_ERROR 的用途是什么，虽然从字面上已经猜到这个函数是干什么用的。平时用来测试的异常处理
我们都是通过dbms_output.put_line来输出异常信息，但是在实际的应用中，需要把异常信息返回给调用的客户端。
其实 RAISE_APPLICATION_ERROR 是将应用程序专有的错误从服务器端转达到客户端应用程序(其他机器上的SQLPLUS或者其他前台开发语言)
