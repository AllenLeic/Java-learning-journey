# Oracle数据的导入导出
Oracle 有两种导出方式，一种是利用 Oracle 所在的计算机命令行方式导出，效率高，一种是利用远程工具导出效率较低
## Oracle命令行方式
- 导出用户的所有数据
```
exp scott/123456 [file=c:\soctt.dmp] 
```
执行上面语句的效果是把 scott 用户的所有数据导出到指定地方，**文件名必须以 `.dmp` 结尾。**  

- 导出用户的某一张表的数据  
```
exp scott/123456 [file=c:\soctt_emp.dmp] tables=emp   -- 多张表用逗号隔开
```
执行这条语句的效果是把 scott 用户的 emp 表导出到指定文件 soctt_emp.dmp ，**文件名必须以 `.dmp` 结尾。**
（PS: file 可以不指定，那么就会在当前执行 cmd 命令的路径下生成一个导出文件。

- 把所有数据导入到指定的用户
```
imp hr/123456 file=c:\scott_emp.dmp fromuser=scott touser=hr 

-- fromuser代表源数据的所属用户，touser 代表把数据导入到当前的用户
```
如果导入的表有外键，那么外键会丢失，但是不影响导入数据的完整性。  
单独导入某张表的话，在上面的命令上面加上 `tables=emp` 代表只把 emp 表导入hr用户


## 使用 PL/SQL developer 客户端导出。
- 导出一张表的操作  
tools --> export 然后会出现三种导出方式  
  - Oracle Export  这个缺少命令行工具，PL/SQL 客户端使用不了。 这个是 **效率最高的**，掌握上面的命令行就行了。
  - SQL Inserts  当表的数据很少用 SQL inserts ，如果数据量大，可能会导致客户端卡死，效率不高，可读性高。
  - PL/SQL 这种导出只能导出 PL/SQL 识别的后缀名，`.pde` 不利于跨客户端跨平台和不利于阅读。一般用的很少。


- 导入一张表的操作
tools --> export 然后会出现三种导出方式，然后选择对应的文件导入就行了。


### 整库导出命令
在安装了 oracle 的电脑上执行整库导出命令  
```
exp system/orcl full=y   -- 系统用户名/密码  full 参数代表整库导出
```
执行命令后会在当前目录下生成一个叫 EXPDAT.DMP，此文件为备份文件。
如果想指定备份文件的名称，则添加 file 参数即可，命令如下  

```
exp system/orcl file=C:\sys.dmp full=y  
```

### 整库导入命令
在安装了 oracle 的电脑上执行整库导入命令  

`imp system/orcl full=y`   
  
上面的语句执行默认是从当前目录下寻找 EXPDAT.DMP 文件来还原数据库。  

如果想要指定还原文件的名称，则添加 file 参数即可，命令如下  
  
`imp system/orcl full=y file=c:\sys.dmp` 

### 小结
**Oracle 的数据库的导入导出只要掌握了以上的几种方式完全够用了。**
