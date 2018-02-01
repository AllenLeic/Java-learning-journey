# HTML基础

## 1. 软件的结构

1. C/S：Client/Server  客户端/服务端
   - 特点：开发时需要开发两个端，一个端称为客户端，一个端称为服务端。客户端是用户使用，服务端是运行在服务器的程序。
   - 常见的软件：QQ，微信，迅雷，快播。
   - 优点：可以将一些运行放在客户端执行，减轻服务端的压力。
   - 缺点：开发成本高，周期厂，针对不同系统开发不同的客户端。每次升级版本都需要重新下载安装。
2. B/S：Browser/Server 浏览器/服务端
   - 特点：开发时只需要开发一端即可，就是服务端。只要有浏览器就可以使用该程序。
   - 常见的软件：12306，淘宝，京东
   - 优点：因为只需要开发一端，开发成本低，开发周期短。升级不需要安装任何软件。
   - 缺点：所有的运行都要在服务器端进行，加大服务器的压力。

## 2.HTML概述

### 2.1 什么是HTML

1. HTML的英文全称：Hypertext Markup Langeuage   中文名：超文本标记语言。
   - 超文本：文本中可以包含图片，视频，音频等数据
   - 标记：是使用标记或标签来描述数据结构，比如:<p>aaa</p>.标签由有w3c组织制定的。

### 2.2 HTML的作用

1. 用来制作网站。网站是由网页组成，HTML就是负责搭建网页的结构。它是网页开发的最基础的语言。



## 3. 第一个HTML页面

1. 在任意位置(F 盘根目录)，创建“文本文档”，重命名“01-第一个网页.html”  

2. 右键/打开方式/记事本，开发 html 文件，并编写如下内容：

3. 
```html
   <html>
   	<head></head>
   	<body>
   		第1个html程序。
   	</body>
   </html>
```

4. 使用浏览器打开：01-第一个网页.html

![](image/image10.png)

## 4. 开发工具的使用

1. 使用用“记事本”开发效率低，现阶段比较流程的前端IDE(集成开发环境)是 HBuilder，为了统
   一环境，要求所有同学的都安装 HBuilder。
2. 安装参考文档：**day01--01.HBuilder安装.pdf** 
3. 使用HBuilder开发第一个网页：**01-第一个网页.html**

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<title></title>
	</head>
	<body>
		第一个HTML页面
	</body>
</html>
```

## 5. HTML的语法

### 5.1 标记概述

**标记也称为标签。**

1. **格式**

   - <开始标签名>标签体</结束标签名>
   - 比如：<div>你好</div>
2. **特点**
   - 标签名不区分的大小写。
   - 标签名是固定的，是W3C制定的。
3. **分类**
   - 有主体标签：有标签体的标签。比如：<div>你好</div>
   - 无主体标签：没有标签体的标签。比如：<br />
4. **属性**
   - 标签中可以有属性，属性的格式：**属性名=“属性值”;**
   - 属性值必须使用引号括起来，可以是单引号或双引号。
   - 一个标签中可以有多个属性，多个属性之间使用空格分割。
   - 属性必须写在开始标签中，不能写在结束标签。

### 5.2 HTML注释

1. **格式**

   ```html
   <!-- 注释内容 -->   
   注释标签，注释是给开发人员查看的，浏览器在解析网页内容时会忽略的注释内容。
   ```

2. **注意事项**

   - 注释不能嵌套注释。

### 5.3 文件头标签：head

1. **概述**

   - 在 **<head>** 标签中的内容一般不会显示在浏览器中。

   - **<head> **标签用于引入脚本、导入样式、提供元信息等。

2. **常用子标签**

```html
<meta>：定义文件信息,对网页进行说明，便于搜索引擎查找。	
	比如设置关键字：
	<meta name = "keywords" content="Java培训,Android培训,安卓培训,PHP培训,C++培训,网页设计培训,平面设计培训,UI设计培训,移动开发培训,网络营销培训,web前端培训,云计算大数据培训,全栈工程师培训,产品经理培训"/>
	指定网页的内容和字符集：
	<meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
<title>：设置网页显示的标题。
<srcipt>：用来导入js文件。相当于java的导包操作。
<style>：用来引入样式文件:css文件。相当于java的导包操作。
```

3. 示例代码

```html
<!DOCTYPE html>
<html>
	<head>
		<!-- 元数据 -->
		<!--<meta charset="GBK">-->
		<!-- 关键字越多：权重低，排序越靠后 -->
      	<!-- 定义文件信息,对网页进行说明，便于搜索引擎查找 -->
		<meta name = "keywords"
			content="Java培训,Android培训,安卓培训,PHP培训,
			C++培训,网页设计培训,平面设计培训,
			UI设计培训,移动开发培训,网络营销培训,
			web前端培训,云计算大数据培训,
			全栈工程师培训,产品经理培训"/>
		<!-- 指定网页的内容和字符集 -->
		<meta http-equiv="Content-Type" content="text/html; charset=gbk" />
		<!-- 设置网页标题 -->
		<title>百度一下</title>
		
	</head> 
	<!-- 这是一个牛逼的网页 -->
	<body>
		第一个HTML页面
	</body>
</html>
```

### 5.4 文件体：body

- 用来定义网页的主体内容，比如列表，表格，图片，文本，视频等数据。

## 6. 文本标签

### 6.1 标题标签

- 概述：<h1> - <h6> 标签可定义标题。<h1> 定义最大的标题。<h6> 定义最小的标题。

- 格式

  ```html
  <hn>标题</hn>   n取值是1-6
  ```


- 示例代码

```html
<h1>黑马程序员</h1>
<h2>黑马程序员</h2>
<h3>黑马程序员</h3>
<h4>黑马程序员</h4>
<h5>黑马程序员</h5>
<h6>黑马程序员</h6>
```

### 6.2 换行标签

- 格式

  ```Html
  <br />  
  换行标签，没有任何属性，没有主体。
  ```


- 示例代码

```html
<!-- 换行标签 -->
黑马程序员 <br />
传智播客
```

### 6.3 水平线标签

- 格式：<hr />

- 作用：在网页中添加一条水平分割线。

- 常用属性

  ```html
  size：设置水平线的高度
  noshade：设置水平线为实心。
  color：设置水平线颜色
  ```


- 颜色使用说明

  ```html
  - 颜色取值：颜色名称或#xxxxxx
  - #xxxxxx 使用红绿蓝三原色组合。
  	每一个原色由8位二进制数组成，取值：0到255
  	三原色由24位二进制数组成：取值：2的24次方
  	RGBA: 32位，大约能表示43亿中颜色。
  	ARGB: 32位，大约能表示43亿中颜色。
  #469031：十六进制格式。
  ```

### 6.4 字体标签

- 格式：<font>文本内容</font>

- 常用属性

  ```html
  color：设置颜色
  size：设置字体大小
  face：设置字体类型：比如微软雅黑。
  ```

### 6.5 字体样式标签：粗体和斜体

- 粗体格式：<b>文本内容</b>
- 斜体格式：<i>文本内容</i>

### 6.6 段落标签

- 格式：<p>内容</p>
- 作用：对文本进行分段，会在前后自动添加换行。
- 示例代码

```html
<h3>没有使用段落标签</h3>
黑马程序员<br/>
黑马程序员<br/>
黑马程序员<br/>

<h3>使用段落标签</h3>
<!-- 段落标签：<p> -->
<p>黑马程序员黑马程序员黑马程序员黑马程序员黑马程
	序员黑马程序员黑马程序员黑马程序员黑马程序员黑马程序员黑马程序员黑马程序员黑马程序员</p>
<p>黑马黑马程序员黑马程序员黑马程序员黑马程序员黑马程
	序员黑马程序员程序员黑马程序员程序员</p>
<p>黑马程序员</p>
<p>黑马程序员</p>
<p>黑马程序员</p>
```

## 7. 文本标签案例

### 7.1 案例效果图如下

![](image/image01.jpg)

### 7.2 知识点分析

  	分析一下“公司介绍”基本信息不同的地方都使用了那些标签。 

a) **“公司介绍”**，需要使用标题标签完成 <hn>例如：**<h3>**  

b) “**中关村黑马程序员训练营**” 需要使用字体标签完成 **<font>** 

c) **“传智播客”** 需要斜体<i> 和粗体<b> 组合完成  

d)  这个文档被划分成 4 个区域，每一个区域之间有定义的间隔，需要使用段落标签<p>完成  

e)  第 2 行或第 3 行是一个普通的换行，在 html 标签中，需要使用<br/>完成  

f)  案例文本内容如下：

```java
公司简介
"中关村黑马程序员训练营"是由传智播客 
联合中关村软件园、CSDN，并委托传智播客进行教学实施的软件开发高端培训机构，致力于服务各大软件企业，解 决当前软件开发技术飞速发展，而企业招不到优秀人才的困扰。
目前，“中关村黑马程序员训练营”已成长为行业“学员质量好、课程内容深、企业满意” 动开发高端训练基地，并被评为中关村软件园重点扶持人才企业。 
黑马程序员的学员多为大学毕业后，有理想、有梦想，想从事 IT 行业，而没有环境和机遇改 变自己命运的年轻人。黑马程序员的学员筛选制度，远比现在 90%以上的企业招聘流程更为严格。任何一名学员想 成功入学“黑马程序员”，必须经历长达 2 个月的面试流程，这些流程中不仅包括严格的技术测试、自学能力测试， 还包括性格测试、压力测试、品德测试等等测试。毫不夸张地说，黑马程序员训练营所有学员都是精挑细选出来的。 百里挑一的残酷筛选制度确保学员质量，并降低企业的用人风险。 
中关村黑马程序员训练营不仅着重培养学员的基础理论知识，更注重培养项目实施管理能力， 并密切关注技术革新，不断引入先进的技术，研发更新技术课程，确保学员进入企业后不仅能独立从事开发工作， 更能给企业带来新的技术体系和理念。 
一直以来，黑马程序员以技术视角关注 IT 产业发展，以深度分享推进产业技术成长，致力于 弘扬技术创新，倡导分享、 开放和协作，努力打造高质量的 IT 人才服务平台。 
```

### 7.3 代码实现

```html
<h1>公司简介</h1>
<hr />
<p>
<font color="red">"中关村黑马程序员训练营"</font>是由<b><i>传智播客</i></b> 联合中关村软件园、CSDN，并委托传智播客进行教学实施的软件开发高端培训机构，致力于服务各大软件企业，解 决当前软件开发技术飞速发展，而企业招不到优秀人才的困扰。<br/> 目前，“中关村黑马程序员训练营”已成长为行业“学员质量好、课程内容深、企业满意” 动开发高端训练基地，并被评为中关村软件园重点扶持人才企业。 </p>
<p>黑马程序员的学员多为大学毕业后，有理想、有梦想，想从事 IT 行业，而没有环境和机遇改 变自己命运的年轻人。黑马程序员的学员筛选制度，远比现在 90%以上的企业招聘流程更为严格。 任何一名学员想 成功入学“黑马程序员”，必须经历长达 2 个月的面试流程，这些流程中不仅包括严格的技术测试、自学能力测试， 还包括性格测试、压力测试、品德测试等等测试。毫不夸张地说，黑马程序员训练营所有学员都是精挑细选出来的。 百里挑一的残酷筛选制度确保学员质量，并降低企业的用人风险。</p>
<p>中关村黑马程序员训练营不仅着重培养学员的基础理论知识，更注重培养项目实施管理能力， 并密切关注技术革新，不断引入先进的技术，研发更新技术课程，确保学员进入企业后不仅能独立从事开发工作， 更能给企业带来新的技术体系和理念。 </p>
<p>一直以来，黑马程序员以技术视角关注 IT 产业发展，以深度分享推进产业技术成长，致力于 弘扬技术创新，倡导分享、 开放和协作，努力打造高质量的 IT 人才服务平台。 </p>
```

## 8. 图片标签

### 8.1 概述

​	在上面的案例中，我们发现这个页面都是文字的内容，而我们看到的页面往往文字和图片是并存的，或者很多地方都是图片的效果，那么我们如何在页面中显示图片呢?  要在网页中展示图片要学习图片标签。

### 8.2 图片标签

1. **格式**：<img />
2. **作用**：用来在网页中插入图片，图片可以来源本地，也可以是互联网上图片。

3. **常用属性**
   - **src**：指定图片的路径。本地路径或互联网路径。
   - **alt**：当图片找不到时，显示的提示文字。
   - **width**：设置图片的宽度，单位像素
   - **height**：设置图片的高度，单位像素
   - **title**：设置当鼠标悬停在图片上时显示的标题文字。

### 8.3 示例代码

```html
<!-- 
	src：指定图片的路径。本地路径或互联网路径。
	alt：当图片找不到时，显示的提示文字。
	height：设置图片的高度，单位像素。
	width:设置图片的宽度，单位像素。
	title：设置当鼠标悬停在图片上时显示的标题文字。
-->
<img src="img/2.jpg" alt="你的网络不给力" height="250px" width="250px"
	title="足球宝宝"/>
```

## 9. 图片标签案例

### 9.1 **案例效果图**

![](image/image02.jpg)

### 9.2 知识点分析

![](image/image03.jpg)

### 9.3 示例代码

```html
<body>
	<!-- logo -->
	<img src="img/logo2.png" /> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
	<img src="img/header.jpg" />
	
	Copyright &copy;2005-2016 传智商城 版权所有
	
</body>
```

## 10. 特殊字符

### 10.1 概述

- **特殊字符也称字符实体**。一些字符在HTML 中拥有特殊的含义，比如小于号 (<) 用于定义HTML 标签的开始。如果我们希望浏览器正确地显示这些字符，我们必须在 HTML 源码中插入字符实体。

### 10.2 最常用的字符实体

![](image/image04.png)

## 11. 列表和超链接标签

### 11.1  列表标签

1. **有序列表**
   - 格式：<ol></ol>  
   - 属性：type：列表的类型，可取值：A、a、I、i、1等
2. **无序列表**
   - 格式：<ul></ul>
   - 属性：type：符号的类型，取值：disc 实心圆、square方块、circle
     空心圆。
3. **列表项**

   - 格式：<li>列表项</li>
   - 作用：是有序列表和无序列表的子标签。
4. **示例代码**

```html
<!--有序列表 
	<ol> 标签常用属性
		type：设置列表项类型，常用取值：a,A,i  默认是数字
-->
<ol>
	<li>Iphone</li>
	<li>Mac Book</li>
	<li>ViVO</li>
</ol>
<br />
<ol type="i">
	<li>Iphone</li>
	<li>Mac Book</li>
	<li>ViVO</li>
</ol>

<!-- 无序列表 
	常用属性：
		type属性：
			取值：circle 空心圆  square 方块   disc 实心圆  默认值
-->
<ul>
	<li>Iphone</li>
	<li>Mac Book</li>
	<li>ViVO</li>
</ul>

<ul type="circle">
	<li>Iphone</li>
	<li>Mac Book</li>
	<li>ViVO</li>
</ul>

<ul type="square">
	<li>Iphone</li>
	<li>Mac Book</li>
	<li>ViVO</li>
</ul>

<ul type="disc">
	<li>Iphone</li>
	<li>Mac Book</li>
	<li>ViVO</li>
</ul>
```



### 11.2 超链接标签

1. **格式：**<a>内容</a>
2. **作用：**提供了一种从当前页面跳转到其他页面或当前页面其他位置的方式。
3. **属性：**

   - href：用来确定要跳转页面的地址。
   - target: 用来控制界面在哪里打开，常用值有：
     - **_blank：** 在一个新的空白页面打开。
     - **_self**：在当前界面打开新界面，新界面替换当前界面。
4. **示例代码**

```Html
<!-- 跳到其他界面 -->
<a href="01-第一个HTML页面.html" target="_self">跳转到01-第一个HTML页面</a><br/>
<a href="http://www.baidu.com">百度一下</a><br/>


<!-- 跳转到当前页面的其他位置 -->
<a href="#frist">第一章</a><br/>
<a href="#second">第二章</a><br/>
<a href="#third">第三章</a><br/>

<p id="frist">第一章内容第容第一章内容第一章内容第一章内容第一章内容第一章内容第一章内容第一章内容</p>
<p id="second">二二二二章内容第一章内容第一章内容第一章章内容第一章内容第一章内容第一章内第一章内容</p>
<p id="third">二二二二章内容第一章内容第一章内容第一章章内容第一章内容第一章内容第一章内第一章内容</p>

<!-- 图片超链接 -->
<a href="01-第一个HTML页面.html">
	<img src="img/2.jpg"/>
</a>
```



## 12. 列表和超链接案例

### 12.1 案例效果图如下

![](image/image05.png)

### 12.2 知识点分析

![](image/image06.jpg)

### 12.3 示例代码

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<title></title>
	</head>
	<body>
		<ul type="square">
			<li><a href="http://www.itcast.cn">传智播客</a></li>
			<li><a href="http://www.itcast.cn">百度一下</a></li>
			<li><a href="http://www.itcast.cn">网易</a></li>
			<li><a href="http://www.itcast.cn">腾讯</a></li>
		</ul>
	</body>
</html>
```



## 13. 表格标签

### 13.1 概述

 网页上除了常见文字，图片，超链接等元素外，还有一个元素也是我们在经常看到，那就是表格。如下图显示的表格：

![](image/image07.png)

### 13.2 与表格相关的标签

1. **<table>**：表格标签，是父标签，相当于整个表格的容器。

   - 常用属性

   ​               border：表格边框的宽度，默认是0，表示无边框。单位：像素

   ​		width：表格的宽度，可以指定像素，百分比

   ​		height：表格的高度，可以指定像素，百分比

   ​		align：表格的对齐方式，取值：**left(默认值)，center，right。**

   ​               cellspacing：单元格之间的间距

2. **<tr>**：行标签，一个<tr>标签对应表格的一行。

   - 常用属性
     - align：设置行内容的对齐方式，常用取值：left，左对齐，center 居中 right 右对齐。
     - bgColor：设置行的背景颜色。

3. **<td>**：列标签，一个<td>标签对应表格的一列。

   - 常用属性
     - rowspan：设置当前单元格跨的行数。
     - colspan：设置当前单元格跨的列数。
     - align：设置行内容的对齐方式，常用取值：left，左对齐，center 居中 right 右对齐。

4. **<th>**：表头标签，使用方式<td>一样，区别：<th>单元格内的内容默认**居中、加粗。**

5. **<caption>**：标题标签，用来给表格设置标题。

### 13.3 示例代码

```html
<!-- 表格
	table标签常用属性：
		border：设置边框粗细，单位是像素，默认值:0
		width：设置表格宽度，单位是px，也可以是百分比，比如：50%
		height：设置表格高度
		cellspacing：设置单元格与单元格之间的间距。
		align：设置表格的对齐方式。left，左对齐，center 居中 right 右对齐。
		
	tr标签常用属性
		align：设置行内容的对齐方式，
			常用取值：left，左对齐，center 居中 right 右对齐。
		bgColor：设置行的背景颜色。
	
	td标签常用属性：
		rowspan：设置当前单元格跨的行数。
		colspan：设置当前单元格跨的列数。
		align：设置行内容的对齐方式，
			常用取值：left，左对齐，center 居中 right 右对齐。
		
	th标签：用来设置表头的单元格。和td是一样使用，区别在于内容默认居中加粗。
-->
<table border="2px" width="40%" height="200px" cellspacing="0" align="center">
	<!-- 表格标题 -->
	<caption>学生成绩表</caption>
	<tr  align="center" bgcolor="lightgrey">
		<th>学号</th>
		<th>姓名</th>
		<th>性别</th>
		<th>成绩</th>
	</tr>			
	<tr  align="center">
		<td>1</td>
		<td>潘金莲</td>
		<td>女</td>
		<td>90</td>
	</tr>			
	<tr  align="center">
		<td>2</td>
		<td>武松</td>
		<td>男</td>
		<td rowspan="2">78</td>
	</tr>			
	<tr  align="center">
		<td>3</td>
		<td>西门庆</td>
		<td>男</td>
	</tr>			
	<tr  align="center">
		<td>总成绩</td>
		<td colspan="3">
			167
		</td>
	</tr>			
</table>
```

## 14. 表格标签案例

- **详情参看预习资料文档pdf中的第16项。**

```html
<table width="95%" align="center">
	<tr>
		<td>
			<img src="img/logo2.png"/>
		</td>
		<td align="center">
			<img src="img/header.jpg" />
		</td>
		<td align="center">
			<a href="#">登录</a> &nbsp;&nbsp;
			<a href="#">注册</a>&nbsp;&nbsp;
			<a href="#">购物车</a>&nbsp;&nbsp;
		</td>
	</tr>
	<tr bgcolor="black" height="60px">
		<td colspan="3">
			&nbsp;&nbsp;&nbsp;&nbsp;
			<a href="#"><font color="gray">首页</font></a> &nbsp;&nbsp;
			<a href="#"><font color="gray">手机数码</font></a> &nbsp;&nbsp;
			<a href="#"><font color="gray">移动办公</font></a> &nbsp;&nbsp;
		</td>
	</tr>
	<tr>
		<td colspan="3">
			<br />
			<img src="img/1.jpg" width="100%"/>
		</td>
	</tr>
	<tr>
		<!-- 热门商品 -->
		<td colspan="3">
			<font size ="5">热门商品</font>
			<img src="img/title2.jpg" />
		</td>
	</tr>
</table>
<table width="95%" align="center">
	<tr>
		<td rowspan="2">
			<img src="img/big01.jpg" />
		</td>
		<td colspan="3" align="center">
			<img src="img/middle01.jpg" />
		</td>
		<td align="center">
			<img src="img/small03.jpg" /><br>
			冬瓜<br/>
			<font size="4" color="red">¥299</font>
		</td>
		<td align="center">
			<img src="img/small03.jpg" /><br>
			冬瓜<br/>
			<font size="4" color="red">¥299</font>
		</td>
	</tr>	
	
	<tr>
		<td align="center">
			<img src="img/small03.jpg" /><br>
			冬瓜<br/>
			<font size="4" color="red">¥299</font>
		</td>
		<td align="center">
			<img src="img/small03.jpg" /><br>
			冬瓜<br/>
			<font size="4" color="red">¥299</font>
		</td>
		<td align="center">
			<img src="img/small03.jpg" /><br>
			冬瓜<br/>
			<font size="4" color="red">¥299</font>
		</td>
		<td align="center">
			<img src="img/small03.jpg" /><br>
			冬瓜<br/>
			<font size="4" color="red">¥299</font>
		</td>
		<td align="center">
			<img src="img/small03.jpg" /><br>
			冬瓜<br/>
			<font size="4" color="red">¥299</font>
		</td>
	</tr>	
	
	<tr>
		<td colspan="6">
			<img src="img/ad.jpg" width="100%"/>
		</td>
	</tr>
	<tr align="center">
		<td colspan="6">
			<a href="#">关于我们</a> &nbsp;
			<a href="#">关于我们</a> &nbsp;
			<a href="#">关于我们</a> &nbsp;
			<a href="#">关于我们</a> &nbsp;
			<a href="#">关于我们</a> &nbsp;
			<a href="#">关于我们</a> &nbsp;
			<a href="#">关于我们</a> &nbsp;
			<a href="#">关于我们</a> &nbsp;
			<a href="#">关于我们</a> &nbsp;
		</td>
	</tr>
</table>
```



## 15. 框架集标签

### 15.1 概述

​	平时我们看到的电商网站，其实只是其前台页面，提供给普通用户进行查询商品，购买商品等操作的。实际上，还有后台页面，提供给管理员使用的，用于添加商品，发货等操作。 一般情况，后台页面都采用的框架方式进行呈现。效果如下图:

![](image/image08.jpg)

### 15.2 框架集标签：<frameset>

1. **作用**
   - <frameset> 标签可以将多个页面整合在一起，通过列和行来确定整体布局，每一个页面(框架)都是单独文档，每一个页面的位置需要使用子标签<frame>来确定。
2. **常用属性**
   - **cols**：确定列数，格式：值1,值2…值n。值的个数代表列数。
   - **rows：**确定行数，格式：值1,值2…值n。值的个数代表行数。
     - **值的说明：**多个值之间使用逗号分隔，值可以是10px、10%等。最后一个值如果不想计算可以使用*匹配剩余量。
3. **注意事项**
   - frameset标签不能和body标签一起使用。
   - cols和rows属性必须要有一个。

### 15.3 框架集子标签：<frame>

1. **作用：**用于设置<frameset>框架集中的一个页面(框架)。 
2. **常用属性**
   - **src：**确定页面的路径
   - **noresize：**规定用户无法通过手动拖拽调整框架的大小。
   - **scrolling：**规定是否在框架中显示滚动条
   - **name: **定义框架的名称，常作为链接的目标

### 15.4 框架集标签案例

1. **案例效果图如下**

![](image/image09.png)

2. **示例代码**

```html
<frameset rows="100px,*">
	<!-- 头部页面-->
	<frame src="top.html" scrolling="no"/>
	<frameset cols="150px,*">
		<frame src="left.html" noresize/>
		<frame src="center.html" name="center" scrolling="auto"/>
	</frameset>
</frameset>
```



## 16. 表单标签：<form>

### 16.1 form概述

1. **作用**：用来搜集用户输入的信息，并将数据发送给服务器。
2. **格式**：<form>表单元素</form>

### 16.2 表单元素标签

#### 16.2.1 input标签

1. **作用：**用来接收用户输入的数据。
2. **常用属性**
   - type：输入框类型，常用取值有以下几个：
     - text：普通文本输入框，明文显示。
     - password：密码输入框，暗文显示。
     - radio：单选框，要设置name属性，同一组的name属性值要一致。checked属性设置该项目选中。
     - checkbox：复选框。
     - file：文件域，用来选中要上传的文件。
     - reset：重置按钮，可以将表单元素的内容恢复到默认值。
     - submit：提交按钮，可以触发form进行提交
     - image：图片按钮，与submit具有相同的功能，可以提交数据给服务器端。
     - button：按钮
     - hidden：隐藏域，用于记录不需要显示给用户看，但需要提交给服务器的数据。
   - name：定义表单元素的名称。
   - value：设置表单元素的值。

#### 16.2.2 select标签

1. **概述：**下拉框，让用户选择内容。

2. **常用属性**

   - size：设置显示项目的个数。默认是1

3. **子标签：<option>**

   - 用法：<option>东莞</option>

   - 属性：

     l  selected：选中当前项

     l  value：该项对应的值，该值会被提交到服务器。

#### 16.2.3 textarea标签

1. **概述**：文本域标签，当需要输入多行内容时，就需要该标签。

2. **常用属性**

   - name：指定文本域的名称


   - rows：指定文本域大小，指定行数
   - cols：指定文本域大小，指定列数

### 16.3 form常用属性

- **action**：指定数据提交到目标服务器地址

- **method**：用于设置数据提交的方式，常用方式有：**get和post**  默认值**GET**

  ```
  get和post的区别
  get方式提交，所有数据都是拼接到url后面。
  post方式提交，数据不会拼接到url后面，数据封装的请求体中发送给服务器。

  get请求传输数据大小限制在2KB左右。
  post请求传输数据没有大小限制。

  get请求不安全，数据暴露在url后面，
  post提交相对安全
  如果涉及到隐私数据时一定不能使用get请求，文件上传一定是POST请求。
  ```

### 16.4 注意事项

1. 如果表单元素的数据需要提交，那么每个表单元素都必须要有name的属性值。 
2. 如果表单元素可以输入内容，那么可以没有value属性值
3. 如果表单元素不能输入内容，那么必须添加value属性值

### 16.5 示例代码

```html
<!-- 表单标签 -->
<form>
	用户名：<input type="text" value="jack"/> <br/>
	密  码：<input type="password" /> <br/>
	性  别：
		<input type="radio" name="gender" checked/> 男
		<input type="radio" name="gender"/> 女
		<input type="radio" name="gender"/> 人妖 <br/>
	爱  好：
		<input type="checkbox" checked="checked"/> 学编程
		<input type="checkbox" /> 戳麻将
		<input type="checkbox" /> 篮球
		<input type="checkbox" /> 唱歌 <br/>
	头 像：<input type="file"  /> <br/>
	城 市：
		<select size="1">
			<option>广州</option>
			<option>北京</option>
			<option selected>上海</option>
			<option>深圳</option>
		</select><br/>
	自我介绍：
		<textarea rows="15" cols="25">
		</textarea> <br/>
		
	<input type="reset" />
	<input type="button" value="提交"/><br />
	<input type="submit" /> <!-- 自动触发数据的收集和提交-->
	<input type="image" src="img/submit.png"/> <br/> <!-- 自动触发数据的收集和提交-->
</form>
```



## 17. 块级标签：<div>

**17.1 作用**：用来划分区域，一般是作为其他标签的容器使用。

**17.2 特点**

- 独自占一行
- 独自不能实现复杂效果，必须结合 CSS 样式渲染

**17.3 示例代码**

```html
<!-- 块级标签 -->
<div id = "first">传智播客</div>
<div id = "second">传智播客</div>
<div id = "third">传智播客</div>
```

## 18. 行内标签：<span>

**18.1 作用**

- 用来组合文档中的行内元素，没有换行的作用。
- 如果没有应用css样式，那么span元素的文本与其他文本不会有任何视觉上的差异。

**18.2 示例代码**

```html
<!-- span标签：行内标签 -->
我爱<span style="color: yellow;">黑马程序员</span>和传智播客
```

19. ## 小结

- <html> 根标签
- <head> 头部标签
  - <title> 设置网页标题
  - <meta> 设置搜索关键字以及字符编码
- <body>  主体标签
- <b> 加粗
- <i> 斜体
- <font>  字体标签
- <br /> 换行
- <hr />  水平分割线标签
- <p>  段落标签
- <hn> n从1到6  标题标签
- <img>  图片标签
- <ol>  有序列表
- <ul> 无序列表
- <li> 列表项
- <a> 超链接标签
- <table>  表格标签
- <tr>  行标签
- <td> 列标签
- <th>  表头标签
- <caption> 表的标题标签
- <div>  块级标签
- <span>  行内标签
- <frameset>
- <form>