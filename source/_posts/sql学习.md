---
title: sql学习
date: 2024-02-06 19:43:21
tags: [数据库,sql]
categories: 学习笔记
---

# Sql语句学习
## 一.Sql数据分类
### 1.DQL(数据查询语言)
 DATA QUERY LANGUAGE
 查询语句 凡是select语句都为DQL

### 2.DML(数据操作语言)
 DATA MANIPULATION LANGUAGE
 insert delete update 对表当中数据进行增删改
### 3.DDL(数据定义语言)
DATA DEFINITION LANGUAGE
create drop alter 对表结构的增删改
### 4.TCL(事务控制语言)
 commit提交事务，rollback回滚事务
### 5.DCL（数据控制语言）
 DATA CONTROL LANGUAGE
 grant授权，revoke撤销权限
## 二.mysql独特命令

###  1.查看有哪些数据库

**show  databases；**

### 2.创建属于自己的数据库

**create database studybase**;

### 3.使用自己的数据库

**use studybase;**

### 4.查看当前数据库有哪些表

**show tables**;

### 5.导入sql脚本

**source D:/study/study.sql**

### 6.删除数据库

**drop database studybase**

### 7.查询表数据结构

**desc studybase**

### 8.查看当前使用的是哪个数据库

**select database();**

### 9.终止一条语句命令

**\c**

### 10.导出数据库

**mysqldump xxxdatabase;**

## 三.查询语句详解

### 1.sql规则

**任何一条sql语句以分号“;"结尾**

**sql语句不区分大小写**

**标准sql语句要求字符串使用单引号括起来**

**起别名的as可以用空格代替**

>举个例子
>
>select t_no t_money as ‘工资‘ where t_name = 'zhangsan'
>
>select t_no t_money  ‘工资‘ where t_name = 'zhangsan'
>
>这两个语句查询效果一样

### 2.select关键字

#### 1.null

>所有数据库只要运算有null参与结果均为null

```sql
#ifnull关键字用法(可能为null的数据，当做什么处理)
select ename,(sal+ifnull(comm,0))*12 from emp
```



null为空，查询u_name不为null值的所有用户

>select * from user where u_name is not null

#### 2.between ... and ...

两端都为闭区间 等价于<= ... and >=...

>select * from user where money >=1000 and money<=3000
>
>select * from user where money between 1000 and 3000

#### 3.and 以及 or

and表示并且

or表示或者

and优先级高

#### 4.in

in等同于or

```sql
#查找sal工资等于1000或者5000的员工
select ename,job from emp where sal in(1000,5000)
```

#### 5.like

>%表示任意多个字符
>
>_表示一个字符

#### 6.order by

>排序 
>
>asc为升序 desc为降序 默认为asc

```sql
select ename,sal from emp order by sal
select ename,sal from emp order by sal asc
select ename,sal from emp order by sal desc
#按照工资降序排列，工资相同时，按照名字升序排列
select ename,sal from emp order by sal desc , ename asc 
```

#### 7.分组函数

>count 计数 sum求和 avg平均值 max最大值 min最小值
>
>也叫多行处理函数 输入多行 最终输出结果为一行
>
>分组函数自动忽略null !!!

``` sql
#找出工资总和
select sum(sal) from emp;
#找出最高工资
select max(sal) from emp;
#找出最低工资
select min(sal) from emp;
#找出平均工资
select ave(sal) from emp;
#找出总人数
#count(*)统计总记录条数
#count(具体字段)统计具体字段不为null的总条数
select count(*) from emp;
```

>分组函数不能直接出现在where子句后面
>
>因为group by在where后面执行
>
>而分组函数在group by后面执行
>
>分组函数如果没有group by语句 则自成一组
>
>下面是sql关键词顺序
>
> from  where group by having select order by

```sql
#找出工资高于平均工资的员工
#第一步,找出平均工资,结果为2073
select avg(sal) from emp;
#第二步，找出高于平均工资的员工
select ename ,sal from emp where sal >2073；
#通过子查询 合一起
select ename,sal form emp where sal > (select avg(sal) from emp)；
```



#### 8.ifnull

>ifnull()函数 可以将null值转换成其他值

```sql
#ifnull关键字用法(可能为null的数据，当做什么处理)
select ename,(sal+ifnull(comm,0))*12 from emp
```

#### 9.分组查询

>group by 关键字

```sql
#找出每个岗位的最高薪资
select max(sal),job from emp group by job;
```

>当用group by分组后 查询的字段只能为分组的字段

```sql
#可以联合分组
#找出 每个部门 不同岗位 的最高薪资
select
  deptno,job,max(sal)
  from
   emp
   group by
     deptno,
```

#### 10.distinct

>去除重复记录
>
>distinct只能出现在字段最前面，去除联合字段的重复记录

```sql
#是 去重 deptno以及job的联合字段的数据
select distinct deptno job from emp;
```



### 3.连接查询

#### sql关键字顺序

##### from  where group by having select order by limit

>select from where group by having order by limit   

#### 1.笛卡尔积

>当两条表进行连接查询的时候，没有条件进行限制，最终查询的结果是两条记录条数的乘积

##### 如何避免笛卡尔积现象

>加条件进行过滤
>
>注意！！！ 记录的匹配次数不会减少 只会显示有效记录 
>
>没有提高效率

#### 2.给表起别名

>有两个好处
>
>1.可读性好
>
>2.执行效率高，会具体到起别名的表的字段

#### 3.join on关键词

##### 1.等值连接

```sql
#SQL99语法
##后面还可以加where关键字 进行条件筛选
select 
  e.ename,d.dname
from
  emp e
(inner) join
  dept d
on 
   e.deptno= d.deptno;
##等价于这条SQL92语法 已被淘汰
select e.name,d.dname from emp e,dept d where e.deptno = d.deptno
```

  ##### 2.非等值连接

>找出每个员工的工资等级 显示员工名 工资 工资等级

```sql
select 
  e.ename,e.salary,s.grade
from 
  emp e
join
  salgrade s
on
  e.salary between s.losal and s.hisal;
```

#####  3.自连接

>找出每个员工的上级领导，要求显示员工名以及领导名

```sql
select 
   a.ename as '员工名',b.ename as '领导名'
from 
   emp a
join
   emp b
on a.mgr=b.empno   
```

##### 4.外连接

>内连接： 假设A表和B表进行连接，使用内连接的话，凡是A表和B表匹配得上的记录都会查出来，AB两表没有主副之分

>外连接： 假设A表和B表进行连接，使用外连接，AB两张表，有一张为主表，有一张为副标，主要查询主表数据，如果副表数据没有与主表数据匹配上 副表会自动模拟null匹配

>外连接分为左外连接以及右外连接

```sql
select a.ename '员工',b.ename '老板'
from emp a
#join前面为left就为左外连接 为right就为右外连接
left(right) join emp b
on a.mgr = b.empno;
```

>案例 找出哪个部门没有员工

```sql
select 
   d.*
from 
   emp e
right join 
   dept d
on 
   e.deptno = d.deptno
where
   e.empno is null;

```

##### 5.全连接

>暂时没学 以后补充

##### 6.三张表连接

>表示A表和B表先连接 ，连接之后A表和C表在连接
>
>案例 找出员工名字 部门名字 以及工资等级

```sql
select 
   e.ename,d.dname,s.grade
from 
   emp e
join 
   dname d
on 
   e.deptno = d.deptno
join
   salgrade s
on
   e.sal between s.losal and s.hisal;
```

>案例： 找出每一个员工的部门名称 工资等级 以及上级领导

```sql
select 
   e.ename '员工',d.dname,s.grade,e1.ename '领导'
from
   emp e
join
   dept d
on 
   e.deptno = d.deptno
join 
   salgrade s
on 
   e.sal between s.losal and s.hisal
left join
   ename e1
on 
   e.mgr = e1.empno;
```

#### 4.嵌套子查询

##### where后面嵌套子查询

>案例： 找出薪资大于平均薪资的员工记录

```sql
select * from emp where sal > (select avg(sal) from emp );
```

##### from后面嵌套子查询

>案例：找出每个部门平均薪水的薪资等级

```sql
#第一步 找出每个部门平均薪水
select deptno,avg(sal) from emp group by deptno;
#第二步，把上面结果看做临时表，让临时表t和salgrade表结合
#条件为t.avg(sal) between s.losal and s.hisal
select 
   t.*,s.grade
from 
   (select deptno,avg(sal) as avgsal from emp group by deptno) as t
join
   salgrade s
on 
   t.avgsal between s.losal and s.hisal;
```

##### select后面嵌套子查询

>案例： 找出每个员工所在的部门名称 
>
>要求显示员工名和部门名

```sql
select e.ename,d.dname
from emp e
join dept d
on e.deptno = d.deptno
#老师举了一个不常用的例子 以后再补充
```

#### 5.union关键字

>可以将查询集相加
>
>select stuno,stu from class1
>
>union
>
>select stuno,stu from class2

#### 6.limit

>limit是mysql独有的 oracle有个相同机制叫rownumber
>
>语法机制
>
>limit startIndex，length
>
>startIndex表示起始位置 从0开始 0表示第一条数据
>
>length表示取几个
>
>案例： 取出工资前五名的员工

```sql
 #取出所有员工 按工资降序排
 select ename,sal from emp order by sal desc;
 #取出员工工资前五
 select ename,sal from emp order by sal desc limit 0,5;
 #如果直接写一个数字，默认起始索引为0
 select ename,sal from emp order by sal desc limit 5;
```

>分页 假设每一页显示三条记录
>
>第一页 0,3
>
>第二页 3,3
>
>第三页 6,3
>
>得出规律 
>
>每页显示pageSize条记录
>
>第pageNo页的索引为 （pageNo-1）*pageSize

## 4.DDL

### 1.创建表

#### mysql常用数据类型

1. int 整数型

2. bigint 长整型（java中的long）

3. float 浮点型

4. char 定长字符串

5. varchar 可变长字符串（最大255）

6. date 日期类型

7. BLOB 二进制大对象（存储图片，视频等流媒体信息）

8. CLOB 字符大对象（存储较大文本，可存储4G文本）

```sql
  drop table if exists t_student;
  create table t_student(
       no bigint,
       name varchar(255),
       gender char(1) default 1,
       classno varchar(255),
       birth char(10)
   );
```

   #### 复制表

```sql
create table tmp1 as select * from t_student
```

#### 设置自增

>auto_increment 

#### 约束

##### 1.非空约束 

not null

约束的字段不能为null

>not null 没有表级约束 只有列级约束

##### 2.唯一约束

unique

约束的字段不能重复

```sql
#代表各自不能重复 列级约束
create table t(
id int unique,
username varchar(255) unique
)
```

```sql
#代表联合不能重复 表级约束
create table t(
id int,
username varchar(255),
unique(id,username)
)
```



##### 3.主键约束

primary key

约束的字段不能为null也不能重复

>主键的作用：唯一标识

```sql
create table t_user(
 id int,
 username varchar(255),
 primary key(id)
)
```



##### 4.外键约束

foreign key

外键值可以为null

外键引用字段，必须唯一字段，不一定要是主键 

```sql
drop table if exists t_student;
drop table if exists t_class;
create table t_class(
  cno int primary key,
  cname varchar(255)
);
create table t_student(
  sno int primary key ,
  sname varchar(255),
  classno int,
  foreign key(classno) references t_class(cno)
)
```



##### 5.检查约束

check

oracle有check约束 mysql没有

## 5.DML

### 1.插入数据

```sql
insert into t_student (no,name,gender,classno,birth)
values(001,'zhangsan','1','高三一班','2001-11-23')
```

#### 将查询结果插入一张表中

```sql
insert into tmp1  select * from t_student
```

### 2.修改数据

```sql
#update语句如果没有where条件是将整张表更新
#update语句后面是逗号，不是and！！！
update dept1 set loc ='shanghai',dname='zhangsan' where deptno=10
```

### 3.删除数据

```sql
#如果没有where条件表示全部删除
delete from dept1 where deptno =10;
```

```sql
#怎么快速删除大表 不可恢复！！
truncate table emp1;
```

## 6.事务

>一个事务是一个完整的业务逻辑单元，不可再分
>
>与事务相关的语句只有：DML语句
>
>事物的存在是为了保证数据的完整性，安全性

### 事物的特性

>事务包括四大特性： ACID
>
>A： 原子性：事务是最小的工作单元不可再分
>
>C： 一致性：事务必须保证多条DML语句同时成功或者同时失败
>
>I:    隔离性：事务A与事务B之间具有隔离
>
>D:  持久性：持久性说的是最终数据必须持久化到硬盘文化

#### 关于事物的隔离性

第一级别：读未提交

第二级别：读已提交

第三级别：可重复读

第四级别：序列化读，串行化读

## 7.数据库三大范式

### 第一范式

任何一张表都应有主键，且每一个字段原子性不可再分

### 第二范式

所有非主键字段完全依赖主键，不能产生部分依赖

>解决方式 多对多？三张表，关系表两个外键

### 第三范式

在第二范式的基础上，所有非主键字段直接依赖主键，不能产生传递依赖

>一对多?  两张表 多的表加外键

### 在实际的开发中，以客户的需求为主，有时候会以冗余换执行速度

>一对一？ 主键共享 或者 外键唯一

 ## 经典易错题

### 1.找出每个部门的最高薪资，显示薪资大于2900的数据

>常见效率低的解决方式：

```sql
#可以分两步
#第一步，找出每个部门的最高薪资
select max(sal),deptno from emp group by deptno;
#第二步，用having过滤大于2900的数据
select max(sal),deptno from emp group by deptno having max(sal) > 2900;
```

>正确解决方式：

```sql
#第一步，找出每个部门的最高薪资
select max(sal),deptno from emp group by deptno;
#第二步，先用where排除掉2900以下的数据，再分组查询
select max(sal),deptno from emp where sal > 2900 group by deptno;
```

### 2.（举个只能用having不能用where的例子）找出每个部门的平均薪资，要求显示薪资大于2000的数据

```sql
select deptno,avg(sal) from emp group by deptno having avg(sal) > 2000;
```

### 3.统计岗位的数量

```sql
select count (distinct job) from emp;
```

### 4.取得每个部门最高薪水的人员名称

```sql
#第一步查询每个部门最高的薪水
select deptno,max(sal) maxsal from emp group by deptno;
#第二步 将以上当成t表 t表和emp e表进行连接
#条件为 t.deptno =e.deptno t.maxsal =e.sal
select e.ename,t.* from (select deptno,max(sal) maxsal from emp group by deptno) t join emp e on t.deptno = e.deptno and t.maxsal = e.sal;
```

