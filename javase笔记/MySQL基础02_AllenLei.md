[TOC]
## MySQL基础第二天 day22
- 主要内容是MySQL的约束 和多表入门
知识点补充:
1. 用set names gbk; 来解决dos命令窗口不能插入中文编码的问题,不过不是永久性的;
2. 比较运算符: between... and ...  <==>  >= ... <=
3. 逻辑运算符: not 相当于Java的!
4. 包含  in(1,3) 意思为 1或者3 相当于Java的正则表达式的 [1,3] 只能2选1;
5. 使用  \`关键字\`   来转义关键字, 让关键字可以当普通的字符串来用

###### 常见问题回答
1. 如何解决在DOS中无法插入或查询中文字符时乱码的问题   
    方案1:修改my.ini 配置文件,将utf8修改gbk即可，不建议使用。
    方案2:执行一条SQL语句：set names gbk;
2. 如何解决指定IP地址连接数据库无法连接问题？  
    + 打开cmd窗口，进入MySQL安装的bin目录
    + 执行命令登录数据库,之后会出现一行要你输入密码的 mysql -u root -p
    + 执行以下命令分配新用户：
  grant all privileges on *.* to 'root'@'%' identified by 'root'; 
  (%) 表示所有ip
  - 执行完上述命令后用下面的命令刷新权限
      flush privileges;
  - 之后关闭mysql服务，然后启动mysql服务，大功告成
</p>
<h4>学习目标:</h4>
    1. 排序
    2. 聚合函数
    3. 分页查询
    4. 分组查询
    5. 数据库备份和还原
    6. 约束
    7. 级联操作
    8. 标语表的关系
    9. 常见面试题
<hr>
###### 1.排序 从小到大,或从大到小 默认从小到大 asc
- 查询表信息
`select * from user;`
- 查询所有人的信息,按从小到大排序查看
`select * from user order by math;`
- 默认就是从小到大,如果要从大到小的话
`select  * from user order by math desc;`
- 按总分相加来排序的话
`select * ,(math+english) as 总分 from user order by 总分;`
###### 2.聚合函数演示
关键字,count max sum min avg 
如:
>select sum(english) english_sum,max(english) as maxEnglish, count(*) as peoples, avg(english) English_avg from user;
 查询了总分 最值,人数,平均分.
###### 3. 分页查询
- 分页查询数据,每页显示两条数据共三页:
select * from user limit 0,2; 
第一个数据代表从 第0 个索引数据开始,查2个数据
- 分页查询时排序
select * from student order by math asc limit 0,4;
分组查询可以用到having对分组的数据进行筛选
where 和 having 的区别 :
1. 数据查询方式不同where 对 行数据经行筛选, 而having 是对列经行 筛选
2. 出现的位置不同 where 在group by 前面, having 在后面
3. where 后面不可接聚合函数, having 可以;
### 数据库的备份
1. 命令行
    + mysqldump -u用户名 -p密码 数据库>路径
    + mysql -u用户名 -p密码 数据库<路径
2. SQLyog的导入和导出
####  约束
- 作用
 保证数据的正确性、有效性和完整性。
 数据类型也可以看成数据约束的一种，起到限制数据类型的一种，但不够严格。
     比如int age,限制age是整数，但不能限制是负数。
- 分类
    + 默认约束
 关键字：default 默认值
 当这个字段没有输入任何的值，则数据库使用默认的值
    + 非空约束
 约束某一列的值不能为null,必须有值。
    + 主键约束
用来标识记录的唯一性。
- 设计原则
1. 主键应当对用户没有意义的，因为主键是给程序猿看的，不是给用户使用的。
2. 主键应当由计算机/数据库自动生成。
3. 主键应当是单列的
- 自增长字段
    + 关键字`auto_increment`
让某一整数列的值每次在当前的基础加1，从1开始。
- 零填充
    + 关键字 `ZEROFILL`
整数列的数值不满指定的位数时用零填充。
- 唯一约束
    + 关键字 `unique`
约束某一列的数据在一张表中不能出现相同的值。
- 外键约束
- 检查约束
在用户输入完数据之后就立即检查数据的合法性，如果不合法就立即报错。
MySQL不支持约束
- 主键约束
创建表的时候指定主键约束,在主键列后面 加上 `primary key` 
````sql
    create table 表名(
    列名 数据类型 约束 primary key,
    列名 数据类型 约束,
    列名 数据类型 约束
        )
```
指定主键列自动增长
    格式:
```sql
create table 表名(
列名 数据类型  primary key  auto_increment,
列名 数据类型 约束,
列名 数据类型 约束
)
```
注意: 自动增长只能用在整形的主键列上
特点: 当我们添加数据时候,不指定主键列,主键列数据都会在原来的基础长递增1





