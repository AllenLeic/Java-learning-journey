[TOC]
# 事务的学习
## 事务是什么？
概念：在一个业务的操作中，要么所有的SQL语句全部执行成功，要么回滚全部失败  如何理解，用一个转账案例来理解
### 案例:转账
- 需求：Jack向Rose转200元钱
```sql
# 创建表
create table account(
    id int primary key auto_increment,
    name varchar(20),
    balance int  -- 金额
    );
-- 插入两条记录
insert into account(name,balance) values('jack',500),('rose',500);
-- 更新两条语句： 一个转账的业务操作最少要执行下面两条语句
update account set balance = balance - 200 where name='jack';
update account set balance = balance + 200 where name='rose';
select * from account;
```
这样做会存在的问题是，如果执行了第一条语句的时候遇到了错误，那么，jack账户中的钱少了，但是rose 账户上面的钱没有多，这样就和实际需求不符合，这时候就需要事务处理了
## 事务有什么用？
- 通过上面的案例我们知道了转账过程中会存在的问题，那么事务可以解决这一问题
- 把这个转账看作是一个业务，只要没有执行到最后面就可以把之前的操作都自动回滚，这样Jack账户上面的钱不会少，除非转账业务完成了。
## 事务怎么用？
不同的数据库对数据的处理方式有所不一样但是大体是一样的
### MySQL事务操作
#### 1.MySQL事务处理方式
1. 默认是自动提交方式。即默认每一条SQL语句执行完后都会自动提交事务，不可以回滚。
通过设置自动提交参数可以变更事务处理默认值，不过一般不使用这种方式
```sql
set autocommit = 0; -- 禁止自动提交模式
set autocommit = 1; -- 开启自动提交模式， 默认值
```
2. 手动提交方式
```sql
start transaction; --开启事务
-- 一旦手动开启事务，接下来的一系列操作都是在同一个事务中，只要没有提交
-- 就可以对事物进行 rollback (回滚)
```
#### MySQL事务控制语句
1. rollback; 回滚事务，撤销当前执行成功的SQL语句。
2. start transaction; 开启事务。
3. commit; 提交事务
#### MySQL事务结束条件
1. commit; 执行提交事务语句。
2. rollback; 执行回滚事务语句。
3. 执行了一条DDL语句：比如创建了一张表，之前的事务会自动提交。
4. 又开启了一条新的事务，之前的事务会自动提交。
#### MySQL事务使用演示
```sql
set autocommit = 0; -- 相当于关闭了自动提交
    -- 只要没有执行DDL语句、commit提交或者又开启了一条新的事务
    -- 就可以用rollback进行回滚
set autocommit = 1; -- 相当于自动提交，每条SQL语句都自动提交事务，
    -- 无法用rollback进行回滚
start transaction; -- 主动开启一条事务
    -- 没有出发其他关闭条件，就可以使用rollback进行回滚
```
### JDBC事务操作
#### 案例操作
- 从Jack的账户转200元到rose账户上面。
1. 默认处理方式
```java
    public static void test01() {
        Connection conn = null;
        PreparedStatement ps = null;
        try {
            // 获取连接对象
            conn = JDBCUtil.getConnection();
            // 准备SQL语句
            String sql = "update account set balance = balance - 200 where name = ?";
            ps = conn.prepareStatement(sql);
            // 给占位符赋值
            ps.setString(1, "jack");
            // 开始执行转账操作
            ps.excuteUpdate();
            JDBCUtil.close(null,ps);
            // rose 加钱
            ps = conn.prepareStatement(sql);
            ps.setString(1, "rose");
            ps.excuteUpdate();
            System.out.println("转账成功")
            
        } catch(Exception e) {
            System.out.println("转账失败")
        } finally {
            JDBCUtil.close(conn, ps);
        }
    }
```
2. 手动提交事务方式
```java
/*
    手动事务处理方式
    void setAutoCommit(boolean autoCommit)
    设置是否自动提交事务。false：手动提交，开启事务，等价于在控制台输入
    start transaction;
    true : 自动提交事务，默认值。

    void commit()提交事务
    void rollback();回滚事务
*/
    public static void test02() {
        // 获得连接对象
        Connection conn = null;
        PrepareStatement ps = null;
        try {
            conn = JDBCUtil.getConnection();
            // 开启事务
            conn.setAutoCommit(flase);
            String sql = "update account set balance = balance -200 where name = ?";
            ps = conn.prepareStatement(sql);
            // 给占位符赋值
            ps.setString(1, "rose");
            ps.executeUpdate();
            
            // 提交事务
            conn.commit();
            System.out.println("转账成功");
        } catch (Exception e) {
            System.out.println("转账失败");
            try {
                // 回滚事务
                conn.rollback();
            } catch (SQLException e1) {
                e1.printStackTrace();
            }
        } finally {
            JDBCUtil.close(conn, ps);
        } 
    }
```
#### Connection 接口中与事务相关方法
```
void setAutoCommit(boolean autoCommit) : 设置是否自动提交事务
 false: 手动提交，开启事务，等价于在控制台执行： start transaction;
 true: 自动提交事务，默认值。

void commit();提交事务
void rollback();rollback transaction
```
###  DbUtils事务操作
    - 案例需求 ： 从Jack的账户转200元到rose的账户上。
1. 默认处理方式 
## 事务的注意事项