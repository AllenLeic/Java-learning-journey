# Windows下Mysql错误ERROR 1045 (28000) ERROR 1054 (42S22)以及ERROR 1820 (HY000)的解决
1. 去根目录配置你的mysql配置文件my.ini 
2. 记事本打开my.ini，在[mysqld]这个条目下加入
>skip-grant-tables
3. 保存退出后重启mysql 
    - 重启方法1：
        1. 点击“开始”->“运行”(快捷键Win+R)。 
        2. 启动：输入 net stop mysql 
        3. 停止：输入 net start mysql 
    - 重启方法2：（如果1不行的话）
        + 到 计算机管理–>服务和应用程序–>服务–>MYSQL–>右键–>启动.
4. 在cmd里面输入mysql -u root -p就可以不用密码登录了，出现password：的时候直接回车可以进入
5. 重点步骤(斜体为操作后命令提示的结果，不输入)

1.进入mysql数据库

>mysql> use mysql;
>*Database changed*

2.给root用户设置新密码，新密码自己输：

>mysql> update user set password=password(“新密码”) where user=”root”;
## 警告：这个命令是5.7之前一些老版本的，如果你用的新的，这样输入会出现错误：

>ERROR 1054 (42S22): Unknown column ‘password’ in ‘fie

这是因为5.7版本下的mysql数据库下已经没有password这个字段了，password字段改成了

>authentication_string

所以，应该输入如下命令：

>update mysql.user set authentication_string=password(‘root’) where user=’root’ ; 
>*Query OK, 1 rows affected (0.01 sec) Rows matched: 1 Changed: 1 Warnings: 0*

- 3刷新数据库
>mysql>flush privileges;

>*Query OK, 0 rows affected (0.00 sec)*

- 4退出MySQL：怎么退都行
- 5改好后把my.ini把刚才加入my.ini文件的的”skip-grant-tables”这行删除保存退出再重启mysql就可以了。
- 如果还要输入密码的话

>mysql> SET PASSWORD = PASSWORD(‘123456’);

括号中密码随意