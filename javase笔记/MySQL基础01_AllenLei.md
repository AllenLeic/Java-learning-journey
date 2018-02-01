[TOC]
#  MySQL 基础 和 SQL语句
**查询的格式：每个关键字换一行比较好，思路比较清晰** 如下所示：

    mysql> select *
        -> from users
        -> where salary<1200
        -> or salary>5000;
###### ifnull 的用法

    mysql> select ifnull(salary,0) 薪水,ifnull(salary,0)*12 年薪
        -> from users;
学习目标:
# 数据库是什么?
	用于存储数据的仓库
	
# 数据库有什么用?
	其本质就是一个文件系统,可以方便的对数据进行增删改查操作

#有什么同类产品? 目前状况如何? 有何特点?
Oracle 	关系型数据库	大型数据库		大企业用 收费	
MySQL 	关系型数据库	中小型数据库	中小型企业够用 Oracle收购后 6.0版本开始收费
Microsoft SQL Server 	关系型数据库 只能在windows 上用 收费
目前使用前三的关系型数据库就是这三个了

- 什么是关系型数据库	存储的数据有关系,比如列表

  关系型数据库把所有的数据都通过行和列的二元表现形式表示出来。

-  关系型数据库 和非关系型数据库的区别
	非关系型数据库的优势：
		1. 性能NOSQL是基于键值对的，可以想象成表中的主键和值的对应关系，
			而且不需要经过SQL层的解析，所以性能非常高。
		2. 可扩展性同样也是因为基于键值对，数据之间没有耦合性，所以非常容易水平扩展。
	
关系型数据库的优势：
	1. 复杂查询可以用SQL语句方便的在一个表以及多个表之间做非常复杂的数据查询。
	2. 事务支持使得对于安全性能很高的数据访问要求得以实现。
	
对于这两类数据库，对方的优势就是自己的弱势，反之亦然。
	
	
#为什么要学习MySQL数据库?
1.免费
2.开源
3.体积小,可靠性高
	
#MySQL数据库要怎么用?
用SQL语句操作 所以要学习SQL语句
可以用SQLYog 可视化界面操作
{
1. 概念: 
- 什么是数据库?
	用于存储数据的仓库,其本质就是一个文件系统,可以方便的对数据进行增删改查操作

- 数据库系统的管理结构:	
	以下是包含关系
	数据库操作系统 -> 多个数据库 -> 多张表单 -> 多条记录

- 数据库和Java中的类的对应关系
	数据库        		Java
	表			<->		类
	字段(列) 	<->		属性
	多条数据	<->		对象

2. MySQL 
-  MySQL 安装 直接傻瓜式安装就行 端口3306
-  MySQL 服务的启动与关闭 
1. Windows的服务找到MySQL服务关闭掉
2. cmd -> services.msc -> 找到MySQL服务右键启动或关闭
这两个本质上是一样的找到Windows的服务菜单
}
3. 使用管理员系统权限启动cmd命令窗口
  1) net  start mysql 开启
  2) net stop  mysql 关闭
		
-  MySQL 数据库的登录
1.本地登录 mysql -u用户名 –p密码	
	如 mysql -uroot -proot
2.远程登录 mysql --host= ip地址 --user= 用户名 --password= 密码
	如 mysql --host=192.168.100.123 --user=root	--password=root

- MySQL中的三种注释	
    	# 注释内容 mysql 特有的注释 单行注释
    	-- 注释内容 所有的数据库通用的注释 单行注释
    	/* 注释内容 */ 多行注释
	
- MySQL中的数据类型
	1. int 整型
	2. double 浮点型
	3. varchar 字符串型
	4. date 日期类型

###  SQL语句 : 每条语句用分号来作为结束符,和Java一样
1.SQL概念:
- SQL的全称：structured query language		结构化查询语言。

2.SQL的作用 :
- 用来操作数据库,数据表,以及数据表中的数据,执行增删改查操作.
	- 增删改查 crud;

3.SQL语句的分类
- DDL	(data definition language)  -->相当于定义一个类或者一个对象
	数据定义语言,定义数据库,数据表,表结构等	
	关键字 : create / drop / alter
	
- DML  (data manipulation language)--> 相当与给对象赋值和清除数据
	数据操作语言,用来操作数据库数据的	
	关键字: insert / update / delete
	
- DQL  (data query language)  -->相当于遍历,可以有条件的遍历
	数据查询语言,用来查询数据的;
	关键字: select / show

- DCL (了解) (data control language) 
	数据控制语言, 用来创建用户,删除用户,给用户分配权限等操作
	关键字: grant / revoke / create 
--------------------------------------------------------------------------		
4.具体的学习SQL语句
	注: 每条语句用分号来作为结束符
--> DDL (data definition language):(student用来代替数据名) 
	-- 对库操作
1. show databases; 查看所有数据库
2. create database student; 使用默认编码创建数据库
3. create database student default character set gbk; 使用指定编码创建数据库
4. show create database student; 查看数据库创建语句
5. drop database student;删除student数据库
6. alter database student default character set gkb;
	
- 对表操作 
1. use student;		选择要操作的数据库 
2. show tables;		查看数据库的所有表
3. create table student (	创建列 空列要加() 如create table student();
  	id int,
  	name varchar(20),
  	age int
4. show create table student; -- 查看数据表创建语句
5. desc table; -- 以表结构形式查看表结构。}
	
6. create table employee like student ; 创建新的数据库表和旧表结构一样
7. drop table student;删除表
8. alter table student add sex char(2); 加个性别列
9. alter table student add math int , add english int ;同时加两列
10. alter table student modify sex varchar(2); 重新定义列的数据类型
11. alter table student change sex gender varchar(2);修改列的名字和数据类型
12. alter table student drop math , drop english;删除列;可删多个
13. alter table student rename employee ;重命名表标题 
14. alter table student default character set utf8; 从新定义表的编码类型
-----------------主要是对数据的结构和类型进行操作---------------

- > DML (data manipulation language) 数据操作
-  查看数据
	1. select * from student; 选择student上面的所有查看 如果没数据就不显示
	2.
  -  对数据操作,主要是插入,删除,查看数据;
  1. insert into student values (1,'诡术妖姬',33,'女',100); 插入完整数据
  2. insert into student(name,age) values(盲僧,44);插入指定列的数据
- 修改和删除数据
1. update student set name= 'jack'; 把name列所有的数据都改为jack
2. update student set name= 'jack' ,age = 10 where id=1;
- 修改id 为1 数据name = jack age =10
1. delete from student; delete student 中的所有数据
2. delete from student where id= 1; 把id=1的这一行数据删除;
3. truncate student;删除所有记录 
---

- 问:drop delete 和truncate 删除所有记录 有什么不同?
1. delete 一行一行的删除数据;还把数据放回收站;
  truncate (是截断的意思)先把表全部截断,
  再创建一个和之前的数据结构一样的表,不能回滚
  drop 是直接把数据结构也给删除掉,
  所占用的空间全部释放掉不能回滚
2. 速度上面一般而言 drop>truncate>delete
3. 应用范围:truncate 只能对table; delete可以对table和value;
4. drop 不保留数据结构,而delete和truncate保留数据结构
-----------------主要是对数据的内容进行操作---------------

--> DQL (data query language) 查询数据的语句; query 查询
普	 distinct : 不重复的
查	1.查询所有列: select * for student; * 代表所有的列
2.查询指定列: select name,age from student;
3.查询时指定别名 select name as 姓名,age as 年龄 from student;
4.合并列查询: select * ,(math+english) as 总分 from student;
  这里的as 可以省略 把英语和数学成绩加起来 显示别名总分
	--  查询时添加常量列
--  在查询学生表时都带上一个班级列，内容为"JavaEE就业班"
select *,'JavaEE就业班' from student; 字符串常量要用单引号括起来
5.去除重复数据,比如去除姓名重复的学生. 
    	select distinct name from student;

条件查询语句 关键字where 主要关键字有 and or not like;
6.逻辑条件
--查询id值为3,且性别为男的学生,(同时满足两个条件)
select * from student where id=3 && gender = '男';
select * from student where id=3 and gender = '男';
		&& 	等价于	and
同理 	|| 	<==>	or

-- 判断是否为空串：=''、<>''
-- 判断是否为空：IS NULL,IS NOT NULL

alter table student add address varchar(20);
--  查询 address 为空串的学生
select * from student where address = '';

--  查询 addres 不为空的学生
select * from student where address <> '';

--  查询 address 为NULL的学生
select * from student where address is null;
--  查询 address 不为NULL的学生
		select * from student where address is not null;

--  查询 address 为空或NULL的学生
select * from student where address is null || address = '';
--  查询 address 段不为空且不为NULL的学生
select * from student where address is not null && address <> '';

-- 模糊查询：LIKE
-- %：表示匹配多个任意字符(0到多个)
-- _：表示匹配一个任意字符
		
--  查询姓张的学生
select * from student where name like '张%';
--  查询姓名中包含'张'的学生
select * from student where name like '%张%';

--  查询姓张，且名字只有两个字的学生
select * from student where name like '张_';

-- in 关键字
-- 查询id是1或3的学生
select * from student where id = 1 || id = 3;
select * from student where id in(1,3);


 show character set;
 show collation like 'utf8%'

 12、校对规则概述(了解)
1.  概念
它是一组规则，该规则决定了某一字符集下的字符如何进行排序和比较。
如：a,B,c,D，如果使用utf-8的编码，按照普通的字母顺序，而且不区分大小写。如果想使用字母的二进制比较和排序，则可以修改它的校对规则。
    
        utf8_general_ci 按照普通的字母顺序，而且不区分大小写
        （比如：a B c D）
        utf8_bin    按照二进制排序（比如：A排在a前面，B D a c） 

2.  查看字符集和校对规则
    -- show character set; -- 显示所有字符集及其默认的校对规则
    -- show collation like 'utf8%'  -- 显示所有utf8的校对规则

3.  创建数据库同时指定字符集和校对规则
    create database 数据库名 default character set gbk collate gbk_chinese_ci;

4.  修改数据库的校对规则 
    alter database 数据库名 collate utf8_general_ci;
					 

##### homework
4. SQL语句分类DDL,DML,DQL,DCL表示的含义
  + DDL(data definition language) 数据定义语句
  + DML(data manipulation Language) 数据操作语句
  + DQL(data query language) 数据查询语句
  + DCL(data control language) 数据控制语句

5. 创建数据库并设置 utf8 编码,完成数据库的添加,删除,查询,使用.
>create database;
6. 使用数据库 webdb_1,在该数据库下创建表: category.
> create database webdb_1; create table category;