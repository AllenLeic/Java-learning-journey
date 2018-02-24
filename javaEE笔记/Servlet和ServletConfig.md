# Servlet和ServletConfig 

## Servlet的开发

### 什么是Servlet
A servlet is a small Java program that runs within a Web server. Servlets receive and respond to requests from Web clients, usually across HTTP, the HyperText Transfer Protocol.
- 概念：运行在Web服务器中的一个Java小应用程序
- 作用：Servlet用于接收客户端发送过来的请求，并做出响应通过http协议。

### Servlet生命周期
- Servlet创建的时机：
**实例化（构造方法）、初始化（init方法）、服务（service）、销毁（destroy）**
![Servlet生命周期](/img/Servlet生命周期.png )

### Servlet的运行过程
![Servlet的运行过程](/img/Servlet的运行过程.png "Servlet的运行过程")

### Servlet的生命周期方法
- 定义在javax.servlet.Servlet接口中
|方法|作用|运行次数|
|:---:|:---:|:---:|
|构造方法|实例化对象的运行，**单例**|1次|
|void init(ServletConfig config)|实例化对象后，执行初始化|1次|
|void service(ServletRequest req,ServletResponse res)|每次请求和响应都会执行<br/>**参数：请求和响应**|多次|
|void destroy()|Servlet销毁，服务器关闭或重启的时候执行|1次|

- 演示：直接实现Servlet接口，并重写所有的方法
1. 创建web项目
2. 创建类实现servlet接口，重写所有的方法


## Servlet的实现类

### Servlet继承结构

### GenericServlet类 

### HttpServlet类

## Servlet的访问地址

### Servlet映射多个路径

### <url-pattern>的访问方式

### load-on-startup

## 使用注解创建Servlet

## request接受请求参数

### 得到参数的方法

### 接受请求参数案例

## 案例：Servlet技术完成登录功能

### 需求分析：使用三层结构

### 项目结构

### 创建数据库表和数据

### 登录界面

### 添加包到WebRoot/WEB-INF/lib目录

### Servlet写出登录功能

## Web开发中的路径问题

### 相对路径的个编写规范

### 什么是相对路径

### 什么是绝对路径

## ServletConfig的使用

### 作用

### 常用的方法

### Enumeration中的方法

### 硬编码的缺点

### 案例演示

### 代码
