# sublime text 3 使用方式
<!-- MarkdownTOC style="ordered" -->

1. [常用快捷键](#常用快捷键)
1. [使用模板](#使用模板)
1. [如何开启vi模式](#如何开启vi模式)
1. [如何配置Markdown的文档编写环境](#如何配置markdown的文档编写环境)

<!-- /MarkdownTOC -->


<a id="常用快捷键"></a>
## <p id="2">常用快捷键</p>
- CTRL + 数字1~6表示 标题大小,1代表一级标题
ctrl + shift + d : 向下快速复制一行
ctrl + shift + k : 快速删除整行
ctrl + shift + ↑ : 整行向上移动
ctrl + shift + ↓ : 整行向下移动
#### 如何使用markdown 在sublime text 3 上编辑
1. 首先install package control
2. ctrl + shift +p 进入package control
3. 安装中文插件 直接搜索Chinese 就可以出来
4. 安装markdownEditing 和 MarkDownPreview
5. 设置MarkDownPreview 快捷键 ctrl + m   
    { "keys": ["alt+m"], "command": "markdown_preview", "args": {"target": "browser", "parser":"markdown"} }
6. 设置行数显示 
    - 在 preferance --> package settings --> MarkDown Editing --> 选择GFM 用户设置，在上面加上："line_numbers": true  
完成，基本的编辑就可以了


<a id="使用模板"></a>
## 使用模板
1. 工具--→插件开发--→新建代码段--→会出来一个文件如下
```snippet
<snippet>  
    <content><![CDATA[ 
Hello, ${1:this} is a ${2:snippet}. 
]]></content>  
    <!-- Optional: Set a tabTrigger to define how to trigger the snippet -->  
    <!-- <tabTrigger>hello</tabTrigger> -->  
    <!-- Optional: Set a scope to limit where the snippet will trigger -->  
    <!-- <scope>source.python</scope> -->  
</snippet>
```
2. 这就是新建的代码段了，将要修改的内容放入到 **CDATA[ 内容 ]**里面
3. 把`<!-- <tabTrigger>hello</tabTrigger> -->`这段代码的注释解开，代表用table键触发
4. hello代表需要触发的单词，可以自己修改
5. `<!-- <scope>source.python</scope> --> ` 这段代码代表了在那些地方使用
- .python 代表在python中使用。如果是在.css文件中使用就把python改为css就行了
经过测试测试成功

6. `Hello, ${1:this} is a ${2:snippet}.`这段代码的含义如下
  - `${1:this}` :代表光标在这个地方 在代码上放`${1}`就行，如果需要通时编辑几个光标就弄重复的相同的`${1}`，如果想光标快速跳转到下一光标可以放`${2},${3}`然后按table键可以把光标从1移到2上面去，按esc解除光标快速移动

<a id="如何开启vi模式"></a>
## 如何开启vi模式

1. 在setting里面把package ignore 里面的vintage给去掉
2. 然后在下面加上`"vintage_start_in_command_mode": true,`这样就可以了，因为是 json 格式，所以只要语法不错就可以了，这是设置的一打开sublime text 3 就进入command模式，也就是命令模式。  

<a id="如何配置markdown的文档编写环境"></a>
## 如何配置Markdown的文档编写环境  

主要是几个插件的下载和基本的配置 **插件的配置最好是把所有的默认配置复制过去再修改，不然有些插件直接不会生效**   

1. 通过package control 下载 `Markdown Editing`，和`Markdown Preview`，这样就可以预览和编写 markdown 文档了。`Markdown TOC`是一个可选的插件
2. `Markdown Editing`的配置 
3. `Markdown Preview`的使用 `ctrl +shift + p` 搜索`markdown preview` 然后就有选项出来了。GFM 格式需要自己设置  
4. 解决中文乱码的问题，设置这一项 `"uri_encoding": false,`
下面是经过测试可以在GitHub上面正确使用的配置，直接 copy 后然后放到自己的 MarkdownTOC 的 user 设置中就可以了。 要全部copy  
```json
{
  "defaults": {
    "autoanchor": true,  // 这是生成的自动的html标签，移除TOC的时候选false
    "autolink": true,// 这是生成自动链接的。
    "bracket": "round", // 这是代表链接后面的括号是（ 如果改成[ 则写square
    "levels": [1,2,3],// 这是目录的深度，最多是6层
    "indent": "\t",  // 每级目录前面多一个制表符
    "remove_image": true,  // 如果标题有图片的话移除图片
    "link_prefix": "",  // 这是链接前缀
    "bullets": ["-"],  // 这是代表每集目录所使用的连接符号。
    "lowercase": "only_ascii", // 这是关于是否转换为小写的设置。
    "style": "unordered",  // 这是代表生成的目录是否是有序的。 有序填 ordered
    // 这是解决中文乱码的问题的。
    "uri_encoding": false,
    // 使用markdown preview插件时使用的规则，可以不选，在 markdown preview 中设置
    "markdown_preview": ""  
  },
  "id_replacements": [
    {
      "pattern": "[_*]{2}([^\\s])[_*]{2}",
      "replacement": "\\1"
    },
    {
      "pattern": "[_*]([^\\s])[_*]",
      "replacement": "\\1"
    },
    {
      "pattern": "\\s+",
      "replacement": "-"
    },
    {
      "pattern": "&lt;|&gt;|&amp;|&apos;|&quot;|&#60;|&#62;|&#38;|&#39;|&#34;|!|#|$|&|'|\\(|\\)|\\*|\\+|,|/|:|;|=|\\?|@|\\[|\\]|`|\"|\\.|\\\\|<|>|{|}|™|®|©",
      "replacement": ""
    }
  ],
  "logging": false
}


```
更多的 markdown-TOC 设置参考 [markdownTOC document](https://github.com/naokazuterada/MarkdownTOC) 。  
 
